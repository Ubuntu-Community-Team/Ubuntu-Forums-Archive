---
title: "I made a /boot partition, and it's too small. Remove, resize..?"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by Andersson on 2010-03-13
I made a /boot partition during install, and I made it ~64 MB. That seems to be an old fashioned way of partitioning and too little space for upgrading the kernel. And here I was trying to be smart.

I've been thinking of two ways to solve this. But I want to be sure not to end up with an unbootable system, so I would like some feedback first.

Alternative 1.

[LIST=1]
[*]Remount /boot partition somewhere else and copy the contents to /boot (on sda3, the root partition.)
[*]Give sda3 the bootable flag.
[*]Update GRUB.
[/LIST]
Alternative 2.

[LIST=1]
[*]Resize the filesystem on sda3, making it 300 MB smaller.
[*]Resize sda3 partition, making it 300 MB smaller.
[*]Make a new bootable partition sda4 in the free space.
[*]Make sda4 the new boot partition. Move everything on sda1 to sda4, update fstab and GRUB.
[/LIST]
Alternative 1 seems the best solution. But I am unsure how grub works. Do I need to reinstall it, will that overwrite the files I copied from sda1? Is an update enough?

How about this, will that do it or am I missing something?

mkdir /mnt/oldboot
umount /boot
mount /dev/sda1 /mnt/oldboot
cp -r /mnt/oldboot/* /boot/
(remove /boot entry in /etc/fstab)
fdisk /dev/sda (and add bootable flag to sda3)
grub-install

```
user@computer:~$ df -h
Filsystem            Storlek Anvnt Tillg Anv% Monterat på
/dev/sda3              22G  9,6G   11G  48% /
udev                 1007M  288K 1007M   1% /dev
none                 1007M  220K 1007M   1% /dev/shm
none                 1007M  192K 1007M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda1              59M   43M   14M  77% /boot
/dev/sda5             207G  149G   47G  77% /home/user/Storage
``````
user@computer:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 250,1 GB, 250059350016 byte
255 huvuden, 63 sektorer/spår, 30401 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0xc448c448

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1           8       64228+  83  Linux
/dev/sda2            2812       30401   221616675    f  W95 Utökad (LBA)
/dev/sda3               9        2811    22515097+  83  Linux
/dev/sda5            3061       30401   219616551    7  HPFS/NTFS
/dev/sda6            2812        3060     2000029+  82  (SWAP)
``````
user@computer:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=d27ada86-7811-437f-b606-e7537c0bf06c /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=aca1aab4-3a27-42be-af3b-500d639883ee /boot           ext2    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=a978bfe3-293d-4271-a2df-128c89b60021 none            swap    sw              0       0
# used to be E: in windows, now ext3
UUID=ee195dec-571c-404a-a01f-d93e280fd067 /home/user/Storage    ext3    defaults    0    2

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by oldfred on 2010-03-13
I moved /boot around without any issue. First I moved it to its own partition for one version I am booting but decided I did not like that and moved it back but made the partition a grub (only) partition. Where ever grub and the boot files are and the entries in fstab must match. Depending on the version of grub the instructions to reinstall grub vary. I would make sure I have a liveCD to boot just in case the reinstall of grub does not work.

Boot flag is only required by windows and some BIOS need one partition with the flag if you do not have it on a windows partition. Linux does not use the flag.

---

