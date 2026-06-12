---
title: "Cannot load Ubuntu after Install"
date: 2015-10-03
forum: Installation &amp; Upgrades
---

### Post by nicolas45 on 2015-10-03
Hello, here is my problem:

I am running windows 10 and I decide to install Ubuntu 15.04. I downloaded the iso, extracted it on my usb key and booted from the usb.
I then proceeded to install Ubuntu, it asked me to choose the size I wanted to allocate to it (I used the easy option, installing it alongside windows boot or wtv) gave it 200GB out of my 1TB drive and then he installed himself.
When he rebooted, I could not find ubuntu in the boot option but when I boot from the usb again, it ask me if I want to reinstall Ubuntu so it is apparently intalled.
How can i boot from ubuntu? I spent hours trying to find a fix, im going crazy...

Thank you

---

### Post by yancek on 2015-10-03
Is your windows 10 installed using UEFI?  Did you also install Ubuntu using UEFI?  You need to do that or one will not boot.  You can get some minimal inforation to post here by booting the Ubuntu flash drive, opening a terminal and running the two commands below to show drive/partition information:

```
sudo fdisk -l
sudo parted -l
```

It's a Lower Case Letter L in both commands.  You might try downloading "boot repair" on the flash drive.  If you do that, make sure you select the option to "Create Bootinfo Summary" rather than trying to repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by nicolas45 on 2015-10-04
My windows is installed using UEFI. I think it is th same for Ubuntu since I havent changed anything. Ill try to post the boot repair summary later

ubuntu@ubuntu:~$ sudo fdisk -l


Disk /dev/loop0: 1 GiB, 1101672448 bytes, 2151704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 3CD114E2-B7C5-4296-B8EF-863D7F0C638E


Device          Start        End    Sectors   Size Type
/dev/sda1        2048    1230847    1228800   600M Windows recovery environment
/dev/sda2     1230848    1845247     614400   300M EFI System
/dev/sda3     1845248    2107391     262144   128M Microsoft reserved
/dev/sda4     2107392 1530989718 1528882327   729G Microsoft basic data
/dev/sda5  1920045056 1920966655     921600   450M Windows recovery environment
/dev/sda6  1920966656 1953523711   32557056  15.5G Windows recovery environment
/dev/sda7  1530990592 1903441919  372451328 177.6G Linux filesystem
/dev/sda8  1903441920 1920045055   16603136   7.9G Linux swap


Partition table entries are not in disk order.
Disk /dev/sdb: 57.9 GiB, 62109253632 bytes, 121307136 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000


Device     Boot Start       End   Sectors  Size Id Type
/dev/sdb1          32 121307135 121307104 57.9G  c W95 FAT32 (LBA)





ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  630MB   629MB   ntfs            Basic data partition          hidden, diag
 2      630MB   945MB   315MB   fat32           EFI system partition          boot, esp
 3      945MB   1079MB  134MB                   Microsoft reserved partition  msftres
 4      1079MB  784GB   783GB   ntfs            Basic data partition          msftdata
 7      784GB   975GB   191GB   ext4
 8      975GB   983GB   8501MB  linux-swap(v1)
 5      983GB   984GB   472MB   ntfs                                          hidden, diag
 6      984GB   1000GB  16.7GB  ntfs            Basic data partition          hidden, diag




Model: SanDisk Ultra (scsi)
Disk /dev/sdb: 62.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  62.1GB  62.1GB  primary  fat32        lba

---

### Post by nicolas45 on 2015-10-04
Here is my bootinfo summary [http://paste.ubuntu.com/12682944/](http://paste.ubuntu.com/12682944/)

---

### Post by oldfred on 2015-10-04
I see Acer.
Every Acer we have seen needs you to create a supervisory password and enable "trust" on the Ubuntu efi boot files.

       Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)

---

### Post by nicolas45 on 2015-10-05
Problem solved, thank you Oldfred.

---

