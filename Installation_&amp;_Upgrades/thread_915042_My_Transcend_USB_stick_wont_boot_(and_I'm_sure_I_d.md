---
title: "My Transcend USB stick wont boot (and I'm sure I did it right)"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by mujambee on 2008-09-09
Hi all,

 I have a 2Gb LG USB Drive ([http://www.lge.com/products/model/detail/ub2gvms01.jhtml]("http://http//www.lge.com/products/model/detail/ub2gvms01.jhtml")) and a 8Gb Transcend JF V60 ([http://www.transcend-uk.com/Products/ModDetail.asp?ModNo=126&LangNo=0](http://www.transcend-uk.com/Products/ModDetail.asp?ModNo=126&LangNo=0)). I've been using the LG drive for a while, installed several times and never had a problem (always used the pendrivelinux.com method).

Now I'm trying to run from my 8Gb and can't do it, none of my computers will even try to boot from it: when I plug it in and power on, it goes directly to the hard drive, ignoring the USB stick. If I plug the 2Gb and boot the same computer, it boots from the USB.

I've used a similar procedure on both drives. Only difference, only for the first time , whas that I added a 1Gb partition to use from Windows. That time I plugged in the 2Gb to move some files from one to the other and forgot to unplug. After reboot it started on the 8Gb drive, but it was the only time it did.

After a second reboot (unplugging the 2Gb), it wasn't able to boot. I installed lilo again (just in case) but to no avail.

A second try following pendrivelinux.com to the letter gave no better result, still wont boot.

Next I used the install option on the LiveCD on the pen drive. No way.

A last and desperate try was to dd from my 2Gb to my 8Gb. This way I get exactly the same boot record from both drives, but nothing happens. Before doing this I suspected it might not work, but I can read both my partitions and see the remaining 6Gb as unpartitioned space.

Now my question is: Is there anything that I'm leaving out? I mean, I believe that to boot up a system you start in the MBR, and that the bios is responsible for that, but having the same MBR in two different drives gives different results.

---

### Post by mrsteveman1 on 2008-09-09
I've seen some USB drives refuse to boot for some reason, even a 60gb hard drive.

I'm not as familiar with Lilo but some bootloaders leave a simple program in the MBR code section that reads which partition is active and jumps to it to continue the bootloader process. 

So see if the partition is active and also, try using syslinux or extlinux.

---

