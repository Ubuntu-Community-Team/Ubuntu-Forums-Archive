---
title: "How to install another version of ubuntu on same disc drive as xubuntu ?"
date: 2019-05-30
forum: Installation &amp; Upgrades
---

### Post by radu19842 on 2019-05-30
[FONT=arial]I currently run Xubuntu 18.04 Bionic Beaver and i would like to install another ubuntu version on same hard drive , i tried and somewhere along the installation proces it asks me what to do , there is a simple choice to just install ubuntu/kubuntu,etc along side my xubuntu , is this a correct way to install it , can something nasty come out or i should do it in another manner ? Thank you , sorry to bother you but i'm starting to enjoy ubuntu more and more ... bu still i am a beginner ! :D 
All the best ! :)[/FONT]

---

### Post by Rubi1200 on 2019-05-30
Before offering advice we need some more information.

Post the output of the following commands please:

```
sudo fdisk -l
```

```
df -Th
```

Thanks.

(and yes it is possible)

---

### Post by radu19842 on 2019-05-31
**Rubi1200 **Thank you so much and have a great weekend ! :)
[COLOR=#000000]
> [B]sudo fdisk -l
[/B]
[/COLOR]> Disk /dev/loop0: 88,4 MiB, 92733440 bytes, 181120 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 150,2 MiB, 157536256 bytes, 307688 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 129,5 MiB, 135823360 bytes, 265280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 21,4 MiB, 22388736 bytes, 43728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 105,5 MiB, 110608384 bytes, 216032 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 50,7 MiB, 53182464 bytes, 103872 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 238,5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 5B70C9BD-1AD7-4632-A527-5A372FB1E854


Device       Start       End   Sectors  Size Type
/dev/sda1     2048   1050623   1048576  512M EFI System
/dev/sda2  1050624 500117503 499066880  238G Linux filesystem
barbos@barbos-X541NA:~$ 


> [B]df -Th
[/B]
> 
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1,9G     0  1,9G   0% /dev
tmpfs          tmpfs     381M  1,4M  380M   1% /run
/dev/sda2      ext4      234G  9,4G  213G   5% /
tmpfs          tmpfs     1,9G   28M  1,9G   2% /dev/shm
tmpfs          tmpfs     5,0M  4,0K  5,0M   1% /run/lock
tmpfs          tmpfs     1,9G     0  1,9G   0% /sys/fs/cgroup
/dev/loop0     squashfs   89M   89M     0 100% /snap/core/6964
/dev/loop1     squashfs  151M  151M     0 100% /snap/opera/38
/dev/loop2     squashfs  130M  130M     0 100% /snap/boxy-svg/6
/dev/loop3     squashfs   22M   22M     0 100% /snap/chromium-ffmpeg/13
/dev/sda1      vfat      511M  6,1M  505M   2% /boot/efi
tmpfs          tmpfs     381M   24K  381M   1% /run/user/1000
/dev/loop4     squashfs  106M  106M     0 100% /snap/shotcut/45
/dev/loop5     squashfs   51M   51M     0 100% /snap/p7zip-desktop/163


---

### Post by Dennis N on 2019-05-31
```
Disk /dev/sda: 238,5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 5B70C9BD-1AD7-4632-A527-5A372FB1E854


Device Start End Sectors Size Type
/dev/sda1 2048 1050623 1048576 512M EFI System
/dev/sda2 1050624 500117503 499066880 238G Linux filesystem
barbos@barbos-X541NA:~$ 
```

Your Xubuntu partition is using all the available space, so it will have to be reduced to allow another partition for the new install. Try the 'install alongside' option, and a dialog should ask by how much to shrink sda2. Specify how much to shrink it, and then the installer can go to work, get your user information and finish the install.

---

