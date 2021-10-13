# Configuring the pi as a wifi to ethernet bridge

## Document version

1.4

## The legal blah-blah

I do take no responsibility for the below not working or doing damage, etc etc. You get the point.

## Synopsis

Since wlan0 cannot be simply bridged to eth0, we achieve this by reflecting the same wlan0 IP on eth0. We then forward the ARP requests between interfaces. The parprouted and replicateip services are the ones that make this happen. dhcp-helper is for dhcp routing. A custom forwarding binary and startup script allow for other udp broadcast and multicast forwarding.

## Steps

- Connect to WiFi
  - [Ubuntu 20.04](connect-wifi-ubuntu.md)
  - [Raspberry Pi OS](connect-wifi-rpi.md)
- [Check WiFi connection status](check-wifi-stat.md)
- [Install dependencies and openssh](install-deps.md)
- [Get current IP, routes and link status](get-ip.md)
- Connect to the Pi via `ssh`
- [Disable unattended-updates](disable-unattended.md)
- [Enable services](enable-srv.md)
- [Configure IP forwarding](conf-ip-fwd.md)
- [Configure dhcpcd5](dhcpcd5.md)
- [Configure dhcp-helper](dhcp-helper.md)
- [Configure parprouted service](conf-parprouted.md)
- Configure IP replicator
  - [Create bash script](ip-repl-bash.md)
  - [Add systemd service](ip-repl-systemd.md)
- [Ubuntu 20.04 only: Reconfigure netplan to not acquire an IP - dhcpcd5 will handle this from now on](ubuntu-reconf-netplan.md)
- Restart your pi: `$ reboot`
- [resolv.conf - DNS](resolvconf.md)
- Add support for broadcast/multicast
  - [Install binary](udprelay-inst-binary.md)
  - [Install script (optinonally adjust to your needs)](udprelay-inst-script.md)
  - [Install systemd unit](udprelay-inst-systemd.md)
- [Optional: install wavemon to watch and monitor wifi](wavemon.md)
- [Test: final reboot and check services](test.md)
