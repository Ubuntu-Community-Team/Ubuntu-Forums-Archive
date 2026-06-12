---
title: "casper, live cd, dhcp assigned hostname"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by dreh on 2012-11-01
I'm booting sucessfull via pxeboot a live ubuntu remix. I wan't to set the hostname via dhcp because I'm booting several instances of the same image. Right now I'm using a hookline in /etc/dhcp/dhclient-enter-hooks.d/pinhostname that works quite well.

RUN="yes"
if [ "$RUN" = "yes" ]; then
var=`/sbin/ifconfig eth0 | /usr/bin/awk '/inet addr/ {print $2}' | /usr/bin/cut -f2 -d:`
var=`/usr/bin/dig -x $var +short`
var=`echo $var | /usr/bin/awk -F. '{print $1}'`
/bin/hostname $var
fi

But the dhcp server comes to late for munin etc and the hostname is not set in time. In the Casper log it shows me it receives the hostname much earlier:

IP-Config: eth0 hardware address 08:00:27:86:3e:84 mtu 1500 DHCP RARP
IP-Config: eth0 complete (from 10.1.1.1):
address: 10.1.1.10        broadcast: 10.1.1.255       netmask: 255.255.255.0
gateway: 10.1.1.1         dns0     : 10.1.1.1         dns1   : 0.0.0.0
host   : storage1
domain : domain.com
rootserver: 10.1.1.1 rootpath:
filename  : pxelinux.0

How can I set that host name. I think I need to put a script in /scripts before I pack the initrd. The file init looks promising too. There a loads of different scripts where would I put mine? Thank you for your time

---

