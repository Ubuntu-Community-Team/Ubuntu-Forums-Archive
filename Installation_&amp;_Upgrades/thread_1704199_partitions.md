---
title: "partitions"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by fburhas on 2011-03-10
hi

im using ubuntu 8.04 right now but id like to install ubuntu 10.10 or ubuntuStudio. well i did it for trying as a dual boot just to see if it works. but i have files to back up. i tried to have them on dvds or usb but it takes time. i want to know if i can creat a new partition where to stock my files and then erase the rest to install ubuntu 10.10

when im in gparted i see:

_/dev/sda                                        111.79GB_:
      /dev/sda1        ext3                  107GB
      /dev/sda2        extended           4.58GB      ->  i cant use it :(
            /dev/sda5  ext3                  4.3GB
_/dev/sdb                fat32                 15GB_         -> i think its my ubuntustudio

is there any chance to create a new partition (40GB) to stock my files?

---

### Post by ajgreeny on 2011-03-10
> **fburhas said:**
> hi

im using ubuntu 8.04 right now but id like to install ubuntu 10.10 or ubuntuStudio. well i did it for trying as a dual boot just to see if it works. but i have files to back up. i tried to have them on dvds or usb but it takes time. i want to know if i can creat a new partition where to stock my files and then erase the rest to install ubuntu 10.10

when im in gparted i see:

_/dev/sda                                        111.79GB_:
      /dev/sda1        ext3                  107GB
      /dev/sda2        extended           4.58GB      ->  i cant use it :(
            /dev/sda5  ext3                  4.3GB
_/dev/sdb                fat32                 15GB_         -> i think its my ubuntustudio

is there any chance to create a new partition (40GB) to stock my files?
I am confused!

It looks to me as if sda1 is your Ubuntu partition, it is certainly not sdb as that is not a partition any partition
 a) should have a number, eg sdb1, sdb is just a device/disk. 
 b) Ubuntu can not be installed on a fat32 partition 

The partition sda2 is an extended partition and sda5, probably swap, is sited within sda2, but for some reason does not seem to use all of it.

From your running ubuntu OS or even from a live CD or USB can we see the output of ```
sudo fdisk -l
``` which will give a better chance of giving you the right information.  If possible screenshots of gparted for sda and sdb would also be useful.

---

