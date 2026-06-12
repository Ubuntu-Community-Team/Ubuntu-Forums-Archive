---
title: "[SOLVED] Upgrade to Gutsy CD/DVD Drive weird problem"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by tomski on 2007-10-01
Hi there,

I have just upgraded from Feisty to Gutsy

before i did thid i cleaned out all orphan packages & removed downloaded cache for apt
rebooted
all was ok 
removed compiz-fusion from feisty
added metacity to sessions
rebooted
all ok 
upgraded to gutsy:

alt+F2:
upgrade-manager -c -d

2 hours later & 3 question answers & bingo gutsy desktop with wobbly windows & shadows
but now every 2 seconds my CD/DVD drive is being polled & light flashes but i have lots of Device-Mapper errors in the following log files:
syslog
messages
kernlog
debug

also when i ctrl+alt+F2 to get default tty2 these warnings are scrolling on the screen too???

i can access dvd's & cd's but i still get the warnings

udevd runs constantly with 70-80% CPU

I cannot access my 2nd harddrive that has 2 partitions(ntfs) they are just not there as well as any other ntfs partitions

do you think that udevd has been misconfigured during the upgrade?
if so how do i re-configure this??
or could this be because the new pata drivers are unsupported?

Thred with similar issue:
[http://ubuntuforums.org/showthread.php?t=515394](http://ubuntuforums.org/showthread.php?t=515394)

---

### Post by tomski on 2007-10-01
Very odd

after leaving my PC off all night & day to think about the issue and not kill my CD/DVD drive
The problem has gone??
but know i am left with a harddrive thats un-accessable.
i have tried to use the ntfs config tool but it fails
also i notice my drives are now listed as SDa,b,c, whereas they used to be HDa,b,c,d
What has caused this change?
am i for some reason a SCSI driver or software ??

---

### Post by tomski on 2007-10-03
I have just changed the thread title because the CD/DVD problem appears to have fixed itself but now i am left in a situation where my harddrives are listed as sda,b,c etc instead of hda,b,c etc??

I know this is wrong because i donot use SCSI controller for any drive & these are pata & not sata

any fixes or advice would be much appreciated

Hre is a link to the bug report i have filed:

[https://bugs.launchpad.net/ubuntu/+bug/148062](https://bugs.launchpad.net/ubuntu/+bug/148062)

---

### Post by tomski on 2007-10-04
This is what is appearing repeated in syslog:
Oct  4 19:16:53 localhost kernel: [  923.593827] device-mapper: table: 254:2: linear: dm-linear: Device lookup failed
Oct  4 19:16:53 localhost kernel: [  923.594384] device-mapper: ioctl: error adding target to table
This is repeated over and over in kern.log:
Oct  4 19:10:47 localhost kernel: [  557.316103] device-mapper: ioctl: error adding target to table
Oct  4 19:10:47 localhost kernel: [  557.329463] device-mapper: table: 254:2: linear: dm-linear: Device lookup failed

This is repeated in messages:
Oct  3 23:50:31 localhost kernel: [  740.765650] device-mapper: ioctl: error adding target to table

I also still can't use my second harddrive:(

i have no idea what is causing this please help

---

### Post by tomski on 2007-10-13
Technically this is still unsolved but i resolved my issue's by backing up all important files and clean install gutsy

sorry to the moderators but i had to find a quick solution to this so that i did not harm any of my hard drives or dvd drive!!

---

### Post by makeyre on 2007-10-13
This is actually a major problem - the workaround to it is to uninstall evms.  See [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/119315/](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/119315/)

---

### Post by pikmaster on 2007-11-29
If you cannot access the second harddisk and removing evms does not help, have a look into /dev/mapper directory. During feisty to gutsy upgrade my** /dev/sda2** drive has been renamed to **/dev/mapper/sda2** and I had to correct my */etc/fstab* entry to acces my partition again. What was more confusing, there is still /dev/sda2 device which is another disk.

---

