---
title: "Help multiboot Ubuntu and W2K"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by ifouane on 2006-12-02
I'm newbie and want to install Ubuntu on my new machine;
For some apps I still need Windows for the short term.
I'm installing first W2K without problem, then install Linux in additional partition. Linux is working Ok but being installed, Windows is no more starting (message ntoskrnl.exe not found)more over if I try to restore W2K it does not recognize anymore the existing FAT32 and NTFS partitions.
I have the same with Fedora 6 installation
I can't find what is wrong, could someone give some advise?
(I'm using a ASUS P5WH Deluxe board with 250Gb SATA drive)
Thanks

---

### Post by ajgreeny on 2006-12-02
When you get to installing ubuntu do you chose to use the largest free space or the whole disk?  Assuming you have the live CD you should chose the free space option, then set the size you want by using the slider.  It is probably easiest not to set partition sizes before you start installation of windows, but let the installer do it all.

The other possible, and perhaps easier way for the partitioning bit, is to use the alternate install CD, not the live CD.  If you don't really understand partitioning, however, stick with the live CD version and try again.

Just to check things further, in ubuntu, open a terminal and type:-
sudo fdisk -l
The -l is a lower case L, not a figure 1.  This will then show all the partitions on disks on your machine so you will be able to see if the ntfs or fat32 partitions are still there as you believe.

Look at these pages as well, they have some useful info.
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

And good luck.

---

### Post by ifouane on 2006-12-02
I'd checked
When I look to my partitions From Ubuntu or from my hdd tool (MaxBlast from Maxtor) everything looks ok.
I just tried to restore the MBR with MaxBlast.
As expected Ubuntu is not launched anymore,but W2K still gives the same message.

---

### Post by ifouane on 2006-12-11
Hi, I finally understood what what happening:
While installing Linux in the disk free space, I was creating a new primary partition which in turn changed the number of my windows partition (it is a partition inside an extended partition). The result was that the windows boot.ini file was no more pointing to the right partition. Simply editing this file solves the problem

---

