---
title: "System time incorrectly reset by Ubuntu (dual boot)"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by misterbk on 2009-12-12
Hi guys, 

This is my problem - In Windows, I set the system time using NTP.  When I boot into Linux, Ubuntu also sets the clock using NTP, but uses some time other than the local timezone, and clock is 4 hours behind.  (Ubuntu is set to same timezone as Windows.)

In other Linux installers, there is an option how Linux should treat the system clock.  This is there so that if you have another OS (Windows) that treats the system clock as the local time, things work together.  In the Ubuntu installer, they have removed this option.

Honestly I don't know why someone would want their bios to not be set to local time, but it seems to have been made the default.  When set this way, hardware-based system log events generated through the BIOS, and other things like server management boards (SMB) and RAID cards, have the incorrect timestamp.  It could be useful if coordinating hardware events between multiple servers in a global network, but really is that the "default" usage of Ubuntu?

I dug around and found this solution.  It's from two years ago.  I expect it to work, but can someone verify for me whether this is the CORRECT way to solve this problem?

(i.e. putting a Cisco router with failed fans in a freezer will keep it running...  but is not the CORRECT way to fix the problem.)

this thread, very bottom:
[http://ubuntuforums.org/showthread.php?t=534578&highlight=time+resets+dual+boot](http://ubuntuforums.org/showthread.php?t=534578&highlight=time+resets+dual+boot)

[QUOTE=fallencyi]sudo gedit /etc/default/rcS


Change:

UTC=yes

to

UTC=no[/QUOTE]

---

