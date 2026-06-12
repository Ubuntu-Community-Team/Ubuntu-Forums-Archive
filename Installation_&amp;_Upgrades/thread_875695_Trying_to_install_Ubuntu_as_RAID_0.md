---
title: "Trying to install Ubuntu as RAID 0"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by Timothy Benton on 2008-07-31
I want to install Ubuntu to run as RAID 0, but the installer detects both my hard drives. Shouldn't it be detected as one drive? I am aware that I should not be using "FakeRAID" but I don't know ow o use the software based RAID. How can I install Ubuntu and run it in a RAID 0 array? I don't want to dual boot Windows if that simplifies anything.

Please go step by step, I'm a little slow.

---

### Post by Timothy Benton on 2008-07-31
I found this and am reading it now, hope it solves my problem...
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto#Pre-configure_you_system](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto#Pre-configure_you_system)

---

### Post by dstew on 2008-07-31
That particular How-To is for installing on a FakeRAID system. If you want to do a software RAID, you can use the Alternate Install CD. The installer has options to set up and install to a software RAID. You will probably need to have a non-RAID (or RAID-1) boot partition, because the grub boot loader cannot operate from a striped software RAID, such as RAID-0 or RAID-5. However, if you have a FakeRAID controller, grub can work from there if installed correctly.

---

