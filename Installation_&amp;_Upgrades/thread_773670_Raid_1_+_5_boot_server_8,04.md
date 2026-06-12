---
title: "Raid 1 + 5 boot server 8,04"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by rgotten on 2008-04-29
I am in the process of installing my server and have being trying for the last few weeks diferet options on isntalling my raid and be able to boot. I am installing the boot on Raid 1 128mb, Swap on Raid 1 (2gb), the root on raid 5 (10 gb) and the rest for home on Raid 5 ( aprox. 960 gb).
For doing this i am using 3 hard drive 500 ngb each. Before the 8.04 relaese i had to install the boot instruction on each one of the hard drive (device (hd1) /dev/sda
root (hd1,0)
setup (hd1)
device (hd1) /dev/sdb
root (hd1,0)
setup (hd1)
device (hd1) /dev/sdc
root (hd1,0)
setup (hd1)
so if one fails the raid can be started from the other hard drive. With version 8.04, when i disconect either of the hard drive it appears to boot and i get a message that says: start the raid in degrade (or somethng similar), with the command mdadm -R /dev/mdx ( in version 7.10, i have to install the boot insruction in each one of the hard drive). Since i am getting this message, does this mean that the newer version has the bug fixed in regards to the instruction on how to boot in each one of the hard drive??

How can i check each hard drive to be sure they have this instruction and that i have installed grub also on the second disk's (/dev/sdb) master boot record (MBR), as well as the third. ??

rgotten

---

