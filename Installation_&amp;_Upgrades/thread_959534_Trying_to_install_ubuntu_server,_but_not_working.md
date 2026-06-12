---
title: "Trying to install ubuntu server, but not working"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by lorderico on 2008-10-26
I am trying to install ubuntu server edition (the pre-release of 8.1) with ltsp from the alternate cd.  During installation, I get the error:

No interface for ltsp dhcp config found
There are no free interfaces for usage with the ltsp server
Please configure the file /etc/ltsp/dhcp.conf manually by pointing to a valid static interface after the installation finished.

So I click ok, and go on to finish the installation.  After it finished, I rebooted like it told be to do, then logged in via the graphical login screen.  The screen then went black with the white beach-ball cursor that I could move around.  Only the image on the beach ball was static, as opposed to going in circles.  It never logged in, just stayed there.  So I manually powered off the computer, and turned it back on.  Then it comes up with this:

gave up waiting for root device.  Common problems:
-boot args (cat /pro/cmdline)
-check rootdelay = (did the system wait for the right device?)
-missing modules (cat /proc/modules; ls /dev)
Alert /dev/disk/by-uuid/e19de49e-085504aa0b2ef0e95ec1660ed does not exist.  Dropping to a shell!

Then it comes up with:
BusyBox v 1.1o.2
and sometimes throughout my shell session it displays this: ata2: SRST failed (errno =-16)

I reinstalled it without LTSP (still using the alternate cd), and aside from not getting the first error, it did the same thing.

I have no clue what's going on, can you help?
Thanks,
Eric

---

### Post by cariboo on 2008-10-26
I would suggest downloading the server installation CD with out the desktop first, then install a minimal desktop, if you really need to. To run ltsp you need two nics. If you plan on running a sever you should really give it a static ip address as a lot of services count finding the same ip address every time.

Jim

---

