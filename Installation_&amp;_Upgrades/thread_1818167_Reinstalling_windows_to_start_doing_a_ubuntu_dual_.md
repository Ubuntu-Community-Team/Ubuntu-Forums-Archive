---
title: "Reinstalling windows to start doing a ubuntu dual boot"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by ShadowHunter332 on 2011-08-04
Hi, about six months ago i switched from windows 7 to ubuntu. although since i switched i have figured out a few errors about doing the switch. so therefore i would like to try a dual boot. but, my hard drive can no longer support the ntfs file format to install windows. How do i fix this? and from there how do i execute a dual boot?

---

### Post by Blasphemist on 2011-08-04
Please download and run this script to give us information on your disk configuration now. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It may be a challenge getting windows re-installed without considerable partition changes. Do you have your important files backed up? If needed can the drive be wiped and both windows and Ubuntu re-installed?

---

### Post by flemur13013 on 2011-08-04
It's best and far easier to install windows first, then ubuntu. But you don't have to.

The best and safest way would be to:

- back up your ubuntu install (if you haven't installed much extra software, you can get by with just backingup your /home/yourname directory), then 

- optionally make some partitions from using the ubuntu install CD/DVD and gparted (easy way=let the installers do it in later steps), then 

- install windows (easy way=let it use entire disk), then 

- install ubuntu (easy way=tell it how much space to use "side-by-side" w/windows), then

- repair/replace ubuntu from your backup (but DON'T copy the boot loader stuff! If you do, see the 'fix boot' part below)
(eg copy the saved /home/yourname directory and reinstall extra programs).

To install windows while trying to keep ubuntu installed 

1 - Backup your stuff anyway!

2 - Boot from the ubuntu CD/DVD and use gparted to make some free space on your linux (ext3 or 4) disk. Don't format it. Make it big enough to hold Windows.

3 - Boot from the Windows CD and install it to the unformatted free space you created. This *will* screw up your ubuntu boot.

4 - Fix the boot and make it dual boot: 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
or
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

I'd do the first method if I didn't have much stuff to backup, or if my system wasn't very customized - still had original software, etc, or if I wanted to "clean-up" my ubuntu install to original condition.

I'd do the 2nd method if I had lots of custom software and settings or if I felt lucky.

---

### Post by ShadowHunter332 on 2011-08-04
Thanks, i will try creating a new partition then install windows

---

### Post by oldfred on 2011-08-06
Windows needs a primary (sda1 thru sda4) NTFS partition with the boot flag (active partition in windows) to install into.

---

