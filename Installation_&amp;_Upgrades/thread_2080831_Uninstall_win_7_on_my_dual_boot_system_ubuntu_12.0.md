---
title: "Uninstall win 7 on my dual boot system ubuntu 12.04"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by astraone on 2012-11-05
Hello, 


I have win 7 on my dual boot system along with  ubuntu 12.04 the ssd drive is partioned,please could someone advise /link me to thread on how to uninstall win 7 from my system


I am fairly new to Linux but like it a lot


David

---

### Post by Al Stat on 2012-11-05
Is there only one hardware data storage device (your SSD)? Or there are other HDD/SSD?

You need to search for:

1)  How to install Grub on disk (hardware one) containing your Linux  installation. Probably Grub is already on it.  [http://askubuntu.com/questions/30341/how-to-know-the-partition-where-grub-is-installed](http://askubuntu.com/questions/30341/how-to-know-the-partition-where-grub-is-installed)
If it is not - then you need to use "grub-install" command to install Grub on disk (hardware one) containing your Linux.

2) How to with GParted delete partition with unwanted operating system.

3) How to expand existent partitions and use space to be freed.

4) Launch "sudo update-grub".

Pay attention:

On what partition is located "/boot/grub/grub.cfg".

On  file "/etc/fstab". In case of partitions resise may be changed  partition's UUIDs. Use separately Gparted (or "sudo fdisk -l") and  command "ls -l /dev/disk/*" to investigate partition's UUIDs. Correct  values in "/etc/fstab".

Good tool is [http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start)
It allows you to boot from independent data storage (CD, flash drive, etc.) and organise your computer's internal data storages.

Before  you start - do backup of any valuable data. Create this backup on  external storages, on storages NOT to be used or accessed while you will  be working on your computer.

---

### Post by varunendra on 2012-11-07
Hi astraone, Welcome to the forums !
> **astraone said:**
> I have win 7 on my dual boot system along with  ubuntu 12.04 the ssd drive is partioned,please could someone advise /link me to thread on how to uninstall win 7 from my system

Are you positive that it is a 'proper' dual boot and not a wubi installation ? (in a proper dual boot you are presented with the purple grub menu with options to boot linux...., linux.... (recovery mode), memtest, windows etc.)

If so, all you need to just delete or format the partition that holds windows (plus its separate 'boot' partition if it has one).

You can use the included 'Disk utility' tool to do that, or install and use Gparted to do it more elegantly. Gparted is already available on the live cd, but you have to be careful if running from live cd. Running it from the installed Ubuntu is safer.

That said, why do you want to do this ? You said yourself that "I am fairly new to Linux". As such, I won't suggest to remove windows until you get quite familiar and comfortable with Ubuntu. In any case, You should consider creating a set of 'Backup DVDs' using 'Backup and recovery' option in windows' control panel, in case you ever wish to restore windows back.

---

