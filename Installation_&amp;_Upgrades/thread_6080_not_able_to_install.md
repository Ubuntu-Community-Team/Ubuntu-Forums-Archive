---
title: "not able to install"
date: 2004-11-24
forum: Installation &amp; Upgrades
---

### Post by rlocone on 2004-11-24
Hello All!

This is the second distro I'm not able to get working on my system.  The first was Gentoo, now Ubuntu.  Here are the following errors I'm getting at bootup:

Very first line in boot screen.
1) MP-Bios Bug 8254 - Timer not connected to IO-APIC

Going into X server.
2) Fatal Error: No Screens Found
3) Failed to set up write combing ranges

Trying to Shutdown.
4) Init Timeout writing control channel /dev/initctrl

Now, if I go into fail safe mode the following happens:  Xserver comes up but no mouse control.

Next No network.  If it comes up it's only IPv6 only.  If I try to add a route to it, it's the following: route add default gw 192.168.0.1.
---

Now if I use the expert mode:  CD comes up fine w/ the network, but "No Screens" is displayed then exit complete & reboots.

Thanks
-rlocone
[http://www.rlocone.com](http://www.rlocone.com)
[http://www.i386srv2k.com](http://www.i386srv2k.com)

---

