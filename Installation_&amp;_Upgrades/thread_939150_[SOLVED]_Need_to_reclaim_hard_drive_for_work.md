---
title: "[SOLVED] Need to reclaim hard drive for work"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by xj0hnx on 2008-10-05
Hello.

I a while back I installed Ubuntu on one of my hard drives, but unfortunately I have to remove it, and reclaim the hard drive for use with Vista for work.

My system is set up as follows...

C:\ 150gb Window Vista x64
D:\ 80gb Windows XP (Wifes OS)
E:\? 80gb with Ubuntu

Before I installed Ubuntu I could see this hard drive from Vista, and XP, but now it is hidden from both.

When I boot up, it goes to GRUB, and then gives me the selections for Linux, or Vistas bootloader, if I select Vistas bootloader it goes to that, and from there I can select XP or Vista. So I need to remove GRUB, and have it load straight into the Vista bootloader, but I need access to that drive. I would guess if I could see that drive in Windows I could simply reformat it, and then use something like EasyBCD to fix the bootloader, problem is I can't see the drive anywhere except in Ubuntu.

When I go to Computer Managment in System Administration I believe I can see the drive there. It displays

Disk 0 (pretty sure this is my D:\ drive with XP)
  basic
  74.56 GB
  online

Disk 1 (pretty sure this is the Ubuntu disk as it has a 3.08GB partition)
  Basic
  74.53 GB
  online

Disk 2 (this is my Vista disk)
  Basic
  139.73 GB
  online

and then my USB externals.

Any more info needed to help me out? Thank you in advance.

John

---

### Post by xj0hnx on 2008-10-05
All right, well, I'll answer this myself so maybe it can help someone down the road in a similar situation.

First you need a Windows Vista recovery disc. If you don't have one you can download one, and then burn the .iso file to a CD...

[http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc](http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc)

It is a .torrent, so you are going to need a torrent client, either uTorrent, Azureus, other other. Once you have it downloaded you can burn with your favorite burning utility, Nero, Ashampoo Burning Studio, etc...

Once you have your disc burned, stick it in your drive, and reboot your computer, and boot from the CD. Go through the setup (looks like you are about to install Vista), and then select "**Repair Computer**". It will look for operating systems, and it will find your Vista installation, select it and click next, tehn select Command Prompt and at the prompt enter "**Bootrec.exe/FixMbr**" without the quotations and press enter. It will take all of a split second to finish, then reboot the computer, you will be greeted by the Vista bootloader.

Once back in Vista click "**Start > Control Panel > Administration Tools > Computer Management > Storage**" and find the drive you have Linux installed on. Chances are it is going to be listed with no drive letter, apparently Vista can't comprehend Linux file system or something. Right click on the drive, which should be broken up into two, maybe three different partitions, and "**delete**" the volumes that make up the complete Linux disk/partition, and you'll be left with one partition, then simply right click on it and then Format it following instructions for the drive letter, file system, etc...

Hope this helps someone.

---

