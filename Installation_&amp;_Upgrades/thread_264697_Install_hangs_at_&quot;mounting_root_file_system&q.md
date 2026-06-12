---
title: "Install hangs at &quot;mounting root file system&quot;."
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by sjlauritsen on 2006-09-25
Hi guys!

I have had the following problem:

The Ubuntu 6.06 install hangs at "Mounting Root File System" when booting from the install cd. I get a "hdc error in sector n" or the like. I have seen this problem reported a lots of places, but never seen a solution I could use. This post is my solution to the problem, in case anyone could use it.

System:
Fujitsu/Siemens AMILO M1425 Laptop.
ATI Radeon 9700 Mobility
Standard hardware. Nothing fancy, normally no problems.

Applies to Ubuntu version:
Dapper Drake 6.06

Symptoms:
Install hangs with a "hdc error in sector n" - or similar error.
Install cd ISO checksum is OK!
Install cd works on other pc's!

Solution:
I've burned the cd againg using 8 speed. At first I've burned it with 24x, but it seems to have a problem with that. So a reduced burn speed, and the system installed like a charm.

AMILO M1425 speciality:
Oh and btw. when you get Xorg up and running, it will use the 1024x768 resolution. This looks pretty bad! So you will have to change it to 1280x800 - however Xorg will not do this the right way. The problem is solved by editing the configuration file manually (/etc/X11/xorg.conf - or around there) and find the display settings with depth 24. Add "1280x800" to the front of the list. Save whatever work you have running. Restart the X server (CTRL+ALT+BACKSPACE) and voila! :-)

---

