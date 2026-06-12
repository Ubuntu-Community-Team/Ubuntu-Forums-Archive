---
title: "Ubuntu not detecting windows drives"
date: 2016-07-30
forum: Installation &amp; Upgrades
---

### Post by satwaghole on 2016-07-30
I have installed Ubuntu 16.04LTS on my laptop. While installing ubuntu, **I did not selected dual partition and install Ubuntu as my primary OS**. But now ubuntu is not detecting my windows 7(previous OS) drives. I tried to install again windows but its not detecting required partition.

 **I tried to resize/move ubuntu partition but it shows 0 free space. I cannot resize/move it to create unallocated space. :(**

 Attaching Gparted screenshot of my system. Please help me in this regard as I am totally helpless and not able to access my rest of the windows drives.

---

### Post by howefield on 2016-07-30
There are no windows installation partitions on your disk, were you expecting some to be there ?

To resize the Ubuntu partition, you would need to use the Ubuntu Live media which includes gparted, in other words the disk/partition being resized needs to be unmounted before you can work on it.

---

### Post by satwaghole on 2016-07-30
I cannot unmount as it is showing "Cannot unmount .Target is busy" as ubuntu is installed on the same drive. Please help me in this regard as I am frustrated :(

---

### Post by howefield on 2016-07-30
As I said, you have to boot from the Ubuntu Live media that you created to install Ubuntu, and run gparted from there.

---

### Post by grahammechanical on 2016-07-30
The key icons against the partitions mean the partitions are mounted. Running GParted from a live session will leave sda1 & sda1 unmounted.

 The live session will use the swap partition (sda3) so you will not be able to move/resize or delete the swap partition until you use the GParted menu system to take swap off.

Regards.

---

### Post by gordintoronto on 2016-07-30
There might be some misunderstanding about what you did. When you installed Ubuntu, you selected the option which completely wiped out your Windows installation. 

Unless you have multiple hard drives, everything is gone. You might be able to recover some files, but to do this you need to stop using this computer immediately.

---

