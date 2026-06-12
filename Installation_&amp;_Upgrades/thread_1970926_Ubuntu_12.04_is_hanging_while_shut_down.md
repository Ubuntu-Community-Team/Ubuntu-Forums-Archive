---
title: "Ubuntu 12.04 is hanging while shut down"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by jsmanian on 2012-05-01
Dear All,

     I installed ubuntu 12.04LTS last week. It looks good and I have one issue. It is not properly shutting down. It hangs on by showing ubuntu background in pink color. I checked syslog. I think that network manager is causing this problem. I attached syslog here. 

syslog
[PHP]May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): disconnecting for new activation request.
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): device state change: activated -> disconnected (reason 'none') [100 30 0]
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): deactivating device (reason 'none') [0]
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): canceled DHCP transaction, DHCP client pid 6124
May  1 21:31:08 jsm avahi-daemon[793]: Withdrawing address record for 192.168.42.150 on usb0.
May  1 21:31:08 jsm avahi-daemon[793]: Leaving mDNS multicast group on interface usb0.IPv4 with address 192.168.42.150.
May  1 21:31:08 jsm NetworkManager[744]: <info> DNS: starting dnsmasq...
May  1 21:31:08 jsm avahi-daemon[793]: Interface usb0.IPv4 no longer relevant for mDNS.
May  1 21:31:08 jsm dnsmasq[6142]: exiting on receipt of SIGTERM
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): writing resolv.conf to /sbin/resolvconf
May  1 21:31:08 jsm dnsmasq[6238]: started, version 2.59 cache disabled
May  1 21:31:08 jsm dnsmasq[6238]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May  1 21:31:08 jsm dnsmasq[6238]: warning: no upstream servers configured
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) starting connection 'Wired connection 2'
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 1 of 5 (Device Prepare) scheduled...
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 1 of 5 (Device Prepare) started...
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) scheduled...
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 1 of 5 (Device Prepare) complete.
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) starting...
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): device state change: prepare -> config (reason 'none') [40 50 0]
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) successful.
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) scheduled.
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) complete.
May  1 21:31:08 jsm dbus[701]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) started...
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): device state change: config -> ip-config (reason 'none') [50 70 0]
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May  1 21:31:08 jsm NetworkManager[744]: <info> dhclient started with pid 6247
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Beginning IP6 addrconf.
May  1 21:31:08 jsm avahi-daemon[793]: Withdrawing address record for fe80::e864:aeff:feda:7d72 on usb0.
May  1 21:31:08 jsm avahi-daemon[793]: Leaving mDNS multicast group on interface usb0.IPv6 with address fe80::e864:aeff:feda:7d72.
May  1 21:31:08 jsm avahi-daemon[793]: Interface usb0.IPv6 no longer relevant for mDNS.
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) complete.
May  1 21:31:08 jsm dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
May  1 21:31:08 jsm dhclient: Copyright 2004-2011 Internet Systems Consortium.
May  1 21:31:08 jsm dbus[701]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May  1 21:31:08 jsm dhclient: All rights reserved.
May  1 21:31:08 jsm dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  1 21:31:08 jsm dhclient: 
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): DHCPv4 state changed nbi -> preinit
May  1 21:31:08 jsm dhclient: Listening on LPF/usb0/ea:64:ae:da:7d:72
May  1 21:31:08 jsm dhclient: Sending on   LPF/usb0/ea:64:ae:da:7d:72
May  1 21:31:08 jsm dhclient: Sending on   Socket/fallback
May  1 21:31:08 jsm dhclient: DHCPREQUEST of 192.168.42.150 on usb0 to 255.255.255.255 port 67
May  1 21:31:08 jsm dhclient: DHCPACK of 192.168.42.150 from 192.168.42.129
May  1 21:31:08 jsm dhclient: bound to 192.168.42.150 -- renewal in 1581 seconds.
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): DHCPv4 state changed preinit -> reboot
May  1 21:31:08 jsm NetworkManager[744]: <info>   address 192.168.42.150
May  1 21:31:08 jsm NetworkManager[744]: <info>   prefix 24 (255.255.255.0)
May  1 21:31:08 jsm NetworkManager[744]: <info>   gateway 192.168.42.129
May  1 21:31:08 jsm NetworkManager[744]: <info>   hostname 'jsm'
May  1 21:31:08 jsm NetworkManager[744]: <info>   nameserver '192.168.42.129'
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Commit) started...
May  1 21:31:08 jsm avahi-daemon[793]: Joining mDNS multicast group on interface usb0.IPv4 with address 192.168.42.150.
May  1 21:31:08 jsm avahi-daemon[793]: New relevant interface usb0.IPv4 for mDNS.
May  1 21:31:08 jsm avahi-daemon[793]: Registering new address record for 192.168.42.150 on usb0.IPv4.
May  1 21:31:09 jsm dnsmasq[6238]: exiting on receipt of SIGTERM
May  1 21:31:09 jsm NetworkManager[744]: <info> DNS: starting dnsmasq...
May  1 21:31:09 jsm NetworkManager[744]: <info> (usb0): writing resolv.conf to /sbin/resolvconf
May  1 21:31:09 jsm dnsmasq[6265]: started, version 2.59 cache disabled
May  1 21:31:09 jsm dnsmasq[6265]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May  1 21:31:09 jsm dnsmasq[6265]: using nameserver 192.168.42.129#53
May  1 21:31:09 jsm NetworkManager[744]: <info> (usb0): device state change: ip-config -> activated (reason 'none') [70 100 0]
May  1 21:31:09 jsm NetworkManager[744]: <info> Policy set 'Wired connection 2' (usb0) as default for IPv4 routing and DNS.
May  1 21:31:09 jsm NetworkManager[744]: <info> Activation (usb0) successful, device activated.
May  1 21:31:09 jsm NetworkManager[744]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Commit) complete.
May  1 21:31:10 jsm avahi-daemon[793]: Joining mDNS multicast group on interface usb0.IPv6 with address fe80::e864:aeff:feda:7d72.
May  1 21:31:10 jsm avahi-daemon[793]: New relevant interface usb0.IPv6 for mDNS.
May  1 21:31:10 jsm avahi-daemon[793]: Registering new address record for fe80::e864:aeff:feda:7d72 on usb0.*.
May  1 21:31:19 jsm kernel: [20745.568019] usb0: no IPv6 routers present
May  1 21:31:28 jsm NetworkManager[744]: <info> (usb0): IP6 addrconf timed out or failed.
May  1 21:31:28 jsm NetworkManager[744]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May  1 21:31:28 jsm NetworkManager[744]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May  1 21:31:28 jsm NetworkManager[744]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May  1 21:31:36 jsm ntpdate[6299]: adjust time server 91.189.94.4 offset 0.025567 sec
May  1 21:57:29 jsm dhclient: DHCPREQUEST of 192.168.42.150 on usb0 to 192.168.42.129 port 67
May  1 21:57:29 jsm dhclient: DHCPACK of 192.168.42.150 from 192.168.42.129
May  1 21:57:29 jsm dhclient: bound to 192.168.42.150 -- renewal in 1505 seconds.
May  1 21:57:29 jsm NetworkManager[744]: <info> (usb0): DHCPv4 state changed reboot -> renew
May  1 21:57:29 jsm NetworkManager[744]: <info>   address 192.168.42.150
May  1 21:57:29 jsm NetworkManager[744]: <info>   prefix 24 (255.255.255.0)
May  1 21:57:29 jsm NetworkManager[744]: <info>   gateway 192.168.42.129
May  1 21:57:29 jsm NetworkManager[744]: <info>   hostname 'jsm'
May  1 21:57:29 jsm NetworkManager[744]: <info>   nameserver '192.168.42.129'
May  1 21:57:29 jsm dbus[701]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May  1 21:57:29 jsm dbus[701]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May  1 22:17:01 jsm CRON[6355]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 22:22:34 jsm dhclient: DHCPREQUEST of 192.168.42.150 on usb0 to 192.168.42.129 port 67
May  1 22:22:34 jsm dhclient: DHCPACK of 192.168.42.150 from 192.168.42.129
May  1 22:22:34 jsm dhclient: bound to 192.168.42.150 -- renewal in 1645 seconds.
May  1 22:49:59 jsm dhclient: DHCPREQUEST of 192.168.42.150 on usb0 to 192.168.42.129 port 67
May  1 22:49:59 jsm dhclient: DHCPACK of 192.168.42.150 from 192.168.42.129
May  1 22:49:59 jsm dhclient: bound to 192.168.42.150 -- renewal in 1435 seconds.
May  1 23:13:54 jsm dhclient: DHCPREQUEST of 192.168.42.150 on usb0 to 192.168.42.129 port 67
May  1 23:13:54 jsm dhclient: DHCPACK of 192.168.42.150 from 192.168.42.129
May  1 23:13:54 jsm dhclient: bound to 192.168.42.150 -- renewal in 1465 seconds.
May  1 23:17:01 jsm CRON[6414]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 23:38:19 jsm dhclient: DHCPREQUEST of 192.168.42.150 on usb0 to 192.168.42.129 port 67
May  1 23:38:19 jsm dhclient: DHCPACK of 192.168.42.150 from 192.168.42.129
May  1 23:38:19 jsm dhclient: bound to 192.168.42.150 -- renewal in 1450 seconds.[/PHP]

     Please help to me to solve this issue. I also has issue in connecting to internet through mobile gprs modem. I opened separate thread for this one.

with regards,
Subramanian

---

