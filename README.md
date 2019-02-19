# Overview

Use this interface to expose public API endpoint of Designate service.

# Usage

## metadata

To consume this interface in your charm or layer, add the following to `layer.yaml`:

```yaml
includes: ['interface:designate']
```

and the following to `metadata.yaml`:

```yaml
requires:
  external-dns:
    interface: designate
```

## handler example

```python
@reactive.when('external-dns.available')
def expose_endpoint(endpoint):
    with provide_charm_instance() as instance:
        endpoint.expose_endpoint(instance.public_url)
```

## deployment example

```python
$ juju deploy designate
$ juju deploy neutron-api
$ juju add-relation designate:external-dns neutron-api:external-dns
```

# Bugs

Please report bugs on [Launchpad](https://bugs.launchpad.net/openstack-charms/+filebug).

For development questions please refer to the OpenStack [Charm Guide](https://github.com/openstack/charm-guide).
