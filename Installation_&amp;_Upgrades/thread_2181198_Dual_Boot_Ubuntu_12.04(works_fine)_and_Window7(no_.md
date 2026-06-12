---
title: "Dual Boot Ubuntu 12.04(works fine) and Window7(no boot)"
date: 2013-10-16
forum: Installation &amp; Upgrades
---

### Post by Tammy_Carter on 2013-10-16
Hi Guys,

Oops! I believe the root of my problems is that I overwrote the Windows 7 system recover partition with the  Ubuntu boot partition. (maybe?)
When I select the Windows 7 (loader) (on /dev/sda1) from the GRUB menu, it flashes black and then it just returns back to the main GRUB menu.

The disk partitions:
/dev/sda1 ntfs       System Reserved  100.00 MiB 33.59 MiB  66.41 MiB boot
/dev/sda2 ntfs       Window 7            109.86 GiB 12.38 GiB   97.48 GiB
/dev/sda3 ext4 /     Ubuntu               121.55 GiB  5.74 GiB  115.81 GiB
/dev/sda4 ntfs        Storage              700.00 GiB  2.10 GiB  697.90GiB                    


os-prober yields -> /dev/sda1: Window 7 (loader); Windows:chain


grub boot line:

setparams "Windows 7 (loader) (on /dev/sda1)

insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)
search --no-floppy --fsuuid --set=root A0C65330C6530646
chainloader +1

If I look at the contents of /dev/sda1:
I see a BOOT directory, bootmgr, BOOTSECT.BAK, and an empty System Volume Information
In the boot directory, is BCD(size 28672), a BCD.log, a BOOTSTAT.DATfile (None are human readable). There is also a memtest.exe and alot a zero size files with names like zH-TW

Please save me from having to rebuild the machine.

Thanks,

---

### Post by oldfred on 2013-10-16
This will show a little more detail. :)

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Tammy_Carter on 2013-10-18
Boot-Repair was just what  I needed. Thanks alot

---

