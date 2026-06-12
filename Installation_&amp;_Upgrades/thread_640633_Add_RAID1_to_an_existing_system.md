---
title: "Add RAID1 to an existing system"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by dbyrne on 2007-12-14
I can't believe that I'm the first person to have ever done this, but after several frustrating hours of trawling the forum and other sites I can't find an answer to my question ...

I have a running Ubuntu 7.04 system on one 300Gb drive with four partitions (filesystems /, /opt, /home, swap). I have bought a second identical drive and would like to add it to the system so that all partitions on the first are RAID1 mirrored.

My question is simply how to do this :) Any links or comments on the ramblings below would be very welcome :)

I'm thinking:

1. Put the second drive in as IDE secondary slave, format it the same as the first using gparted giving me /dev/hdd1-4;

2. Copy the /, /opt, /home partitions over (what's the best way ?), something like:

$ mkdir /mnt/newroot
$ sudo mount -t ext3 /dev/hdd1 /mnt/newroot
$ cd /
$ find . -depth -print0 | cpio &#8211;null &#8211;sparse -pvd /mnt/newroot

Same for the other partitions. Do I really need to do this though ? Won't the RAID re-sync ensure that the second disk is the same as the first ? (Any chance that if I don't do this copying, the RAID re-sync it will make the first disk the same as the second, i.e. delete everything ?)

3. Make the second drive bootable (is all this necessary ?):

$ sudo install-mbr /dev/hdd
$ sudo grub-install /dev/hdd1
$ sudo grub
grub> device (hd0) /dev/hda
grub> root (hd0,0)
grub> setup (hd0)
grub> device (hd0) /dev/hdd
grub> root (hd0,0)
grub> setup (hd0)
grub> quit


4. Make RAID1 devices:

$ mdadm --create /dev/md0 --chunk=64 --level=raid1 --raid-devices=2 /dev/hda1 /dev/hdd1
$ mdadm --create /dev/md1 --chunk=64 --level=raid1 --raid-devices=2 /dev/hda2 /dev/hdd2

Create /dev/md2-3 in the same way.

5. Reboot ???

---

### Post by ian dobson on 2007-12-14
Hi,

When creating your array, only have one drive in your configuration so you create a degraded array, then add the missing drive. 
Something like:-

mdadm --create /dev/md0 --level 1 --raid-devices=2 missing /dev/sdb2
mdadm /dev/md0 -a /dev/sda2

Have a look here:- [http://www.parisc-linux.org/faq/raidboot-howto.html](http://www.parisc-linux.org/faq/raidboot-howto.html)

Note: This is only a rough idea and make sure you have good backups before you start.


Regards
Ian Dobson

---

### Post by psusi on 2007-12-14
Yea, creating the array destroys the existing data AFAIK, so you will need to create the array initially only with the new drive, copy all files over, boot from that drive, then add the first drive to the array.  

Also don't connect one drive as master and the other as slave since only one can be accessed at a time, and that will kill the performance of the raid.

---

