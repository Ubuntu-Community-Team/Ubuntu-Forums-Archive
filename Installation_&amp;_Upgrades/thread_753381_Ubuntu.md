---
title: "Ubuntu"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by SaintHairBall on 2008-04-12
My name is Saint Hair Ball.

I'm a noob.  "hello noob"  I have come to realize that I am powerless over linux.  I believe that a linux power greater than myself can restore my sanity.  

Trying to install Ubuntu 7.10 to AMDxp1700 / seagate 40gb ide/ 640mb pc133 ram

The install begins creating partitions and then just exists out of install with no message display.  This is the end of the system log file. HELP?!

Apr 12 12:23:53 ubuntu kernel: [  513.921412] EXT3 FS on hda7, internal journal
Apr 12 12:23:53 ubuntu kernel: [  513.921614] EXT3-fs: mounted filesystem with ordered data mode.
Apr 12 12:23:53 ubuntu kernel: [  513.967631] kjournald starting.  Commit interval 5 seconds
Apr 12 12:23:53 ubuntu kernel: [  513.968471] EXT3 FS on hda6, internal journal
Apr 12 12:23:53 ubuntu kernel: [  513.968690] EXT3-fs: mounted filesystem with ordered data mode.
Apr 12 12:23:56 ubuntu ubiquity: /usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
Apr 12 12:23:56 ubuntu ubiquity:   warnings.warn("apt API not stable yet", FutureWarning)
Apr 12 12:27:31 ubuntu ubiquity: umount: /target/cdrom: not mounted
Apr 12 12:27:31 ubuntu ubiquity:

---

### Post by Pumalite on 2008-04-12
Memory? Graphics?

---

### Post by SaintHairBall on 2008-04-12
Memory = generic pc133 2x256 1x128 
Graphics geforce fx5200 128mb agp

---

### Post by Pumalite on 2008-04-12
Try the Alternate CD. Don't forget to burn at 4x or less to CD-R after doing md5sum to iso.

---

### Post by twist2b on 2008-04-12
faulty burn to cd/dvd problem I'm guessing

keep your burn speed as LOW as possible, between 2-4x
This is to cause less/no errors.
I also suggest getting the free cd. takes about a month. But the cd is always flawless.

---

### Post by SaintHairBall on 2008-04-16
Swapped graphics card.  OLD = geforce fx5200 128mb agp  NEW = ATI Radeon 9500 pro agp 128.  Installed and runs wonderfully!.

---

