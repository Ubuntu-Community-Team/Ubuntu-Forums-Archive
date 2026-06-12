---
title: "RAID 0, error installing ubuntu 14.04"
date: 2014-05-20
forum: Installation &amp; Upgrades
---

### Post by makis-best on 2014-05-20
Hi.

I am new in world of ubuntu and i can't understand this error.
I have Windows 8.1 install in one partition.
I create a new partition for the installation files, one swap partition 
and one partition for home.

When the installation start and show the screen with the time zone
a popup window show with title ??? ??? and message ??? ???
after that the installation stop.

I try changing the partitions or errasing one partition like home but nothing change.

**_I must tell that my system use RAID0 with two HDD._**

Please help.
Thank you.

---

### Post by makis-best on 2014-06-12
nothing?

---

### Post by oldfred on 2014-06-12
Did you install Windows yourself? Is it in BIOS mode or UEFI?

Did you create RAID 0 or are you saying system wants RAID 0?
Desktop installer is not for RAID, I think only server installer works. With 12.04 it was the alternative installer that was for desktops with RAID, but they eliminated that.

       Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

