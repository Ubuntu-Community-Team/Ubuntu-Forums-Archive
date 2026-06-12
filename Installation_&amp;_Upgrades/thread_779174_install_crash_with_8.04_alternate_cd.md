---
title: "install crash with 8.04 alternate cd"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by zmpk34 on 2008-05-02
I'm new to linux--first time trying this out.  Lots of windows experience.
Trying to install 8.04 using alternate cd iso burnt to cd on HP Pavilion 6648c with AMD K6-2/550mhz proc., 64mb ram, 20ghb hard drive.  Checked md5 of iso before burning and was OK.  CD boots ok and install works ok until it gets to partitioner step.  At that point it goes into a loop or otherwise hangs.  Can't tell if it detects hard drive ok in previous step.  Seems to!  
I've tried different partitionings of the drive including no partitions at all.  Nothing works.  I can partition drive ok using cute partitioner or Partition Magic.

I've tried all the menu options.  Some work, some don't.  I don't know how to do things at the command line level of linux.

Any ideas?

zmpk34

---

### Post by zmpk34 on 2008-05-02
Found the problem.

56mb of ram is not enough to install on this computer.  I plugged in more ram to up the total to 384mb and the partitioner started working correctly and the install proceeded to the 'install base sys' step.

---

