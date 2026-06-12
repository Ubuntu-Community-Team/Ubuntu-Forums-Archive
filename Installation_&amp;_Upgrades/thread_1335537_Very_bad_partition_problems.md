---
title: "Very bad partition problems"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by Robert Blafford on 2009-11-23
Hello everyone. 
 
I am having very bad problems when paritioning my hard drive with gparted. I have a new hp laptop with windows 7 on it and I am trying to put ubuntu 9.10 on it with dual boot. My first step would be to partition my drive in windows since doing that in ubuntu would not let me reboot into windows7. So i create free space and then load in the live cd. From there i would use gparted to format the free space into the ext4 file system. This will not let me reboot into windows 7. Notice that I haven't installed anything yet. It will try to boot into windows and then halt halfway. The only way for me to reboot is to undo what I have done in gparted.
 
Any help would be greatly appreciated
Thank you.

---

### Post by zvacet on 2009-11-23
Create free space in way to shrink existing Windows partition.You can do that with live CD or with [Gparted live CD.]("http://gparted.sourceforge.net/")On created free space install Ubuntu and after that grub should recognize both OS and you can choose witch one you want to use.

---

### Post by Robert Blafford on 2009-11-23
I have done that. I have tried to create free space with both operating systems and they both work. When I try to format that free space, then I cannot boot into windows. Grub or ubuntu has not been installed yet! I just want to reboot with that new partition. I think win 7 keeps a record of the hd in the mbr and will report an error if it doesnt look the same way as it was the last time it shut down

---

### Post by Mark Phelps on 2009-11-23
> **Robert Blafford said:**
> I have done that. I have tried to create free space with both operating systems and they both work. When I try to format that free space, then I cannot boot into windows.

My guess would be that when you created the free space using GParted, you got hit by the "Gparted sometimes corrupts MS Windows OS partitions" problem -- leaving you an MS Windows installation that will no longer boot.

Since you knew you were going to be messing with partitions, you made sure that you used the Win7 built-in function for creating and burning a Win7 Recovery CD, right?

In that case, boot from that recovery CD and run Startup Repair three times to restore the Win7 boot loader.

---

### Post by oldfred on 2009-11-23
starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

Herman's MBR page
[http://members.iinet.net.au/~herman546/p6.html](http://members.iinet.net.au/~herman546/p6.html)
sudo fdisk -lu
The result of that command will show that the first partition almost always begins in sector 63, except in the case of Vista and Windows 7, which normally don't begin until sector 2048.

---

### Post by Robert Blafford on 2009-11-23
Thank you so much I will try this tonight

---

### Post by Robert Blafford on 2009-11-23
Sorry but unchecking the box to round the cylinders off still hasn't resolved the issue, any more suggestions?

---

### Post by Robert Blafford on 2009-11-23
Here is my fdisk -lu if it helps

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xebfe1010

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2048      409599      203776   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3          409600   451059711   225325056   42  SFS

Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    15682526     7841232    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(976, 48, 63)
ubuntu@ubuntu:~$

---

### Post by oldfred on 2009-11-23
You forgot to mention you had encrypted partitions.

How to: Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

from above:
Resizing your encrypted file system can not be done directly as of yet with Gparted as Gparted sees the encrypted partitions as unformatted space.

---

### Post by Robert Blafford on 2009-11-23
Hey thanks very much for the help, are you sure that I have an encrypted harddrive

---

### Post by Robert Blafford on 2009-11-23
If I just buy a new windows 7 cd (I can get a student edition for $29) won't this just fix the problem? Everyone else that has windows 7 can dual boot except for me any my hp encrypted drives?!

---

### Post by oldfred on 2009-11-23
I do not know encrypted partitions but you still are working with them.

/dev/sda1              63        2047         992+  42  SFS

the 42 SFS is identified as encrypted.

---

