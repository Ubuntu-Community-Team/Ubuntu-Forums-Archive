---
title: "Fiesty Minimal Install - no dns resolution?"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by spliner on 2007-10-09
Alright, did a 7.04 32bit minimal/command line install.  Would like to install flux.  I ran into one small problem, during the install I gave my system an IP/subnet/gateway but gave it the wrong DNS number.  I now have no dns resolution and am stuck with the install.  I can log in but not install any packages/download updates because I have no dns resolution.  I found what I thought was the config file, and changed the DNS number (can't remember what file it was, but it had the incorrect DNS number, IP/Sub/Gateway) to the correct one, but still no go.  Can't ping a name on the Internet nor get update packages.

I'm a newb to Linux, and seem to mutter my way around Gnome fairly well, but command line options are beyond me.  Can someone tell me the correct procedure to set up eth0 for Internet when the settings were wrong on the install?  I could just re-do the command line install with the alternate CD again, but it takes a while on this machine and would rather learn how to fix it.

Thanks,

Spliner

---

### Post by spliner on 2007-10-09
anyone?

I need commands for a terminal to configure:

eth0's IP address, subnet, gateway, DNS  (IPv4)
enable/disable ethernet interfaces
reset or test dns resolution

etc.

---

### Post by webdr on 2007-10-11
to do a static config on eth0:
ifconfig eth0 xxx.xxx.xxx.zzz netmask 255.255.255.0 up
ip route add default via xxx.xxx.xxx.yyy (gw ip address)

edit dns server(s)
sudo nano /etc/resolv.conf

resolve.conf should contain entries like this:
nameserver xxx.xxx.xxx.sss
nameserver 4.2.2.2

making sense of all this...
if we were using a 10. network and /24 subnet or 255.255.255.0...
ifconfig eth0 10.24.24.100 netmask 255.255.255.0 up
ip route add default via 10.24.24.1

example resolv.conf entries:
nameserver 10.24.24.1
nameserver 4.2.2.2

Hope this helps you, 8)

---

### Post by webdr on 2007-10-11
Almost forgot ... dig <hostname> is handy for dns diagnostics
example:
dig markw.net

---

### Post by spliner on 2007-10-15
Thanks,

I gave up and did a re-install, but that will be helpful for the future.

Spliner

---

