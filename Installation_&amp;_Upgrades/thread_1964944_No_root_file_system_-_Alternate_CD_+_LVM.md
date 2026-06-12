---
title: "No root file system - Alternate CD + LVM"
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by charliezen on 2012-04-24
I am trying to install 11.10 as dual boot with Windows 7.
I have all partitioned well as you can see here:

[http://www.flickr.com/photos/42897978@N00/7111180385/](http://www.flickr.com/photos/42897978@N00/7111180385/)

I burned the Alternate CD ISO to a CD.
Boot from it and followed instructions to Partitioning.

There, I configured the LVM partitions as follows:

Volume Group
* ubuntu-vg
- Uses Physical Volume          /dev/sda7     380GB
- Provides Logical Volume      home-lv        60GB
- Provides Logical Volume      root-lv          60GB
- Provides Logical Volume      swap-lv          6GB

That is all I want (note that my /boot is outside of LVM)

Then when I say that all is Ok and to write it to disk and 
continue with the installation, I get the following error.

!! Partition Disks
No root file system
No root file system is defined
Please correct this from the partitioning menu.

What should I fix and how?

I tried issuing the "Revert changes to partitions", but nothing happens.
It seems that the LVM configuration has already been written to the CD.

HELP!!

[IMG]http://www.flickr.com/photos/42897978@N00/7111180385/[/IMG]
[IMG]http://www.mercologia.com/solciu/PartitionDiagram.png[/IMG]

---

### Post by kherring7383 on 2012-04-24
You may try to first boot from the install CD or USB drive and then from terminal remove dmraid with sudo apt-get remove dmraid and then use the desktop install shortcut to install Ubuntu. I too have had this problem on occasion when installing 11.04 or 11.10. This didn't happen however when installing Mint 12.

---

### Post by charliezen on 2012-04-24
But, I am not using RAID, I am only using LVM.

And I cant install from the desktop CD because of the same,
if I am going to use LVM, I have to install from the Alternate CD,
which supports LVM.

---

