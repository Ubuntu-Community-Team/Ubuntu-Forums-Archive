---
title: "(ask) how to install  quad boot windows 7,android x86,pclinuxos and ubuntu....."
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by XENOVALKRYIE on 2010-09-15
Hai all...im noob sorry if my english is bad.................to the point i want to install Quad booting..on my old pc.................
Intel Pentium IV with 1 Gb ram and ATI HD 3450...............................i want to install 4 os
1.Windows 7
2.Android X86 1.6
3.PCLINUXOS
4.UBUNTU 10.04.....
 can someone give link or guide................................Thanks

---

### Post by oldfred on 2010-09-15
Welcome to the forum.

Do not know anything about Android X86 1.6. Is system old enough that the BIOS will only boot from the first 137GB? That may change how you have to set it up. You need to do a lot of partition planning on how you want to set up hard drive. Generally it is best to install windows first as it has to be in a primary partition. Ubuntu does not have to be in a primary partition.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Dual Boot Win7 & Ubuntu
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Older but similar:
Dual Boot win/Ubuntu
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

---

### Post by XENOVALKRYIE on 2010-09-15
android x86 1.6 is port of google android 1.6 for x86 cpu.................................
the last version is android X86 1.6-r2..
[http://www.androidx86.org/downloads.html](http://www.androidx86.org/downloads.html)

.its very hard to install this os...??

---

### Post by phillipdhall on 2010-09-15
I don't have any experience with andriod, but I am currently running two windows 7 partitions, two XP partitions, and one Ubuntu partition on a motherboard raid0 array. Multibooting is no easy task!
 
In order to be successful, you will need either a guide from someone who's done exactly the same set up as you, or:
1) A thorough understanding of drive partitioning and boot structures, and
2) A thorough understanding of each OS you are working with, including the way each installs its bootloader, and
3) A toolset for editing partition tables and boot records specific to each os, and
4) A LOT of time and patience.
 
I recommend you start here: [http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html) to understand the process.
 
This is also a great resource: [http://www.goodells.net/multiboot/](http://www.goodells.net/multiboot/)
 
This was even more complicated for me because I have a tendency to repartition my array frequently and restore system images to new locations. In this case, I recommend a third party boot loader (I use GAG). Install each operating system such that it thinks it's the only operating system on the disk, so each partition has its OWN boot record.
 
It's certainly possible, but I do want to warn you that it can cause serious headaches if you aren't fully up to the task.

---

