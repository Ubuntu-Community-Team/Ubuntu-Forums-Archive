---
title: "Shrink partition"
date: 2006-03-27
forum: Installation &amp; Upgrades
---

### Post by blackeagle on 2006-03-27
Hi,

I installed Kubuntu recently, and want to install another distribution on the same hard drive.

Kubuntu used all free space on a 28.63Gb disk, using the LVM system. Now I want to shrink this partition ( /dev/mapper/Ubuntu-root ).

Any idea how to do it ? I read I had to 
resize2fs /dev/mapper/Ubuntu-root XXXXX
where XXXXX is the number of blocks, but how do I know how many blocks I want to resize it
Also I have to 
lvreduce -L-1G /dev/mapper/Ubuntu-root
is that correct ? But how do I know if the sizes matches ( blocksize / reduce size )

Thanks for help

---

### Post by mikwig on 2006-04-06
it a terminal type:
                             man resize2fs

basically you will need to find out which device your root partition is -probably /dev/hda1
to check this type: sudo fdisk /dev/hda
this will start fdisk - in fdisk press "p" this will list the partitions on the drive. the 
biggest will (if you have no other OS) be your root.

the command will probably look like this then:
resize2fs /dev/hda1 40G

40G = 40 gigabyte - make sure your stated size is smaller than the original size of the disk.

lastly - you can't resize a mounted partition - so you will need some sort of a rescue disk. ( I recommend a gentoo live cd) boot with that and then get to work.

good luck

---

### Post by Mustard on 2006-04-06
As welll as getting hold of a live CD to do this (something like System Rescue CD is a comparitively small download), you might be better off trying a graphical partitioner like qtparted (available on the above CD).

---

