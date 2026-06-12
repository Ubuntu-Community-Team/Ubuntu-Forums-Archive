---
title: "Installation Reports from a new user"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by DanWan on 2006-07-06
Reports on some Ubuntu variations distros:

(note: this applies only to my SONY VAIO vgn-T27 laptop)

I need a machine with triple booting (XP, OSX, Linux) to run some minimal Windows packages. They need to run natively therefore I had to get this PC notebook.
As the only working solution to use MACOSX is to install the first hack of the MACOSX-INTEL series I have TIGER OSX 10.4.1. Everything functions properly adding an external Bluetooth but without Wireless connections. NOT WORKING PERIOD: the screen resolution is not 1280x768 (aNY HINTS THANKS) no matter how hard I googled and tried everything suggested.

I do not like Windows so I decided to test Linux as an alternative. Tried SUSE, DEBIAN, MANDRAKE finally decided for the Ubuntu packs.

However:
There are serious discrepancies in the installer program between Ubuntu, Xubuntu and Kubuntu.

To get my 3 partitions working I had to follow this system: 

Partition the HDrive with MACOSX system utilities as follows:
1 FAT32 (for XP)
2 HFSplus for the Mac
3 linux swap (as free space)
4 linux ext3 (as free space)

Install OSX on the second partition
Install XP on the first

Then I tried to use Kubuntu as I prefer the KDE manager and wanted to install kwin-baghira.
As the installer failed on me at the partitioning point several times, I downloaded the ISO from different server, and burned it with different system. The installer always fails at step 5-6 of the graphical or text based process.
As the partitioning screen comes up it gives 3 options:
1 erase the whole thing
2 use the larges free space partition
3 partition manually 

Choosing the manual partition I always get 6 partions

1 the FAT32 windows
2 a hidden very short partition (the MB varied tremendously although within a short range)
3 the MAC hfs+ partition
4 a hidden very short partition (the MB varied tremendously although within a short range)
5 unknown 
6 a hidden very short partition (the MB varied tremendously although within a short range)
7 unknown

Using either Kubuntu or Xubuntu the system crashed the moment I tried to reformat the partitions (step 5-6)

tryng other Linux systems 

DEBIAN Mandrake and SUSE  recognize the Mac partitionning, only Ubuntu does the trick

So I use Ubuntu and I can boot as XP or MAC at bootstrap but I'd like to access my Mac and XP partitions and I was never able to do so.


What is wrong with the different installers and how to mount the other stuff?

---

