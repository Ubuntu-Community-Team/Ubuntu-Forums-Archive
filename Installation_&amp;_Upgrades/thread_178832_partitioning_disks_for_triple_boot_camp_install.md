---
title: "partitioning disks for triple boot camp install"
date: 2006-05-18
forum: Installation &amp; Upgrades
---

### Post by wilfordbrimley on 2006-05-18
I'm trying to install ubuntu on a intel mac with xp and osx as described here:
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)

I resized the volumes like this:
#sudo diskutil resizeVolume disk0s2 170G Linux Lin 31G "MS-DOS FAT32" Win 30G

and then use a gentoo live cd to format the Linux partition and make a swap file like they say to:
#sudo passwd root
#su
#mke2fs -j /dev/sda3
#mkdir /mnt/linux && mount -t ext3 /dev/sda3 /mnt/linux
#dd if=/dev/zero of=/mnt/linux/swap bs=1024 count=2097152
#mkswap /mnt/linux/swap
#swapon /mnt/linux/swap

I then restart with the ubuntu 5.10 install disk and everything is cool until I get to the "[!!] Partition disks" screen and the only option for partitioning method that i have available is "Manually edit partition table". I select that and get a screen that says "This is an overview of your currently configured partitions and mount points"... problem is i don't see any partitions or mount points listed...the only options I have available are 
Configure software RAID
Configure the Logical Volume Manager
Guided partitioning
Help on partitioning
Undo changes to partitions
Finish partitioning and write changes to disk

If I click "Finish partitioning and write changes to disk" then I get the red screen that says "No root file system is defined".

i was thinking it might be a naming issue since the SuSE bootstrapping install described here:
[http://www.ethicalhack.org/howto/triple_boot_howto.html](http://www.ethicalhack.org/howto/triple_boot_howto.html)
uses /mnt/suse so i tried using /mnt/ubuntu:
#mkdir /mnt/ubuntu && mount -t ext3 /dev/sda3 /mnt/ubuntu
#dd if=/dev/zero of=/mnt/ubuntu/swap bs=1024 count=2097152
#mkswap /mnt/ubuntu/swap
#swapon /mnt/ubuntu/swap
but i got the same problems at the partition disks screen.

---

