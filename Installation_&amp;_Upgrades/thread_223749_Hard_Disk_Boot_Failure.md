---
title: "Hard Disk Boot Failure"
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by rblang on 2006-07-26
I did the 6.06 install from a CDROM with no errors.  It tells me to remove the CDROM and reboot.  I get the normal bios startup messages. I get a "GRUB LOADING" message then some messages that look like the operating system but flash off the screen much too quickly followed by what appears to be "BOOTING".

At this point the screen goes blank and the normal bios startup messages appear.  This process continues until the power is turned off.  I do not think it is a hard disk hardware problem.  I am using a 10.2Gb drive.  Does anyone have any ideas on where to look for a solution?:-(

---

### Post by confused57 on 2006-07-26
There seems to be a problem with the Dapper6.06-server install CD and certain systems, especially the AMD K6 processor...I haven't heard of any problems with the Alternate or Desktop iso's.
I had the problem myself with the server version installing on a 500 MHz AMD K6-2, just kept rebooting the system...had to install from the alternate cd using the server option.

---

### Post by rblang on 2006-07-27
Thanks for the help.  On closer observation I saw that I was trying to install the server version.  When I switched to the desktop version, it booted from hard disk with no problem.  Slow but working fine.

Bob:D

---

### Post by kenmar on 2006-07-28
I have an AMD K-6 500 mh, and it works fine with the Ubuntu 6.06 desktop installation.  However I had the same problem with the server installation CD - after installing the server, the box went into a continuous reboot "mode" until I shut it down.    Following the above suggestion and reinstalling from the _Alternate_i386 iso gave me a running server and a big smile! Thanks for the help and a big THANKS to the Ubuntu team for a great distro!
Ken

---

### Post by mdrenwick on 2006-08-04
My 6.06 server installation is suffering from similar symptoms.

The PC is a LEX Systems Light And Smart "silent-server", containing a VIA 533MHz (fanless) cpu.

GRUB starts up, successfully performs the root; kernel; and initrd steps, but then the "boot" command results in a reset back to BIOS.

Repeats indefinately.

I'll have a go at the "alternative" install CD over the weekend. Fingers crossed.

My other PC has been running Ubuntu Desktop for a few weeks now, and it's great - hence why I'm persevering with the server.

---

