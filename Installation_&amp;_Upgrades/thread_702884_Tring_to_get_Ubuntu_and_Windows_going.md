---
title: "Tring to get Ubuntu and Windows going"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by davehamptonusa on 2008-02-20
After somehow corruptimg my BIOS....

I installed Ubuntu without my windows drive attached.  I have:
160 GB Hard Drive as Master on IDE0 (Ubuntu)
60 GB HardDrive as Slave on IDE) (Windows)
a plugged in usb drive about 120G

Here's my fdisk

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    7  HPFS/NTFS

here's my df:
/dev/hdc1            151590628   2482076 141408200   2% /
varrun                 1037484        88   1037396   1% /var/run
varlock                1037484         0   1037484   0% /var/lock
udev                   1037484        92   1037392   1% /dev
devshm                 1037484         0   1037484   0% /dev/shm
lrm                    1037484     34696   1002788   4% /lib/modules/2.6.22-14-generic/volatile
/dev/hdb               4440090   4440090         0 100% /media/cdrom0
/dev/sda1            117218240  54116648  63101592  47% /media/1-Backup Set B

Here's my df **After I mounted the windows drive**
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdc1            151590628   2482104 141408172   2% /
varrun                 1037484        88   1037396   1% /var/run
varlock                1037484         0   1037484   0% /var/lock
udev                   1037484        92   1037392   1% /dev
devshm                 1037484         0   1037484   0% /dev/shm
lrm                    1037484     34696   1002788   4% /lib/modules/2.6.22-14-generic/volatile
/dev/hdb               4440090   4440090         0 100% /media/cdrom0
/dev/sda1            117218240  54116648  63101592  47% /media/1-Backup Set B
/dev/hdd1             58621152  48008456  10612696  82% /media/disk

It kind of looks like Ubuntu is using my usb drive to boot....  I hope not...

Here's my device.map created by ubuntu:
(hd0)	/dev/hdc
(hd1)	/dev/sda

Here's my menu.list.  I added the stuff

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=70c6186e-78a8-402c-9dc4-7c06fada0031 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=70c6186e-78a8-402c-9dc4-7c06fada0031 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

[B]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP
root (hd1,0)
savedefault
makeactive
chainloader +1[/B]

I added the stuff in bold following some suggestions on the forums.  I'm obviously seeing the prompt for windows, but it doesn't work....

Just need to get into Windows every now and then to grab stuff and port it over.  I can see my windows drive from Ubuntu and browse files, just can't boot from it.

Any help would be great!

---

### Post by Pumalite on 2008-02-20
Let XP be Master (sda). Install Ubuntu in 2nd drive with XP drive connected. Let Grub install in MBR (sda) and you'll have dual boot.

---

