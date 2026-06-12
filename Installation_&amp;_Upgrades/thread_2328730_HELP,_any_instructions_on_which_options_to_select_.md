---
title: "HELP, any instructions on which options to select in 16.04 install??"
date: 2016-06-23
forum: Installation &amp; Upgrades
---

### Post by gje975 on 2016-06-23
I'm trying to install 16.04 on my computer which has Win XP SP3 and all my data on a 2TB disk 1 (sda), I have a 1TB disk 2 (sdb) with a 330 GB free space and then 2 NTFS partitions which are now empty. 

At the start I selected install updates during the install and to install 3rd party software for MP3, flash, etc, but the install hung and would't proceed, so I quit, unchecked the 3rd party stuff and it then went ahead

The questions in the 16.04 install are confusing.  When I got to the install selection window I was certian I did NOT want to reformat my sda disk with Win XP and all my data on it, so I selected "something else".  But then a window comes up to select partitions,  It is unclear how you select a partition in the sdb 330 GB free space.  Clicking on the "free space" line does nothing.  I found clicking on the "+" at the left of the partition line brings up another window and allowed me to create a linux partition in the free space, but then when I click continue a window comes up saying I need to create a swap space but has no instructions on how to do that. I have 12 GB RAM so I should have a 24 GB swap file, but how do I create it???  Also it is not clear what mount point I should select for any partition, I selected "/" for the linux partition I created, but that is probably not correct. 

Also, at the bottom of the main window is a selection of where the boot file should go.  Two drop down choices, but no hint of whether it shold be on sda (disk1) or sdb (disk 2).  I know the Linux boot program destroys the Win boot loader, and I think it goes on disk1, but that's not clear.

Is there a detailed tutorial or instructions on how to answer all these questions that come up in the install?  I never got past failing to specify the partitions, but I.m sure there are more choices without explanations of how to select them.  Thanks in advance for any help.

---

### Post by oldfred on 2016-06-23
With 12GB of RAM, I would only use 2GB for swap. You may never use it.
You would only need swap larger if desiring to hibernate, which is not really required.
You also may have the issue with MBR(msdos) partitioning of 4 primary partitions. You can make one and only one primary an extended and have an unlimited number of logical partitions inside it.

I would keep Windows boot loader on sda, and install grub to sdb drive. And set BIOS to boot sdb.
XP is obsolete. You may have to have drives set to IDE when much better to use AHCI. But my XP would not boot in AHCI mode. When I got SSD that had to have AHCI for trim to work, I shut XP down. :)

Differences between versions is minor, process is the same for Something Else:
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation) 

        Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by Geoffrey_Arndt on 2016-06-24
gje975 . . . well, first things first.   Read & re-read OldFred's post including links.   Next, copy or backup your data to external media or the cloud.   So, if the install is messed up (entirely possible if not sure what one is doing),  then at least you have your data.    After securing your data, the simplest install might just be to nuke XP by installing Ubuntu on sda (drive1) and then use the second drive (sdb) for data storage.   Grub then goes on sda.    Also, I usually prefer to format and setup the partitions before running the installer (using the Live Media and the gparted program).   Use ext4 for the filesystem type.   You can also setup the swap partition using gparted.    Much simplifies things in some cases.

Also, it's always a good idea to provide your machine specs (make, model, ram, storage layout, wireless info, graphic card/chipset info (intel, nvidia, ati/amd, etc).   If your machine is quite old, it may not even run Ubuntu.

---

