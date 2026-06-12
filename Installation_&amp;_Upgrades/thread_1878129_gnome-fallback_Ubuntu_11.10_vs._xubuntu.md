---
title: "gnome-fallback Ubuntu 11.10 vs. xubuntu"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by bob12564 on 2011-11-09
I just bought a new HP Compaq laptop with Windows 7 and I want to set up a dual boot with some version of ubuntu which I've been running on 3 other computers for about 3 years.

I don't want to use Unity and I am aware of the gnome-fallback install to get something that looks like the gnome 2.0 desktop. 

Does anyone have a sense of whether the fallback code will be maintained in future versions or does it make sense to move to xubuntu/xfce which looks more like the old gnome classic desktop?

I tried installing xubuntu but unlike my past ubuntu installs, the xubuntu (and maybe ubuntu) installer doesn't seem to want to automatically resize the partitions to create space for linux.  I'm not comfortable doing this myself.  There are partitions for HP Tools and Recovery.  It looks like there's a partition sda2 that can be shrunk but I don't know the impact to the other partitions.  Will Tools, Recovery, and even Windows 7 still work?  

I just want to use the computer and not get too involved in the mechanics of it.  Simple answers, please!  And thanks for the help!!

---

### Post by Gatemaze on 2011-11-09
A word of warning, any type of resizing is a risky water operation. If I were you I would stick with 10.04 (as I actually do). It is much more stable and it has gnome2. You will have to upgrade in two years but till then who knows what will be happening. Regarding the partitioning it is a tricky operation but it is something that you should learn at some point.

---

### Post by Gatemaze on 2011-11-09
It also occured to me that if it is a problem xith the xubuntu installer then you can install through the usual ubuntu cd if it works fine and install from the repo the xubuntu dekstop.

---

### Post by bob12564 on 2011-11-09
I still have the original question about which version to install: ubuntu with the fallback vs. xubuntu/xfce.

I've been reading about the partitioning and I now know why I'm not getting the option to install ubuntu alongside Windows 7.  This is where I need most of my help.

It seems that Windows only allows 4 primary partitions and all 4 are used because of the Tools and Recovery partitions.  Getting any version of linux installed requires some way to create free disk space to make an extended partition (for linux) while not disturbing the 4 primary partitions.  The only free space is in sda2 which is a bootable partition.  Windows 7 System is is the sda1 partition.

It looks like many manufacturers are loading recovery partitions because they no longer ship Windows CDs with the computer.  I can't see how anyone gets linux installed in a dual boot situation without wrecking Windows.

I know it can be done and I'm still reading.  But if anyone can explain the process in a simple and foolproof way, I think many people would be grateful.  This is a Microsoft world and it's tough to get around their way of doing things.

Thanks again.

---

### Post by Gatemaze on 2011-11-09
> **bob12564 said:**
> I still have the original question about which version to install: ubuntu with the fallback vs. xubuntu/xfce.

Install ubuntu with fallback also xubuntu-desktop... so you will have both. In linux world you choose what to use. Use them both and see which one you like. If you want a dictator's command then use ubuntu 10.04 with gnome2 :).

> **bob12564 said:**
> 
I've been reading about the partitioning and I now know why I'm not getting the option to install ubuntu alongside Windows 7.  This is where I need most of my help.

It seems that Windows only allows 4 primary partitions and all 4 are used because of the Tools and Recovery partitions.  Getting any version of linux installed requires some way to create free disk space to make an extended partition (for linux) while not disturbing the 4 primary partitions.  The only free space is in sda2 which is a bootable partition.  Windows 7 System is is the sda1 partition.

It looks like many manufacturers are loading recovery partitions because they no longer ship Windows CDs with the computer.  I can't see how anyone gets linux installed in a dual boot situation without wrecking Windows.

I know it can be done and I'm still reading.  But if anyone can explain the process in a simple and foolproof way, I think many people would be grateful.  This is a Microsoft world and it's tough to get around their way of doing things.

Thanks again.

It's not windows that allows 4 PRIMARY partitions but the way that hard disk partitioning works (cant recall from the top of my head who is exactly to blame). Anyway you only need one partition to be available and then you define it as extended with as many  logical volumes as you want. There are tones of posts about this both in this forum and on the web. Give us your partition table (easiest a screenshot from gparted and we can work from there).

An example of my laptop partition is:

partition 1: primary - win xp
partition 2: extended
  p.2.1: logical - linux root (ext4)
  p.2.2: logical - share between xp and linux (ntfs)
  p.2.3: logical - linux home (ext3)
  p.2.4: logical - linux swap
partition 3: primary - recovery system (not a clue of its filesystem)

---

### Post by subehsharma on 2011-11-10
Here's what i did while installing Xubuntu:

- Logged into Windows (I'm dual booting)
- Shrank the size of a partition using "Disk Management" option available in windows which made some empty space for me to install Xubuntu.
- Installed Xubuntu in that newly created space.

As for the question of which Ubuntu to install: According to my experience, Xubuntu or Lubuntu is much much much better than Unity/Gnome 3 and i gave up on both of them after using them for couple of months. I then moved to Xubuntu and loved the simplicity and the "lightness" of the XFCE/LXDE graphical environments that u get with them. 

And installing xubuntu-desktop over Ubuntu will not effect much as i've tried that myself and eventually had to go back to Unity so do a fresh installation of either Xubuntu or Lubuntu.

HTH

---

### Post by subehsharma on 2011-11-10
Good article on partition shrinking:

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by bob12564 on 2011-11-11
Thanks for the replies.  I think I've decided that xubuntu is the way to go.  I just don't feel comfortable that gnome-fallback will be supported in the future while XFCE is an active project and has a long track record.  The tutorial on the Windows partitioning tool will be useful.

I'm still reviewing the partition issue.  Microsoft changed a few things in Windows 7.  Unlike XP, Windows 7 comes in 2 primary partitions:  "System" is the first and "Windows" is the second.  Unlike earlier versions, the boot sector is in the Windows (second) partition and not at the beginning of the drive.  Using Gpartad or similar tools will corrupt the boot sector according to my reading.  All of the extra space is in the second partition.

HP, Compaq, and maybe Dell and others also ship with 2 additional primary partitions: "Tools" and "Recovery".  So in order shrink "Windows" to find space for unbuntu, you first have to deal with Tools and Recovery.  Ideally you'd want to temporarily delete them, then shrink Windows, and then re-establish Tools and Recovery which would then leave the unallocated space at the end in a logical or extended partition.  Now Windows is happy (no more than 4 primary partitions) and ubuntu has all the space it needs.

I read that many people simply delete the Recovery partition.  If Windows needs to be reloaded, the recovery tool will simple reformat the drive and return it to the state it was in when you bought the computer.  Ubuntu gets wiped out in the process.  So maybe it's not worth saving.  I now see why many people end up buying a standalone copy of Windows and use it for reloading or repairing Windows.  You can control the partitions and load Windows as you see fit.  Life was simpler when the manufacturers gave you the Windows CD so that you could reload from that.

---

### Post by haresear on 2011-11-11
I can sympathize -- it is really annoying when MS and HP conspire to use up all 4 available primary partitions so that you can't create a new partition of your own. If you have a DVD/CD RW drive, you could create a full set of Recovery DVDs and then delete the Recovery partition. In my Toshiba laptop the full set of Recovery media will (supposedly) duplicate the function of the Recovery partition -- not sure if this is true for HP.

---

