---
title: "Installing Ubuntu without deleting Windows 8"
date: 2015-08-25
forum: Installation &amp; Upgrades
---

### Post by cor0na2 on 2015-08-25
Hello,
I want to install Ubuntu 14.04 on my laptop. My HDD is separated into 3 partitions. Disk E: is empty so I want to install Ubuntu there. My question is how to do that without erasing files from C: and D: where my Windows 8 is. I have to use "Something else" in the installation process because I don't have an option to install Ubuntu along side with W8.
Thank you for the help!

---

### Post by Bucky Ball on 2015-08-25
Welcome. Yep, use 'Something Else'. First you need to boot into Windows and switch off hibernate and fastboot then erase partition where you want to install Ubuntu and leave it as free space. Be aware that you will need at least two partitions for Ubuntu:

/ = where the OS goes,
/swap = like a Win pagefile.

If you are going to store your personal data on an NTFS partition to share with Win then make / about 20Gb. If not, make / as big as you can. /swap only needs to be 2Gb.

Welcome. Once you are in the Something Else manually partitioning section of the install you will see the Win partitions clearly. They will be NTFS filesystem. Leave them be, don't touch 'em.

To create your Ubuntu partitions is simple. The mountpoints / and /swap you will find as defaults in there. You only need to select them. / should be a EXT4 filesystem and /swap will be 'swapspace'. 

Let us know if/when you hit a brick wall and it goes without saying, if you haven't already, backup anything you wouldn't want to lose if things go pear-shaped. :) 

PS: Linux-ers don't refer to disks/partitions as E and D, etc. That is a Win thing (a misnomer and a bit confusing as all partitions are considered disks with this convention). When you look in the partitioner you will see the partitions are labelled 'sda1' for example. This means sda = first disk, sda1 = first disk, first partition. So, sd*^ where * = the disk letter and ^ = the partition number on that disk. 

sdc3 would be the third disk, third partition. Hope that makes sense. :)

---

