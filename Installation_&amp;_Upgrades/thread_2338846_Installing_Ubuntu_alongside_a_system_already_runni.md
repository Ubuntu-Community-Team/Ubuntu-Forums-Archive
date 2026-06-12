---
title: "Installing Ubuntu alongside a system already running Windows 7 and Arch Linux"
date: 2016-10-02
forum: Installation &amp; Upgrades
---

### Post by sidrocks123 on 2016-10-02
Currently, I am running a dual-boot setup which consists of Windows 7, and Apricity OS, which is a Desktop Environment for Arch Linux.
I would like to run a triple-boot setup, which consists of Win 7, Apricity OS and Ubuntu.
How would I begin doing this?
I already have a Ubuntu 16.04 ISO file. 
Here is my current setup:
     [IMG]http://i.imgur.com/ReTu8n5.png[/IMG]
Any help would be greatly appreciated.

---

### Post by Mark Phelps on 2016-10-02
Well, you've got a problem -- presuming this is an MBR/BIOS system not GPT/UEFI system -- as you're only allowed a maximum of 4 upper-level partitions, and you already have that limit.

Generally, what you do when adding Linux to such a system, is create an Extended partition, and then create Logical partitions inside that -- as you can have a large number of Logical partitions at that point.

But since you don't have an Extended partition, that is a problem -- as you can't convert a Logical partition to an Extended partition.

What MIGHT work is the following:
1) Boot from Linux CD/DVD/USB (can't be using the disk when doing these steps)
2) Copy sda3 onto an external media -- drive or USB stick
3) Remove sda3
4) Recreate sda3 as Extended Partition
5) Recreate new Logical partition inside Extended partition
6) Copy contents of old sda3 to the new Logical partition
7) Manually edit grub files to point to new Logical partition

---

### Post by oldfred on 2016-10-02
Swap has no data, so easier to delete & recreate.
Not sure about current install, but expect that you would have to edit fstab with new UUID for the new swap.

Little key icons show mounted partitions, you have to use the live installer's version of grub or a grub ISO to edit partitions.

You can then delete swap, You may have to swap off as Ubuntu's live installer typically mounts swap to speed install. Then shrink sda3 and create at least a new / (root) ext4 and swap. You may want a shared data partition and since also Windows use NTFS format for shared data partition.

Then use Something Else to choose(change button) ext4 partition and make it /. If swap already exists it auto finds it. 
       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[URL="http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"]http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation
[/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond) 

[URL="http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"]
[/URL]

---

