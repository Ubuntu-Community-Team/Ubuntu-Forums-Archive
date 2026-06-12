---
title: "ubuntu doesn't see the installed windows 8.1"
date: 2014-09-22
forum: Installation &amp; Upgrades
---

### Post by mephikiss1803 on 2014-09-22
Help me please.My laptop Lenovo Ideapad Z570. I can not share disk for Ubuntu, I can not choose extenedent disk.When I run the installation, the installer writes that at the moment there is no system has not been established. First gparted seen Partitioning then I used fixparts.



[http://hostingkartinok.com/show-image.php?id=184bf3a4e87104473b00c7b43de91cab](http://hostingkartinok.com/show-image.php?id=184bf3a4e87104473b00c7b43de91cab)
[http://hostingkartinok.com/show-image.php?id=5cbeedbcbd6703b3ef3946d6e6b9524f](http://hostingkartinok.com/show-image.php?id=5cbeedbcbd6703b3ef3946d6e6b9524f)
[http://hostingkartinok.com/show-image.php?id=fdfe1715b59b2345d6f78045c501213b](http://hostingkartinok.com/show-image.php?id=fdfe1715b59b2345d6f78045c501213b)

---

### Post by ajgreeny on 2014-09-22
As you are showing an extended partition on the disk the system must be using the old legacy BIOS, not UEFI.
You seem to have plenty of unused space available in /dev/sda5, so I wonder why you were trying to resize /dev/sda2.

The simplest way, I think is to shrink the partition /dev/sda5 using Windows own disk-management utility, or if it just a data partition and not a windows OS partition, using gparted from a live system (DVD or USB, it does not matter) by grabbing the right hand edge of sda5 and pulling it to the left to make unallocated space at the far right end of the disk.

As a general rule, it is much safer and faster to shrink a partition by grabbing the right hand end and not the left hand end as some of the bootloader files particularly of windows, may depend on the start of the partition remaining constant, and if you move the start of a Windows OS partition it may refuse to boot again.  Perhaps this was the reason for your fixparts requirement?

---

### Post by oldfred on 2014-09-23
After you have resized with ajgreeny's suggestions only use Something Else to install. I do prefer to create partitions for Ubuntu with gparted in advance, but you still have to use Something Else to choose which partition is / and which is swap and which is /home and formats, etc. You then use the change instead of + button.

Several similar examples of Something else installs.
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

