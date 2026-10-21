# Cisco Packet Tracer DHCP Snooping Lab

A Cisco Packet Tracer network security lab illustrating DHCP snooping protection against rogue DHCP servers.

## Project Overview

This project documents a switch topology containing clients, a router, a server labeled valid DHCP, and another labeled fake DHCP. The goal is to demonstrate DHCP snooping and the distinction between trusted and untrusted switch ports.

## Features

- Rogue DHCP server threat scenario
- Trusted and untrusted switchport concepts
- DHCP snooping VLAN configuration
- Topology screenshot with valid and fake DHCP server labels
- Suggested validation using DHCP client leases and switch CLI

## Technologies Used

- Cisco Packet Tracer
- Cisco Catalyst switch CLI
- DHCP
- Layer 2 security
- IPv4

## Project Structure

```text
packet-tracer-dhcp-snooping-lab/
├── README.md
└── screenshots/
    └── dhcp-snooping-topology.jpg
```

## Network Topology Details

The screenshot shows a 2960-series switch connected to a router, multiple PCs, and two Server-PT devices labeled `VALID DHCP` and `FAKE DHCP`. The image does not expose VLAN IDs or the actual trust configuration, so these must be configured during recreation.

## How to Recreate and Test

1. Add a switch, router, several PCs, and two servers.
2. Connect all devices to the switch and configure a consistent IPv4 subnet or VLAN design.
3. Enable DHCP service on the valid server and configure a pool with the correct gateway.
4. Configure the fake server with a competing DHCP pool for demonstration.
5. On a switch model that supports the feature in Packet Tracer, enable DHCP snooping globally and for the client VLAN.
6. Mark only the interface leading toward the legitimate DHCP server or trusted DHCP path as trusted. Keep client-facing and rogue-server-facing ports untrusted.
7. Renew client DHCP leases and verify that the legitimate server's offers are accepted while rogue offers are blocked.
8. Save the recreated topology as a `.pkt` file.

## Useful Verification Commands

```text
enable
show ip dhcp snooping
show ip dhcp snooping binding
show running-config

# Illustrative configuration; substitute the actual VLAN and trusted interface
configure terminal
ip dhcp snooping
ip dhcp snooping vlan 10
interface fastethernet0/1
 ip dhcp snooping trust
end
show ip dhcp snooping
```

## Expected Results

When supported and configured correctly, DHCP snooping should allow server messages on trusted paths and block unauthorized DHCP server messages arriving on untrusted ports. Exact command support depends on the simulated switch model and Packet Tracer version.

## Screenshots

![Dhcp Snooping Topology](screenshots/dhcp-snooping-topology.jpg)

## Important Notes

The original `.pkt` file was not provided. This package contains the screenshot and documentation only. The screenshot labels the two servers but does not prove that snooping is enabled or that rogue offers were blocked. Commands are illustrative, not tested.

## Portfolio Use

This repository is intended as networking-lab documentation for a student internship portfolio. To present it as a completed practical implementation, recreate and verify the topology in Cisco Packet Tracer and add the resulting `.pkt` file and your own test evidence.
