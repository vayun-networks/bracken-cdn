# BRACKEN CDN

**Edge caching and content delivery services for BRACKEN.**

BRACKEN CDN is intended to provide reverse-proxy and edge-caching capabilities that can serve content closer to clients while coordinating with origin services. The initial goal is a measurable, limited deployment model with clear cache behavior, origin configuration, and operational visibility.

> **Project status:** Early-stage project. No global network, performance target, protocol matrix, or production availability claim is established.

## Responsibilities

- Proxy HTTP and HTTPS requests between clients, edge nodes, and configured origins.
- Apply explicit cache policies and expose cache status.
- Support cache invalidation and origin health behavior.
- Manage TLS configuration through documented, secure interfaces.
- Report request, response, cache, and error metrics.
- Coordinate edge configuration through the BRACKEN control plane.

## Scope boundaries

The CDN repository owns HTTP delivery and caching behavior. DNS-based traffic steering belongs in [bracken-dns](https://github.com/vayun-networks/bracken-dns). Packet forwarding and network policy belong in the [data plane](https://github.com/vayun-networks/bracken-data-plane) and [network engine](https://github.com/vayun-networks/bracken-network-engine). Origin applications remain outside this repository.

## Design principles

- Make cache keys, TTLs, bypass rules, and invalidation semantics explicit.
- Preserve correct handling of private, authenticated, and non-cacheable responses.
- Make origin failures and stale-content behavior configurable and observable.
- Treat TLS keys and origin credentials as secrets; never store them in source control.
- Measure cache hit ratio, response latency, throughput, and resource use under documented conditions.

## Planned milestones

Start with a single-node reverse proxy and a test origin, then add safe cache policies, invalidation, health checks, and configuration management. Multi-edge coordination, HTTP/3, and distributed cache hierarchies are future work that requires design and validation.

## Development

No build or deployment commands are defined yet. Future instructions should explain local origin setup, cache inspection, invalidation testing, and performance test methodology. Use only systems you own or are authorized to test.

## Related components

- [bracken-control-plane](https://github.com/vayun-networks/bracken-control-plane)
- [bracken-dns](https://github.com/vayun-networks/bracken-dns)
- [bracken-observability](https://github.com/vayun-networks/bracken-observability)
- [bracken-deploy](https://github.com/vayun-networks/bracken-deploy)