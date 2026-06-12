---
title: "how do I remove Ubuntu from dual boot system"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by swaggeringcuban on 2011-03-07
I had windows 7 starter, then repartitioned the HDD and installed Ubuntu netbook remix

the partitions are in this order

Ubuntu -> System -> Data partition -> Windows 7

I'm having some nagging problems with remix and want to try something else.
Can I just destroy the Ubuntu partition or will it stop windows from booting up?  I know Windows was there first, but the computer has been booting from the /boot/grub/grub.cfg menu, so when this is gone will it automatically check the windows partition for a boot.ini or whatever?

---

### Post by wilee-nilee on 2011-03-07
So if you remove the Ubuntu you will lose the boot to windows or anything. You can reload the MS bootloader though if you need to, which will just boot windows. One command from a booted recovery for W7 in the command line.
bootrec.exe /fixmbr
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Post a screen shot of the gparted partitioner it is on the live cd or needs to be installed on the Ubuntu install. Personally I want to see exactly what's on the HD.

---

### Post by Dutch70 on 2011-03-07
> **swaggeringcuban said:**
> I had windows 7 starter, then repartitioned the HDD and installed Ubuntu netbook remix

the partitions are in this order

Ubuntu -> System -> Data partition -> Windows 7

**I'm having some nagging problems with remix and want to try something else.**
Can I just destroy the Ubuntu partition or will it stop windows from booting up?  I know Windows was there first, but the computer has been booting from the /boot/grub/grub.cfg menu, so when this is gone will it automatically check the windows partition for a boot.ini or whatever?

If your wanting to try another Linux distro, you should be able to just install over top of it & keep Grub.

---

### Post by swaggeringcuban on 2011-03-08
[IMG]http://img848.imageshack.us/img848/6278/screenshot1c.png[/IMG]

here is my gparted screenshot, windows is on sda6.  My netbook didn't come with a recovery CD is that the only way to recover the boot sector?

I guess I could install something over Ubuntu remix but I'd rather be able to just start from a clean slate

---

### Post by Mark Phelps on 2011-03-08
> **swaggeringcuban said:**
> My netbook didn't come with a recovery CD is that the only way to recover the boot sector?

Wilee-nilee gave you a link to a site where you can download the disk images.  You will then have to burn the one you need to CD.

You can then use that CD to restore the Win7 boot loader.

There is also the feature inside Win7, Backup, to create and burn the same Win7 Repair CD.

---

