# IP and VLAN Table

## VLANs and Subnets
| VLAN | Name | Subnet | Gateway (SVI) | Addressing |
|------|------|--------|---------------|------------|
| 10 | GAMING | 192.168.10.0/24 | 192.168.10.1 | DHCP |
| 20 | STAFF | 192.168.20.0/24 | 192.168.20.1 | DHCP |
| 30 | GUEST_WIFI | 192.168.30.0/24 | 192.168.30.1 | DHCP |
| 40 | SERVICES | 192.168.40.0/24 | 192.168.40.1 | Static |
| 99 | MANAGEMENT | 192.168.99.0/24 | 192.168.99.1 | Static |

## DHCP
| Pool | Network | Excluded (static) | Default gateway |
|------|---------|-------------------|-----------------|
| GAMING | 192.168.10.0/24 | 192.168.10.1 - 192.168.10.20 | 192.168.10.1 |
| STAFF | 192.168.20.0/24 | 192.168.20.1 - 192.168.20.20 | 192.168.20.1 |
| GUEST | 192.168.30.0/24 | 192.168.30.1 - 192.168.30.20 | 192.168.30.1 |

## Edge Router and ISP
| Link | Addressing |
|------|------------|
| Core switch to edge router | 10.0.0.2/30 - 10.0.0.1/30 |
| Edge router to ISP | 203.0.113.2/24 - 203.0.113.1/24 |
| Public server | 198.51.100.10/24 |

## Notes
- The first 20 addresses of each DHCP subnet are reserved for static infrastructure.
- NAT/PAT on the edge router covers the internal subnets (192.168.0.0/16).
- The guest ACL (inbound on the VLAN 30 SVI) blocks 192.168.0.0/16 except DHCP.