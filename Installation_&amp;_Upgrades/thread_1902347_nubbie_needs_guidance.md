---
title: "nubbie needs guidance"
date: 2011-12-30
forum: Installation &amp; Upgrades
---

### Post by C3Landshark on 2011-12-30
Hello all....first post and it should be an easy one for all the experts on this forum.

I have downloaded the ISO and burned the disk for Ubuntu 11.10. My system is an older AMD machine running Windows XP Pro SP3. I have a mirrored pair of 160G SATA drives partitioned with 80G for windows and an unallocated partition of 80G. I would like to install Linux on the unpartitioned area and make this a dual boot system. I have loaded the CD and poked around and this OS seems to be what I am looking for. I have been all through this website [http://members.iinet.net.au/~herman546/p17.html#Preparation_For_The_Install_ ]("http://members.iinet.net.au/%7Eherman546/p17.html#Preparation_For_The_Install_")
I'm just not grasping the what i need to do. When I try to run the install, Linux see's the windows 80G partition nd nothing else that i can tell. I even partitioned the 2nd 80G into a 60G and 20G part, and the OS still did not see the new parts. 

Kind lost here....

Thanks for any replies

---

### Post by darkod on 2011-12-30
1. Don't partition with NTFS for linux, it doesn't install on NTFS.

2. For installing on RAID (I assume fakeraid, bios raid) you need to use the Alternate Install CD, not the standard desktop image. It can be done, but often grub2 doesn't install correctly with the desktop cd. The alternate cd has raid support and is recommended for raid.

I always prefer manual partitioning during the install. You need a minimum two partitions, bigger root '/' partition, and smaller swap.

---

