---
title: "cannot boot ubuntu along with windows8"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by sakol98 on 2013-02-07
I have a windows8 desktop. core I5 1Tb harrddisk and 16 Gb Ram. I try ton install ubuntu 12.10. It seem smooth on installation. But when I re-start no boot option on the screen. The computer always start winth Windows8.

I search in google and found a recommend to re-install grub. I boot with live USB drive and try to install grub.

> sudo grub-install /dev/sdathe result is

> Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.
I search in google with the error message but still not found the solution.

some one tell me That we cannot install another OS on windows8 system ??

Thank for every suggestion

---

### Post by furything on 2013-02-07
How did you reinstall grub?

Was it like this
```
mkdir /mnt/root
sudo mount -t ext4 /dev/sdaXX /mnt/root 
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
grub-install /dev/sda
update-grub
```Replace sdaXX with your linux partition probably of ext4 format if not then change to what you have used so for ext3 replace ext4 with ext3

Using the live usb run up gparted to check where linux is installed to get the correct partition before trying to fix it

---

### Post by sakol98 on 2013-02-07
Thanks for your reply.
I don't know exactly how to install grub. I only type
> sudo grub-install /dev/sda
and get the error message above

now I follow your suggestion but get error after the :grub-install /dev/sda:
as I copy it below
> ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x114123e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976762879   488380416    7  HPFS/NTFS/exFAT
/dev/sda2       976762880  1465142271   244189696    7  HPFS/NTFS/exFAT
/dev/sda3      1465143294  1953523711   244190209    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5      1920227328  1953523711    16648192   82  Linux swap / Solaris
/dev/sda6      1465143296  1920227327   227542016   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4141 MB, 4141875200 bytes
128 heads, 62 sectors/track, 1019 cylinders, total 8089600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001ea0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     8086783     4043361    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda6 /mnt/root 
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/root/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/root/dev
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
root@ubuntu:/# grub-install /dev/sda
source_dir doesn't exist. Please specify --target or --directory


what should I do next ?

---

### Post by ksprasad on 2013-02-07
Hi,
 
The issue might be due to UEFI. Try the solution given in this link:
 
[http://askubuntu.com/questions/225028/dual-boot-windows-8-with-ubuntu-12-10/225031#225031](http://askubuntu.com/questions/225028/dual-boot-windows-8-with-ubuntu-12-10/225031#225031)
 
Regards,
Ksprasad

---

### Post by sakol98 on 2013-02-07
After read and try suggestion on [http://askubuntu.com/questions/22502.../225031#225031](http://askubuntu.com/questions/22502.../225031#225031)

I still cannot find  "Ubuntu listed" in boot tab on msconfig.
And when type "uefi" in start screen it cannot not found the uefi.

So I think it is not my case.

---

### Post by oldfred on 2013-02-07
Best to see your exact configuration. Also is system an Ultrabook?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

