---
title: "Install multiple Linux"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by billiardman on 2010-03-01
I am a nubi to linux and have just bought a new Win 7 puter and now have an older puter to play around with and test its limits. I have already installed KK 9.1 on the system. I would like to install a couple other versions of linux to test out. 

My system is:

1.2 ghz AMD proc
200   gb hd
500 mb ram
ATI 128 rage pro ultra

I originally installed using the whole HD. I know that I need to do is repartition it. So before the adventure I figure I would get a little advice as to how to partition the HD to accommodate the least amount of pain with lost data. No backups are necessary as I am testing only. I am doing this because I eventually plan to dump windoze but not until I become comfortable with linux. I would like to make room for a total of 3 linux versions. As it stands now, KK is running smoothly. I have done 2 updates so far and no disasters yet. Any help would be greatly appreciated.

---

### Post by Neezer on 2010-03-01
you can use gparted to resize your partition. I would say about 20 or 30 GB for each. You don't need to make a swap partition because any new installs should use your original swap that was made when you installed karmic....At lease I know ubuntu will.

You might want to think about making a partition for your media files that way you can store them and just mount them onto the file system, and you don't have to worry about losing them all from installing on a separate partition.

a few things to remember 
1- make a backup before making any changes with gparted. It should work without a problem, but any time you're making system critical changes like that it is better to be safe than sorry.

2- make sure you are installing to the correct partition. it would be a shame to lose your 9.10 install because you accidentally installed a different distro onto that partition.

good luck

---

### Post by presence1960 on 2010-03-02
you may want to shrink your current partition & then create an extended partition from all the unallocated space you just created. This way you can create as many logical partitions inside the extended partition for those other distros as you wish. The only limit on the amount of logical partitions you can create will be the amount of space allocated to the extended partition.

If you do not create an extended partition you will be limited to the 4 partition rule on a hard disk. You can not have more than 4 primary partitions on a disk. Or you can have 3 primary and one extended. You can create logical partitions inside the extended as I mentioned above. Linux, unlike windows, has no problem booting from a logical partition.

---

