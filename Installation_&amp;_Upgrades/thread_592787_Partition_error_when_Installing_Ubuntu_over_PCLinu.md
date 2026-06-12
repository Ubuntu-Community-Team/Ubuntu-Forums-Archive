---
title: "Partition error when Installing Ubuntu over PCLinuxOS"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by Nghiem Anh Tuan on 2007-10-26
Hi, I tried to install Kubuntu 7.10 over PCLinuxOs 2007 with Desktop Live CD but when I came to the partition step, Kubuntu said  that my hard disk is unallocated. In fact my labtop is dual boot with Windows media center and PCLinuxOs and it works normally. I have tried GParted, QParted and even PQMagic, all of them said that there are errors on partition table. I think that when I installed PCLinuxOs, I have installed grub on MBR. That is why partition program could not recognize partition table of my hard disk. Could anyone help me to solve the problem?

---

### Post by mikewhatever on 2007-10-26
Installing grub to the mbr is a normal installation procedure, so that should not be the problem.

---

### Post by louieb on 2007-10-26
PClinuxOS uses the Disk Drake partitioner. I've seen it do some weird stuff no other partitioner can or will do. The weird thing is the PC works afterward.    
Boot the the Ubuntu Live CD, open a terminal wndow, and post the output of ```
sudo fdisk -l
``` (lowercase L) and maybe we can see whats going on.

---

### Post by Nghiem Anh Tuan on 2007-10-26
Thank you, I will try it now

---

### Post by Nghiem Anh Tuan on 2007-10-26
I have tried and the result is:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25de25dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6446    51777463+   7  HPFS/NTFS
/dev/sda3            6460        8455    16032870   83  Linux
/dev/sda4            6447        9729    26370697+   5  Extended
/dev/sda5            6447        6459      104391   82  Linux swap / Solaris
/dev/sda6            8456        9729    10233373+  83  Linux

Partition table entries are not in disk order

---

### Post by louieb on 2007-10-26
Yes there it is.  If you look at the start end blocks. and arrange them in start block order.   You  will see that primary partition sda3 is inside  extended partition sda4.  
sda5 and sda6 are logical partitions and have to be in an extended partition. But sda3 should not be inside.     
Primary and extended partition are numbered 1 to 4, logical partitions   are numbered 5 and higher.
 [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

 ```

/dev/sda1 * 1    6446 51777463+ 7 HPFS/NTFS
/dev/sda4 6447 9729 26370697+ 5 Extended
/dev/sda5 6447 6459 104391 82 Linux swap / Solaris
/dev/sda3 6460 8455 16032870 83 Linux
/dev/sda6 8456 9729 10233373+ 83 Linux

```Anyway thats why GParted and the other partitioning programs say there is an error in your partition table.   
Not sure what will fix it. but some how your going to need to delete all but sda1 which I assume is you Windows install. This will create a block of unallocated space that GParted or some other program can partition in the usual manner. 
Might try the PClinuxOS live CD or maybe the partitioner one the Ubuntu alternate CD. Another on to try is the [SystemRescueCd]("http://www.sysresccd.org/Main_Page").

---

### Post by meierfra on 2007-10-26
Try [ testdisk]("http://www.cgsecurity.org/wiki/TestDisk"). It fixed various of my partition troubles. 
[ Hermanzone]("http://www.users.bigpond.net.au/hermanzone/p21.html") has more information on testdisk. Testdisk can be found on the [Gparted Live Cd]("http://gparted.sourceforge.net/") and also on the Rescue  CD mentioned in the previous post.

---

### Post by Nghiem Anh Tuan on 2007-10-27
Thank you. I have used testdisk to remove linux partitions. Now I have successfully installed Kubuntu.

---

