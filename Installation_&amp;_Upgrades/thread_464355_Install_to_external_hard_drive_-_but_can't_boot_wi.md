---
title: "Install to external hard drive - but can't boot with it..."
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by floke on 2007-06-04
'Successfully' installed Feisty to an external hard drive using the alternative installer (read that it had better configuration options). I set up an ext3 partition alongside a FAT32, and created a swap file inside an extended partition. The partitions were formatted (I also set the ext3 partition with a boot flag, if that means anything) and the install has gone to the right place (can check all the system files if I plug the drive in but don't try to boot from it), and installed grub onto the external drive too. Grub menu.lst seems to point to the right place (hd1,1) but when I try to boot from the drive I get a grub error 17; can't mount partition. I am also unable to boot to any of my partitions on my internal drive, even though they are listed in the external grub, and even though they point to the same places as the grub entries on my internal drive.

Does anyone know what to do?

---

### Post by confused57 on 2007-06-04
> **Steve.K said:**
> 'Successfully' installed Feisty to an external hard drive using the alternative installer (read that it had better configuration options). I set up an ext3 partition alongside a FAT32, and created a swap file inside an extended partition. The partitions were formatted (I also set the ext3 partition with a boot flag, if that means anything) and the install has gone to the right place (can check all the system files if I plug the drive in but don't try to boot from it), and installed grub onto the external drive too. Grub menu.lst seems to point to the right place (hd1,1) but when I try to boot from the drive I get a grub error 17; can't mount partition. I am also unable to boot to any of my partitions on my internal drive, even though they are listed in the external grub, and even though they point to the same places as the grub entries on my internal drive.

Does anyone know what to do?
Boot to your external drive, in your grub boot menu highlight your Ubuntu entry, press "e", then change root from (hd1,x) to (hd0,x), then press "b" to boot...this change is temporary, but should boot your Ubuntu.

You Window's entry in grub would need to be root (hd1,x), and contain mapping commands:
map (hd0) (hd1)
map (hd1) (hd0)

If you can boot into Ubuntu on your external drive, it's no problem making the changes permanent.  Do you happen to have a Linux distro installed on your internal hard drive?

---

### Post by floke on 2007-06-04
Thanks for the help; I actually read some of your posts on this issue in other threads, and have found the solution.

For some reason, you would think that sdb2 (sdb1 being FAT32 partition and sdb5 being swap) would be listed in grub as (hd1,1) - which is what it was indeed listed as in the menu.lst. However, I read in another thread that someone with the exact same issue solved it by changing the entry to **(hd1,0)** - which makes no sense - but anyway, it worked :p!

So everything is now peachy (or rather, feisty - actually not so feisty, since I have locked the kernel on the USB install so that it can't get borked by silly updates).

Many thanks again for the reply.

---

