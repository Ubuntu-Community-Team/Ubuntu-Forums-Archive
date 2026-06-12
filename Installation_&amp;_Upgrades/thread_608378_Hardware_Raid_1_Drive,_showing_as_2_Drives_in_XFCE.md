---
title: "Hardware Raid 1 Drive, showing as 2 Drives in XFCE?"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by fuji_man on 2007-11-09
Hi, I am new to the whole linux thing, so bare with me.

I am running a AMD Xp 2000+ with 1.5GB of ram on abit NF-7 Mobo which have SATA raid controller, no IDE raid.

I have installed Ununtu Server 7.10 and enabled xfce on a main PATA drive, and setup a raid 1 in bios with 2X maxtor 120GB hard drive for storage.

If I use partition Magic, the raid 1 drives is shown as 1X 120GB hard drive, however inside xfce file manager, it show 2X 120GB drive (is this normal)? 

When I click on drive, it ask for password, but after password is entered, (if it is ext3) I can't write anything into the drive and get a permission denied, (if it is ntfs) I can't mount drive, so how to fix either one of this?

I know having 2 drive shown is not normal for a raid 1 dual drive, so do I have to install any driver for the sata raid or not?

Also which is better ntfs or ext3? I will be only using linux.

And do I have to use encrypted + LVM in the install or can I encrypted the drives without LVM, how?

---

### Post by wtfbrb on 2008-01-12
I am having a similar problem, I have a drive for my os's (Ubuntu with virtualbox xp) then I have 2 hard drives that contain all my work data on raid-1.  I use an abit IP35 motherboard and the bios is set to raid and then when I press ctrl-i while booting I have a raid array setup to mirror and both the drives in question are members.  So it appears I have a good config for the mirror, but when I boot into ubuntu 7.10 I see 2 drives.  Arg please help me get this raid working correctly.  I have found many post about this in the forums, but this one has the closest problem to mine.


Thanks in advance,
Mark

---

### Post by miceagol on 2008-01-12
Same problem here. I have 2x320 GB in RAID 1, and a 500 GB in non-RAID. I'm going to install Ubuntu on the 500 GB, but I want my /home folder on the RAID-array.

However, in the Ubuntu-installer, I see the RAID-array only as two separate disks. If I fire up gparted I see the RAID-array in addition to the two disks (/dev/mapper/isw_bhfbehdiee_Mirror).

I thought I'll try to follow [this guide]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto"), but it looks a bit advanced, and I think it's about installing Ubuntu on the RAID-array, which doesn't apply to me.

---

### Post by wtfbrb on 2008-01-13
Finally sorted through all the crap out there and found the best article on the subject...here is the link:

[http://humandoing.net/past/2007/3/13/software_raid_howto_ubuntu_610/](http://humandoing.net/past/2007/3/13/software_raid_howto_ubuntu_610/)

---

### Post by miceagol on 2008-01-14
> **wtfbrb said:**
> Finally sorted through all the crap out there and found the best article on the subject...here is the link:

[http://humandoing.net/past/2007/3/13/software_raid_howto_ubuntu_610/](http://humandoing.net/past/2007/3/13/software_raid_howto_ubuntu_610/)

It's about configuring software RAID, not hardware RAID. 

Anyway, I've heard that the hardware RAID on the motherboards for home users is not a real hardware RAID, since it still depends on drivers in the OS. These drivers are usually just to be found for Windows, so I gave up on RAID.

---

