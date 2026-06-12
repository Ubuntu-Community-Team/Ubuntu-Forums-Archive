---
title: "LVM resizing needed"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-06-30
I have installed a long time ago LVM - and now I have to resize it.

I cannot find out how much space I have to resize. I know I left space to resize ;-)

Here are some information. I want to increase the size of /home (96%) - maybe reduce some other lvmvolumes.

root@ronald-desktop:~# lvscan
  ACTIVE            '/dev/lvmvolume/root' [48.83 GB] inherit
  ACTIVE            '/dev/lvmvolume/home' [97.66 GB] inherit
  ACTIVE            '/dev/lvmvolume/var' [48.83 GB] inherit
  ACTIVE            '/dev/lvmvolume/swap' [10.00 GB] inherit


root@ronald-desktop:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/lvmvolume-root
                       49G  7.8G   38G  17% /
varrun               1008M  356K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
procbususb           1008M  120K 1008M   1% /proc/bus/usb
udev                 1008M  120K 1008M   1% /dev
devshm               1008M  2.0M 1006M   1% /dev/shm
lrm                  1008M   43M  966M   5% /lib/modules/2.6.24-19-generic/volatile
/dev/sda1              99M   91M  3.6M  97% /boot
/dev/mapper/lvmvolume-home
                       97G   88G  4.0G  96% /home
/dev/sdb1              40G   39G  248M 100% /media/hdc1
/dev/sdb3              56G  4.9G   48G  10% /media/hdc3
/dev/sdb5              40G   27G   13G  67% /media/hdc5
/dev/sdb6              50G   46G  4.5G  92% /media/hdc6
/dev/sdc1              79G   73G  5.9G  93% /media/hdd1
/dev/sdc5              71G   60G   11G  85% /media/hdd5
/dev/mapper/lvmvolume-var
                       49G  5.8G   40G  13% /var



root@ronald-desktop:~# fdisk -l /dev/sda

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00027078

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391   83  Linux
/dev/sda2              14        6093    48837600    7  HPFS/NTFS
/dev/sda3            6094       38913   263626650   8e  Linux LVM


I "think" when I installed I used /dev/sda2 as an emergency partition to be able to install Windows. Now after 1.5 years Ubuntu I am sure I don't want Windows anymore. I tried: mount /dev/sda2 /media/dir but it gave me an error: 
mount: you must specify the filesystem type
Does that mean I "think" right and it is just empty space?

If so, how can we use also this space to get /home/ larger?

---

