---
title: "How to set right Linux Mint MATE Version 17.2"
date: 2015-08-11
forum: MINT
---

### Post by rami7 on 2015-08-11
TO Proper installation Alongside Windows?
in Version 17.2 For example In STEP OF Setting of partitioning there is not in Starts option of add
so what to do?
My data :
 [http://i58.tinypic.com/2ugoxvd.jpg](http://i58.tinypic.com/2ugoxvd.jpg)
 [http://i61.tinypic.com/2898jy9.jpg](http://i61.tinypic.com/2898jy9.jpg)
 [http://i58.tinypic.com/1pebuc.jpg](http://i58.tinypic.com/1pebuc.jpg)
 IN
 device for boot loader installation
 What to choose among the three?
/dev/sde of Hard disk&#8236;&#8207;
/dev/sde1 microsoft windows xp home edition
/dev/sde5 none
  
 thanks.

---

### Post by QIII on 2015-08-11
Support question moved to ***Mint***

---

### Post by yancek on 2015-08-11
The first image you posted is merely stating you need a minimum of 8.7GB of space available on which to install Mint.  If it is connected to the internet during the installation, you can install additional software which does not come on the installation media.

The other two images show you have two windows partitions, the first (sda1) is an ntfs formatted partition which I expect contains your unsupported windows xp.  The second is a FAT32 (windows filesystem) partition which is almost empty.  You don't have anywhere to install Mint at present.  The best thing to do would be to shrink the almost empty FAT32 partition.  I don't know if xp has the necessary software to do this?  You can use GParted (a partition manager) which should be on the Mint installation media.  Simply open a terminal when booted to the Mint install media and enter:  sudo gparted (hit the enter key and the partition manager window will open) and you can then shrink the partition and leave unallocated space on which to install Mint.  If you are not familiar with partition managers, the link below is to an excellent tutorial on using GParted.  It has a Table of Contents so you can go right to the section you want although you would be well advised to read through the whole thing so you understand what is happening.

  [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

After you have shrunk the partition, just reboot the Mint installer and you should be able to proceed.
The Device for bootloader installation should be the default, /dev/sda as a default windows is incapable of booting any Linux system.  This should give you the option to boot both Mint and xp after the installation successfully completes.

---

### Post by rami7 on 2015-08-13
> **yancek said:**
> The first image you posted is merely stating you need a minimum of 8.7GB of space available on which to install Mint.  If it is connected to the internet during the installation, you can install additional software which does not come on the installation media.

The other two images show you have two windows partitions, the first (sda1) is an ntfs formatted partition which I expect contains your unsupported windows xp.  The second is a FAT32 (windows filesystem) partition which is almost empty.  You don't have anywhere to install Mint at present.  The best thing to do would be to shrink the almost empty FAT32 partition.  I don't know if xp has the necessary software to do this?  You can use GParted (a partition manager) which should be on the Mint installation media.  Simply open a terminal when booted to the Mint install media and enter:  sudo gparted (hit the enter key and the partition manager window will open) and you can then shrink the partition and leave unallocated space on which to install Mint.  If you are not familiar with partition managers, the link below is to an excellent tutorial on using GParted.  It has a Table of Contents so you can go right to the section you want although you would be well advised to read through the whole thing so you understand what is happening.

  [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

After you have shrunk the partition, just reboot the Mint installer and you should be able to proceed.
The Device for bootloader installation should be the default, /dev/sda as a default windows is incapable of booting any Linux system.  This should give you the option to boot both Mint and xp after the installation successfully completes.

i have "mini tool pratation wizard free" , instead of gparted, it's ok?
Maybe it is better to install Before linux and afterwards windows xp We will be together?
THANKS

---

