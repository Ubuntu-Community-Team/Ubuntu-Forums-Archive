---
title: "installing dhcp3-server on 11.04 natty"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by loha2x on 2011-07-08
hi, guys
As the title saying I'm having problem installing dhcp3-server actually
I've already installed it but I can't start the service. There ain't any command.

I'm using 11.04 natty narwhal.

Here's what I've tried.

```

#dpkg -l | egrep dhcp3-server
ii  dhcp3-server                       4.1.1-P1-15ubuntu9                      ISC DHCP server (transitional package)

``````

#find / -name dhcp3
/etc/dhcp3
/var/lib/dhcp3

``````

#service --status-all
 [ ? ]  acpi-support
 [ ? ]  acpid
 [ ? ]  alsa-restore
 [ ? ]  alsa-store
 [ ? ]  anacron
 [ + ]  apparmor
 [ ? ]  apport
 [ ? ]  atd
 [ ? ]  avahi-daemon
 [ ? ]  binfmt-support
 [ + ]  bluetooth
 [ - ]  bootlogd
 [ - ]  brltty
 [ ? ]  console-setup
 [ ? ]  cron
 [ ? ]  cups
 [ ? ]  dbus
 [ ? ]  dmesg
 [ ? ]  dns-clean
 [ ? ]  ecryptfs-utils-restore

``````

#service dhcp3-server restart
dhcp3-server: unrecognized service

```it's definitely there but there isn't...
I usually installed it really easily and configured it my way around but
I just can't start the service, is it because I'm using 11.04 which is as long as I'm concerned is very unstable.

But when I tried

```

#dhcpd
Internet Systems Consortium DHCP Server 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
Wrote 3 leases to leases file.
at0 missing an interface address
Listening on LPF/at0/00:26:b6:52:7e:cc/192.168.23.0/24
Sending on   LPF/at0/00:26:b6:52:7e:cc/192.168.23.0/24
Sending on   Socket/fallback/fallback-net
Can't create PID file /var/run/dhcpd.pid: Permission denied.

```so dhcpd == dhcp3-server ???
does dhcp3-server changed their name to dhcpd?

Any suggestions are welcome :smile:

---

### Post by T40 on 2011-07-27
hello to you,
I just tried to do the same thing and I ran into exactly the same issues.
A little bit of google and I managed to get it to work but I must admit it's confusing.
 In order to configure DHCP server, I had to install the package isc-dhcp-server
  

sudo apt-get install isc-dhcp-server
  

to start that service edit: 
edit /etc/dhcp/dhcpd.conf  

sudo service isc-dhcp-server start - [OK]
  

cat /var/lib/dhcp/dhcpd.leases – shows leases


I did not get dhcp3-server to work, but again, I think it isc-dhcp-server is the appropriate package for natty now.


Best regards
Mariusz

---

