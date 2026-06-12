---
title: "G5 Xserve will not boot off cd"
date: 2014-01-03
forum: Installation &amp; Upgrades
---

### Post by brycehenley97 on 2014-01-03
I have been trying to boot two G5 Apple Xserves PPC for the last few weeks. Right now I have a optical drive from a pc running inside the hot swap drive bay. I have tried booting disks(4.3gib dvds) for Ubuntu 12.04 PPC, Ubuntu 12.04 alternate PPC, Lubuntu 12.04 PPC, and Debian 7.3 PPC.
 I tried all of the following: holding c at start (usually sent the monitor into a strobing state, or did nothing), trying to boot the cd in open firmware(returns: can't OPEN: cd:,\install\yaboot), and holding alt down at boot and selecting disk with penguin logo(black screens then goes back to alt selection menu with mouse a different color and more graphics problems), resetting firmware and changing boot order off front panel, and i tried target disk mode between the two servers to install, along with my laptop(not mac or PPC). I have also previously tried booting off the hard drive by doing a image restore using iso, and by mounting the image and copying in primary partition using Apple Partition map, this had same results as cd when selected after holding alt, along with trying to boot from usb(may or not be possible). I do not have another mac, unless you count the other server that is also not working. These do not have OSX on them so there is no chance for a firmware update. I have access to only computers running Debian or Ubuntu based systems that are x64 or x86 Intel architecture.

I'm an experienced Linux user, and I know my way around hardware, but This is the first mac I have ever tried installing Linux on. Thank you in advance

here are the system specs:
Apple Xserve G5
4gb of DDR ram (have tried running configurations 1gb, and 2gb and 3gb)
dual 64bit IBM processors
one drive bay, with stock 80gb Segate Barracuda(7200rpm)
ATI Radeon graphics card PCIX
power supply(unknown Chinese, works)
has internet connection through 1gib/s onboard interface
firmware from circa 2004
a sata cdrom drive out of a Dell XPS 8300 desktop (using the same drive to burn and read for boot just swapping machines)

some interesting things I have noticed:
 the system clock is radically off
the graphics issues in firmware
on one disk it failed to read the first sector, the others specifically yaboot 

[IMG]http://s1294.photobucket.com/user/brycehenley/media/0102141738_zps4ebb973a.jpg.html[/IMG]
[IMG]http://s1294.photobucket.com/user/brycehenley/media/0102141822_zps87a344d6.jpg.html[/IMG]
[IMG]http://s1294.photobucket.com/user/brycehenley/media/0102141640a_zps2b6ca298.jpg.html[/IMG]

---

### Post by brycehenley97 on 2014-01-05
Here is an update, I got OSX 10.4 installed and updated off the same optical drive used with the linux disks. I have updated the firmware to the latest version released for an Xserve G5 (Firmware Update Version 5.1.7f1).*I have also tried installing FreeBSD 8.1, 9.2 64bit, and 9.2 32bit PPC versions. I was able to begin booting FreeBSD 9.2 disks but they*stopped*mid boot because of a*kernel*issue in open firmware. I have also tried Ubuntu 6.10 The last version that*official*supported PPC*architecture. All of these disks were burned by OSX disk utility instead of on linux this time.

Im*actually*writing this on one of the servers, so the hardware is not broken and the firmware works.*
Thankyou*for reading.

here is a copy of the failed FreeBSD boot, I was not able to continue at the end because it was frozen:

Consoles: Open Firmware console

FreeBSD/powerpc64 Open Firmware loader, Revision 0.1
(root@snap.freebsd.org, Fri Sep 27 02:45:25 UTC 2013)
Memory: 1048576KB
Booted from: /ht@0, f2000000/pci@7/k2-sata-root@c/k2-sata@1/disk@0

\
can't load 'kernel'

Type '?' for a list of commands, 'help' for more detailed help.
OK _

---

