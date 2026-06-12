---
title: "Remove ubuntu w/o affecting Windows"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by Camilia on 2010-01-19
I love Ubuntu but now I am school and have to use Windows. Twice I have tried to have both on my PC. Either windows, or Ubuntu have problems when I have both on my computer.

I have spent hours getting Windows updated.  Now so little space for Ubuntu that I have lost the ability to recover a document. Thus decided to remove Ubuntu. This second time loaded Ubuntu in at start up, after installing Windows. Thus it is not in the programs. 

I at GRUB went to start up programs and tried to delete Ubuntu.  It didn't work. 

How can I remove Ubuntu and not affect Windows.

---

### Post by dstew on 2010-01-20
You can remove Ubuntu by removing the partition that contains it, using gparted from a Live CD, or similar partition manager. However, if you do this, you will have two problems. First, by removing the Ubuntu partition, you will remove some components of grub, and therefore you will not be able to use grub to boot Windows. Technically, if you have grub2, you should still be able to boot using the command line, but that is not so good for long term use. You will need to install a new boot loader.

Second, you will need to expand the Windows partition and the ntfs file system to take advantage of the new space. This is harder than you might think. You can easily expand the *partition* using gparted, but you also have to expand the *ntfs file system* that is within the partition. Gparted will not do this for you. You need to use the linux command-line program [ntfsresize]("http://man.linux-ntfs.org/ntfsresize.8.html") to do this. If you don't do it right, you can destroy the file system. So, make sure you do a back-up. The ntfsresize program is on the [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php"). It appears that the Windows repair tools can also expand the ntfs file system. See [this article]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/").

---

### Post by presence1960 on 2010-01-20
You can remove Ubuntu by booting the Ubuntu Live CD. Choose "try ubuntu without any changes". When the desktop loads open a terminal and run ```
gksu gparted
```
This will open gparted. Delete the Ubuntu partitions (backup data you don't want to lose beforehand).
Next step is very important since GRUB is on MBR of your disk and you will not be able to boot windows until you put Windows back on the MBR. Open a terminal from the Live CD still and run ```
sudo apt-get install lilo
```
This will install lilo to the Live CD session. 
Next in terminal run ```
sudo lilo -M /dev/sda mbr
```
This will fix your MBR so windows will boot. sda assuming you have only one hard disk. Once complete you can reboot without the Live CD and boot right to windows. You can use windows disk management utility to set up the unallocated space from the Ubuntu partitions as you like. You can either extend C: to include all that unallocated space or create new partition(s).

---

### Post by Camilia on 2010-01-23
Thanks for the info!!

---

