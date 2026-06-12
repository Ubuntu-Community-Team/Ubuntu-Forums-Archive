---
title: "Boot ltsp client in Edgy"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by brucel on 2007-01-21
Good day, all

I'm battling at present with setting up a ltsp environment with Edgy. I have the ltsp server installed, I've run the ltsp-build-client script (twice!!), I have dhcp and tftp set up as required. When I start up the client machine (AMD64) to network-boot, it gets an IP address ok, gets the initial boot image and starts loading the main image; then part way through the boot process I get:
ipconfig: eth0: SIOCFGINDEX: No such device
ipconfig: no devices to configure
'init: .: 1: Can't open /tmp/net-eth0.conf
Kernel panic....

The ltsp server is an AMD64X2 with a Gigabyte GA-M51GM-S2G motherboard, the client uses the same MB with onboard NVidia LAN chip. The standard Edgy installation on the main (server) machine is fine... it's just getting the ltsp client boot-up that's a problem.

Any help or input much appreciated!!... also, apologies if this is posted in the wrong area... my first real post on these forums

Bruce

---

### Post by linxonline on 2008-02-14
Iv got the same problem, however its with using an ASUS EEE as a client.

---

### Post by schwieb on 2008-03-04
For the Vostro, try here:
[http://ubuntuforums.org/showthread.php?t=552080](http://ubuntuforums.org/showthread.php?t=552080)

For the eee pc, this may work for you (I'll be trying it when I get home today):
[http://forum.eeeuser.com/viewtopic.php?pid=153913](http://forum.eeeuser.com/viewtopic.php?pid=153913)

---

