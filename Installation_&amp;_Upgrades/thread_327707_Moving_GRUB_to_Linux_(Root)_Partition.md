---
title: "Moving GRUB to Linux (Root) Partition"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by fiestaforever on 2006-12-29
This has been coming up quite a few times lately, but my findings were rather confusing. 

Ubuntu (or Xubuntu, 6.10 Edgy, in my case) installs GRUB into the MBR by default and even the "alternate" CD doesn't seem to make it possible to install it into the root partition instead. 

I want to keep (or reinstall) the bootmanager I have when I install Xubuntu 6.10 on a Thinkpad with 10 partitions (please don't ask why), that has both the root and swap partition as logical drives in the extended partition. ATM it has Vector Linux 4.3 installed with lilo in the root partition. 

In other threads, there was some info about installing (or moving) GRUB with 
grub-install /dev/hda2 (or in my case: grub-install /dev/hda5). 

But on another occasion, it was said that it must be a primary partition you install it to. I have to use a logical drive. Can this be done?

---

### Post by confused57 on 2006-12-29
> **fiestaforever said:**
> This has been coming up quite a few times lately, but my findings were rather confusing. 

Ubuntu (or Xubuntu, 6.10 Edgy, in my case) installs GRUB into the MBR by default and even the "alternate" CD doesn't seem to make it possible to install it into the root partition instead. 

I want to keep (or reinstall) the bootmanager I have when I install Xubuntu 6.10 on a Thinkpad with 10 partitions (please don't ask why), that has both the root and swap partition as logical drives in the extended partition. ATM it has Vector Linux 4.3 installed with lilo in the root partition. 

In other threads, there was some info about installing (or moving) GRUB with 
grub-install /dev/hda2 (or in my case: grub-install /dev/hda5). 

But on another occasion, it was said that it must be a primary partition you install it to. I have to use a logical drive. Can this be done?

If you install with the alternate cd, select "no" when asked to install grub to the mbr, then you are given an option of where to install(/dev/hda5).  On an already installed (X)ubuntu you can install grub to the root partition(or mbr), using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

You can use chainloading(if you're using grub on mbr) to boot Linux, if grub is installed on the root partition of the OS you're wanting to boot.

---

### Post by fiestaforever on 2006-12-30
One of the points in the OP was that the installer did not ask where to install Grub (maybe because it didn't recognize the Windows installation at all, I had to repair menu.lst manually). 

When I installed Xubuntu 6.10 to the second machine (the one with the many partitions), it did ask. 
But when I tried to install Grub to /dev/hda11 (I made a mistake here in the first post, it's not /dev/hda5), it failed. 

Then I started the installer over and changed the filesystem from reiserfs to ext3. 
This time it worked. I now have Grub on the 11th and last partition, a logical drive inside the extended partition, and the original boot manager in the MBR. 

This doesn't make much sense to me, I can't see a reason why the filesystem should be important here.

---

