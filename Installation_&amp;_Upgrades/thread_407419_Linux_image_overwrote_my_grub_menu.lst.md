---
title: "Linux image overwrote my grub menu.lst"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by sammydee on 2007-04-12
Hi. I'm not sure if this is in the right forum (mods please move it to the appropriate sub board if there is one).

This isn't really a request for help because I already fixed it, I suppose it is more of a bug report. I downloaded the latest kernel image for Ubuntu dapper (not sure exactly which version but it was the latest and this was yesterday) via automatic updates. After restarting my system I was greeted with a grub error message stating that it could not find hd(1,0). This is because there ISN'T an hd(1,0) on my system.

A few months ago there was and I booted from it, but there isn't anymore and I changed my menu.lst so that it booted from hd(0,1) instead. Somehow the kernel install must have caused the grub menu.lst to have reverted to it's previous settings. I certainly did not do it and I can't think of any other triggers that may have caused it. It's fixed now, but I wonder if anybody else had the same problem?

Sam

---

### Post by kidders on 2007-04-12
Hi there,

> **sammydee said:**
> I changed my menu.lst so that it booted from hd(0,1) instead.

Did you remember to alter the commented **groot** directive in /boot/grub/menu.lst?

---

### Post by User_Program on 2007-04-12
> **sammydee said:**
> Hi. I'm not sure if this is in the right forum (mods please move it to the appropriate sub board if there is one).

This isn't really a request for help because I already fixed it, I suppose it is more of a bug report. I downloaded the latest kernel image for Ubuntu dapper (not sure exactly which version but it was the latest and this was yesterday) via automatic updates. After restarting my system I was greeted with a grub error message stating that it could not find hd(1,0). This is because there ISN'T an hd(1,0) on my system.

A few months ago there was and I booted from it, but there isn't anymore and I changed my menu.lst so that it booted from hd(0,1) instead. Somehow the kernel install must have caused the grub menu.lst to have reverted to it's previous settings. I certainly did not do it and I can't think of any other triggers that may have caused it. It's fixed now, but I wonder if anybody else had the same problem?

Sam


Yep same thing happened!  I fixed it also but man, I can only imagine what a new user to Linux (ubuntu) thinks when he runs into this problem after an update.  Even if he/she has made changes to the menu list before.  I've already seen many similar post in the last day that probably relate directly to this.  

Surely there is a better way to update the menu list.  I wonder if there are any scripts out there that scan HD's and finds the ones that has Linux on them?  This could be attached when ever there is a kernel update/upgrade.

---

### Post by kidders on 2007-04-12
> **User_Program said:**
> I wonder if there are any scripts out there that scan HD's and finds the ones that has Linux on them?  This could be attached when ever there is a kernel update/upgrade.
Unfortunately, things aren't that straightforward. :-( As a simple example, it would be wrong to assume that a disk should have a bootloader installed on it just because there is a linux system in one of its partitions. More often than not, people tend to put their bootloader on their primary boot device which, in multi-boot environments involving Microsoft products, tends to be the one *without* Linux on it.

In multi-boot environments that *don't* involve Microsoft, there would be no way to know Ubuntu was getting basic things like kernel parameters right for operating systems other than itself. More generally, it would also be wrong to assume that the hard disk device order apparent to the installer would be the same as that detected by the bootloader itself.

Essentially, finding a way to correctly guess a user's intentions non-interactively would be non-trivial. On the other hand, it is probably fair to assume that a user with knowledge advanced enough to be able to move disk partitions around, or reorder hard disks, can keep track of bootloader configuration hints like "groot". The simple approach just seems to be more reliable ... something which is important when it comes to bootloaders.

---

### Post by mcduck on 2007-04-12
If you change settings in menu.lst but don't also change the default settings in the same file, or add new things between lines "### BEGIN AUTOMAGIC KERNELS LIST" and "### END DEBIAN AUTOMAGIC KERNELS LIST", then yes, you will loose your settings when next kernel update recreates the menu.lst file. It's not a bug, and if you read through the file it's also very clearly explained in there..

As long as you edit the default options, and add your own boot entries outside the automagick area you'll have no problems.

---

