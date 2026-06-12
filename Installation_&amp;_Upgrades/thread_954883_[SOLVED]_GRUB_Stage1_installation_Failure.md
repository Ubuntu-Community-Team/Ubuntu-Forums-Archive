---
title: "[SOLVED] GRUB Stage1 installation Failure"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by memetichazard on 2008-10-21
The situation is as follows.
The laptop is a Lenovo t400.
The distro is Kubuntu 8.04 (KDE4)
There is a single hard driver, split into 4 partitions.
Vista sits on the first partition. The third is already used.

The first time I installed Ubuntu to the 2nd partition, I did not touch the advanced bootloader settings.
Installation failed at around 95% with 'Error: Grub-install failed'.

After booting in with the CD, I was unable to use any of the methods I found online to fix Grub.

In grub, if I try 'find /boot/grub/stage1', I get a File not Found error (15).
Most telling is perhaps that when I cat stage1, the following line shows up:
'GRUB GeomHard DiskRead Error'

I've also tried reinstalling while telling grub to install to (hd0,1).

Oh, and [this]("https://answers.launchpad.net/ubuntu/+question/7760") post suggests that not having a swap partition may be responsible here for the issues with having a broken stage1. I chose not to use a swap partition. I have read that the 2.6 kernel now supports using a swap file, with no effective difference in performance as compared to the swap partition.

So, how do I install Ubuntu? Can I do it without needing a stage1? I don't recall dealing with any stage1s back when I ran gentoo... -_-

I'd like to have grub installed to the 2nd drive partition, and let Vista's bootloader handle everything... but if I have to write grub to the MBR and have it run Vista, that's fine too.

---

### Post by caljohnsmith on 2008-10-21
Try the following solution to get Ubuntu to install without having Grub fail:

[http://ubuntuforums.org/showthread.php?t=893156](http://ubuntuforums.org/showthread.php?t=893156)

Also, if you want to use Vista's boot loader, in the final stage of the Ubuntu installer, click the "advanced" button, and tell Grub to install to /dev/sda2 or (hd0,1) like you tried before; then you can use Vista's boot loader to easily "chain load" or boot Ubuntu. A really easy way to modify Vista's boot menu is with "EasyBCD":

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Let me know how it goes. :)

---

### Post by memetichazard on 2008-10-21
Making it ext2 worked - grub installed. I also already had Vista setup to be able to boot into the Ubuntu partition. However, it didn't boot properly into grub. I used the LiveCD to get in and try to fix it. The first thing I did was to use 'sudo tune2fs -j /dev/sdXY' - it told me that /dev/sda2 already had a journal.

Then I tried to mount it and failed.

Then I tried to fsck it and... well, then I tried to fsck -y it.

And now I'm just going to try reinstalling it.

Also, I've discovered that Vista's bootloader won't kick in if Vista is hibernating. So, I guess I'll try it again and let it write into the MBR.

Edit: Having it write to the MBR lets Ubuntu boot up just fine, and it even autodetected the Vista bootloader. Nice :D

Next step, colinux!

---

