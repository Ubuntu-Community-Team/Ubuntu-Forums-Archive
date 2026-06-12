---
title: "Display Problem since upgrading to 10.04"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by MadMax2 on 2010-05-13
Description: Some web pages lined and scrambled fonts not forming completely.
eg this type of web page.
[http://salsacycles.com/bikes/vaya/frame/](http://salsacycles.com/bikes/vaya/frame/)
--------------------
I didn't have the problem before upgrading to 10.04

[VGA compatible controller: [COLOR="Red"]ATI Technologies Inc RS480 [Radeon Xpress 200G Series][/COLOR]
	Subsystem: Hewlett-Packard Company Device 2a24
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at d8000000 (32-bit, prefetchable) [[COLOR="Red"]size=128M[/COLOR]]
	I/O ports at ef00 [size=256]
	Memory at fddf0000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion [COLOR="Black"][/COLOR]ROM at fdd00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon

02:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at fdeff000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: bttv
	Kernel modules: bttv

02:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at fdefe000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied> ]
:confused:
Update:
Logging on to other user then out caused a blank screen. Logging back caused the desktop to [flash/ divide in two/go bananas].

Did this:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
max@max-desktop:~$ echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
[sudo] password for max:
options i915 modeset=1
The web page is o.k (so far) but scrambled in the back ground.
Logged out> logged in as new user and was o.k...... so far.
======================
Fixed

After updates? fixed on 24 May @ 9:30 NZ time.
Thanks

---

