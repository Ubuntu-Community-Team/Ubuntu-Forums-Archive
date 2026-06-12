---
title: "Networking issue after 9.10 upgrade with vmware guest install"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by ktulu05 on 2009-11-13
Hi,

I have an Kubuntu 9.04 VMWare guest image that I upgraded to 9.10 using the normal upgrade process.  Things initially worked well.  I went to use the vm today, and I now have no network connectivity. This guest VM is running under 64-bit Windows 7 RC. 

Because of no networking and a no copy/paste, I can't post the actual command output without re-typing.  Here's what I have under ifconfig:

eth0 with an IPv6 address
eth0:avahi with a 169.254.5.34 address
lo

If I run 'sudo dhclient eth0', it eventually times out with "No DHCPOFFERS received".  I've tried to stop avahi-daemon, but that doesn't solve anything.  

I was hoping to just install vmware tools, and see if that fixes this, but I don't have the right kernel sources installed to compile the tools.

Through my searches, it appears in the past there's been issues with the eth0:avahi entry appearing in ifconfig output, but I haven't found a good solution to get my network access.

Again, while this was an kubuntu 9.04 guest vm, everything ran perfectly.  And the initial upgrade was successful, it just stopped working at some point.

Any clues or thoughts?

-Kevin

---

### Post by ktulu05 on 2009-11-13
I just ran the following commands, based on another post:

sudo ifconfig eth0:avahi down
sudo ifconfig eth0 down
sudo ifconfig eth0 up

the eth0:avahi entry is gone if I run ifconfig once again, but the remaining eth0 entry does not have an ipv4 address, only ipv6.

---

### Post by globalist on 2010-01-09
I have the same problem, eth0 only has an IPv6 address... anyone can help?

---

