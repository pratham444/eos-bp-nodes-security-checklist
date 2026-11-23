# eos-bp-nodes-security-checklist

EOS block producers need to keep production traffic reachable without exposing production hosts or administrative APIs. This EOS BP security checklist covers node isolation, fallback peer connections, and RPC exposure for operators who need a practical EOSIO node hardening reference.

**This is a documentation-first project.** The source material describes security controls; it does not establish a working Go CLI, automated checks, or published release archives.

## Features

- Separate block-producing hosts from public peer nodes and RPC nodes to limit direct exposure.
- Plan fallback communication through trusted private peers and VPN links when public peers become unavailable.
- Restrict RPC access and use HTTPS when public API access is required.
- Exclude wallet and producer administration plugins from publicly accessible RPC nodes.
- Review non-root execution, logging, container settings, and connection limits as part of node hardening.

## Installation

Read the checklist before changing a production deployment. Validate configuration options against your installed EOSIO version; the donor material includes historical settings and plugin names.

For a future Go implementation, check your local toolchain first:

```sh
go version
go env GOPATH
```

No Go package path or buildable command is established by the supplied source, so a `go install` command cannot be provided reliably.

The following is a release-download template, not a confirmed download. Replace `OWNER` with the publishing GitHub account and verify that the `v0.1.0` release contains an archive with this exact filename before use:

```sh
curl -fL "https://github.com/OWNER/eos-bp-nodes-security-checklist/releases/download/v0.1.0/eos-bp-nodes-security-checklist_v0.1.0_linux_amd64.tar.gz" -o eos-bp-nodes-security-checklist_v0.1.0_linux_amd64.tar.gz
```

## Usage

Use the checklist during deployment reviews and after changes to node roles, firewall rules, or peer connectivity. Record evidence for each control rather than treating configuration presence as proof that a control works.

- Confirm that the block-producing host is not directly reachable from the public internet.
- Check that public RPC traffic reaches separate full nodes rather than the producer.
- Inspect enabled plugins and remove wallet or producer administration APIs from public endpoints.
- Test private-peer and VPN fallback paths under controlled conditions.
- Verify process ownership, log collection, and connection limits on each host.

**The command below is a proposed interface, not an implemented command.** It illustrates how a future Go checker could accept a local configuration file and a node role:

```sh
eos-bp-nodes-security-checklist --config /etc/nodeos/config.ini --role producer
```

Until an implementation exists, perform these reviews manually. A configuration review cannot establish DDoS resilience or confirm failover behavior without operational tests. Changing a port also does not replace access controls.

## License

Apache-2.0. This project is based on [slowmist/eos-bp-nodes-security-checklist](https://github.com/slowmist/eos-bp-nodes-security-checklist), whose supplied README credits the SlowMist Security Team and Joinsec Team.

Retain applicable copyright and attribution notices, include the Apache-2.0 license when redistributing derived material, and preserve any applicable upstream NOTICE content. Mark modified files as required by the license.

## Related projects

These repositories were supplied as related projects. Their ownership relationship and implementation details have not been verified.

- [mellyyup789-collab/java-microservice](https://github.com/mellyyup789-collab/java-microservice): Java microservice repository by name; consult its README for its actual scope.
- [MuhammadAhmadMurtaza/grafana-dashboards](https://github.com/MuhammadAhmadMurtaza/grafana-dashboards): Grafana dashboard repository by name; consult its README for available dashboards.
- [sankar1942/docker-arr-suite](https://github.com/sankar1942/docker-arr-suite): Docker Arr-suite repository by name; consult its README for supported services.

