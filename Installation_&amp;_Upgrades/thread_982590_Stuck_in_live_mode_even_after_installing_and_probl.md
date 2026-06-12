---
title: "Stuck in live mode even after installing and problems with GRUB"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by ZZQQ on 2008-11-14
So I've been running Ubuntu these past few months and everything has been fine.  After getting more comfortable with linux in general I decided that I wanted to try out both xfce and KDE.  Installing Xubuntu went fine and I tried it out for a couple of days and decided it was not for me.  So then I decided to try out Kubuntu.  Everything installed fine the first time but somehow the partition it installed to was accidentally set to fat32.  I decided to reinstall Kubuntu this time with ext3 and this is when all the problems started.

After going through the installation, the computer does not restart instead I am left in the Live User session mode (Similar to this thread: [http://answers.launchpad.net/ubuntu/+question/47389](http://answers.launchpad.net/ubuntu/+question/47389)).  I have tried installing and setting the bootloader to sda instead of hd0 as mentioned in that thread but it does not work for me.  If I try to restart without the CD, Grub no longer operates and gives me an error 15.  No matter how many times I try to reinstall it doesn't seem to actually do anything different and it just sends me to live CD mode afterward.  And restarting without the CD simply leads to the grub error 15 even after many reinstallations.

I know it's not a CD problem because I have successfully installed with these same CDs on the same computer with no problems until now.  I am running a custom built laptop with a 80gb SATA harddrive.  The partition setup I had before (when everything was working fine) consisted of 5gb partition for Windows XP, 5gb partition for the root directory of linux and the remaining 70gb was a shared ext3 partition (where I put /home).  Now that grub has stopped working I can't even get back into my windows partition.

---

