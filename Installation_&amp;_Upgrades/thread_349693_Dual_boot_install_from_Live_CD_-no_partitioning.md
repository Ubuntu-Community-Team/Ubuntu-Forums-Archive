---
title: "Dual boot install from Live CD -no partitioning"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by btw-nc on 2007-01-30
My goal is to have a dual boot setup with XP in one partition and Ubuntu in another. There are two volumes on the drive currently. One is for XP and it's NTFS. Another is called HP_RECOVERY and it is FAT32.

I can run Edgy fine from the CD. I tried to install from the same CD. I got to the partitioning utility: "How do you want to partition the disk?"

I chose "Resize SCS|1 (0,0,0), partition #2 (sda) and use freed space. New partition size: 29% (40.4GB)

After clicking the Forward button, the spinner wheel started and nothing else happened for I suppose an hour. No disk activity light - nada that I could tell. I clicked "Cancel" and aborted the installation.

Question: Is the new partition (40.4GB in this case) designated for the Ubuntu installation? What did I do wrong?

---

### Post by fktt on 2007-01-30
first off.. what version of ubuntu were you trying to install there?

---

### Post by btw-nc on 2007-01-30
> **btw-nc said:**
> 
I can run Edgy fine from the CD. I tried to install from the same CD.

Umm, Edgy.

---

### Post by zvacet on 2007-01-30
Try with Edgy alternate CD.I had same expirience as you when i tried to innstall from live CD.Alternate CD is better choice.

---

### Post by housam on 2007-01-31
Boot from the live CD and use Gparted tool to configure your partitions.If it is the same as before starting the installation, use it to resize the windows partition ( defrag the partition at least twice before resizing and back-up every thing) to create an unallocated space . devide this space into two new partitions :
one for the root ( / ) ext3 format and the other for the swap ( 1 Gb swap format ). 
After that you can go for the installation .

If you find the partition already exist, repartition it the same as mentioned above and continue for the installation.

---

### Post by btw-nc on 2007-01-31
Thanks, Housam.

I now have Edgy installed (one HD, dual booting with XP) partially with the help of the tutorial at psychocats.net

Some observations from a neophyte at all of this:

The first effort at manual partitioning resulted in an error. Drilling down into the details it said that my NTFS volume had an error and for me to run chkdsk /f. So I did. It must have worked.

Second attempt after fixing the NTFS error: after I got finished manually setting up the partitions (I opted to make a /home dir.) and then the mount points, everything was looking good. Then a dialog box popped up called "Go Back to the Menu?" It indicated that no file system was specified for partition #2 (the NTFS one where Windows is). "If you do not go back to the partitioning menu and assign a file system to this partition, it won't be used at all."

I chose the "continue" button instead of going back. Going back was the default choice though.

The installation finishes and I reboot. GRUB comes up - so far so good. I chose to boot Windows.

It took SO long with SO much disk activity that I just knew something was wrong. Anyway, Windows finally came up just fine.

I haven't done anything with Ubuntu so far, other than (manually) installing the Flash plug-in, again with help from psychocats.net.

The only problem I've noticed is with my LCD display: Samsung monitor, NVIDIA GeForce 6600 card. The entire display is slightly off horizontally. If I have it set right with Windows, everything in Ubuntu is pushed off the right edge by about 10 or 15 pixels.

---

### Post by housam on 2007-02-01
Glad to here that you did it. welcome to ubuntu.

---

