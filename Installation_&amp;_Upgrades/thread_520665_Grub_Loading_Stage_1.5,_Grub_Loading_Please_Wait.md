---
title: "Grub Loading Stage 1.5, Grub Loading Please Wait"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by MrObvious on 2007-08-08
I have a problem with Grub taking about 15-25 seconds to load where it says the error in the subject. Then I can choose to boot Winblows or Linux with two different kernels or memtest. I've tried reinstalling Grub with sudo 0grub-install /dev/hda. Any ideas?

Also, is it supposed to still use the Winblows boot loader after I choose Winblows in the Grub loader? Should I just find a way to switch to Lilo?

Setup: 
MSI KT6V
2400+ AXP T-bred
512 MB (2x256) RAM
2 IDE HDs
2 Optical IDE drives
1 IDE Floppy
2 XP installs on the Primary Master
1 Ubuntu 7.04 install on the Primary Slave
(Not 100% sure) Jumpers set to CS.

---

### Post by logos34 on 2007-08-08
not sure about the grub delay but this

> 2 XP installs on the Primary Master

is why the windows loader appears (two bootable XP's).  In a windows explorer address bar type

C: \boot.ini

and change the timeout to 0.  You won't see it again.

---

### Post by jnorthr on 2007-08-08
Sorry but don't quite see your problem. The supergrub menu will always appear first allowing you to choose which operating system you wish to run. Unless you completely reinstall ubuntu and/or supergrub, it will stay like that.

---

### Post by MrObvious on 2007-08-08
Okay. I guess it's normal then. But I would like to find the issue for my problem. Thanks for the reply though logos34!

As far as jnorthr, I don't usually use SuperGrub. I just use the plain Grub. It's not a problem with the CD, but Grub itself on my hard drive.

---

### Post by MrObvious on 2007-08-09
Bump.:popcorn:

---

### Post by MrObvious on 2007-08-10
Okay I may have finally figured out my problem. Apparently it has to do with the fact that I had my Master with two NTFS partitions that Grub can't write to on it. That's where the MBR was pointing to, and it was not liking it. So I switched around my cable so the Maxtor with Linux is in front, reinstalled Linux, and things seem peachy (outside of having 2 Linux installs which I intend to fix soon).

---

