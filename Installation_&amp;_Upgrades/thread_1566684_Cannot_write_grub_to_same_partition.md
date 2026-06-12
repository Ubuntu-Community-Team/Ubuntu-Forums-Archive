---
title: "Cannot write grub to same partition"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by njmiano on 2010-09-02
Hi everyone,
I am having a problem installing Ubuntu 10.04 in a multi-boot system.

I use GAG as a bootloader, and here is how I have always done it in the past with Ubuntu... During installation, at the last menu I would click advanced, choose to install bootloader and write it to the same partition as the OS. This has been a way that I can add and remove OS' without any issue. This works with Ubuntu 9.10, Fedora 13, and most other OS'. (except MS which is a whole other issue)

However, with the installer on the x86 version of Ubuntu 10.04.1, If I select the same partition to install the boot loader and the OS, the "OK" box is greyed out. The same if I uncheck the bootloader option. This being the case, I cannot continue with the installation using these settings.

I have tried setting the partitions as both "primary" and "extended". 

Is this a bug, a security measure, or just the way things are heading? I have tried burning a different Live CD and varifying the checksum just in case. Same situation.

Does anyone know a workaround? Like I said, I add and remove OS' fairly often, so I do not want to mess with any other OS' partition.

Thanks.

PS I just remembered that I have used this method with success on the 64-bit version of Ubuntu 10.04

---

### Post by njmiano on 2010-09-03
I figured out a solution.

All I had to do was use Gparted from inside the Live CD enviroment and create a small (100MB) partition before the Ubuntu partition to install grub on. Then I just pointed GAG to that partition.

Hope this helps someone.

---

