---
title: "Dual Boot"
date: 2014-11-24
forum: Installation &amp; Upgrades
---

### Post by aman4 on 2014-11-24
I Need to Dual Boot Windows 7 and Ubuntu . My win 7 Is Installed On C Drive and I want to install Ubuntu on E  Drive Is this Possible?
And Will Data Be Preserved On My E Drive Where I will Install Ubuntu Or I need to Delete Data On Drive E and install Ubuntu?

---

### Post by sudodus on 2014-11-24
If you give us more information, it will be easier to give relevant advice.

- Is your computer running in BIOS or UEFI mode?

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It is also important to find out if C: and E: are on the same or on different physical units. Linux makes a difference between drives (physical units like hard disk drives, pendrives, SSDs ...) and partitions. C: and E: are considered partitions in linux terms. They could be on the same drive or on different drives (hard disk drives).

-o-

You need to ***backup (make a copy of) your personal files*** from the target partition E: to another partition, for example on an external drive (or to C:, if there is enough space).

Ubuntu needs another file system (not NTFS, which I guess you have now in E:). This will be done by the installer, or you can do it manually before the installation.

***To do things in a safe way, please backup also Windows or at least your personal files in C: too***, because installing operating systems is risky, and you might overwrite or destroy the contents of the drive by mistake, or by an electric power outage during the installation.[URL="http://ubuntuforums.org/showthread.php?t=2230389"]

Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

And when you are installing, select ***Something else*** at the partitioning window, all other options are risky, and might overwrite your current Windows.

See also these links, and links from them

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[URL="http://ubuntuforums.org/showthread.php?t=2147295"]
UEFI Installing - Tips[/URL]

[booting with UEFI]("https://help.ubuntu.com/community/UEFI")

---

### Post by yancek on 2014-11-24
If you have data from your windows installation on what you refer to as your 'E' drive it will almost certainly be overwritten when you install Ubuntu.  In addition to the advice above it would be a good idea to read some tutorials on installing Ubuntu such as the one below which gives you some information on Linux naming conventions for drives/partitions at the top of the page:

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by aman4 on 2014-11-24
Its bios

- Brand name and model  Dell Inspiron N5010
- CPU  2.40Ghz-2.39Ghz
- RAM (size) 4gb
- graphics chip/card  N/A
- wifi chip/card Dont Know

Okay After Installing Will I Be Able TO Move File To Drive E?

---

### Post by Impavidus on 2014-11-24
Windows labels all partitions that it finds on your system and understands as "Drive C" (the one on which it is installed), "Drive D", Drive E" etc. If you install Ubuntu on the partition now known as "Drive E", Windows will no longer understand it and won't call it "Drive E" any longer. Only Ubuntu will have access to that space. Ubuntu can access the Windows partitions, so you can move files to the Ubuntu partition, but Windows won't be able to see them there.

And read those links in the posts above.

---

### Post by aman4 on 2014-11-24
Ok can some1 help me i have made E drive Free completely and have 40gb i am not able to understand what they do like sda1,2 etc someting home

---

### Post by sudodus on 2014-11-24
> **aman4 said:**
> Its bios

- Brand name and model  Dell Inspiron N5010
- CPU  2.40Ghz-2.39Ghz
- RAM (size) 4gb
- graphics chip/card  N/A
- wifi chip/card Dont Know

Okay After Installing Will I Be Able TO Move File To Drive E?

This computer should work well with any of the current Ubuntu flavours (including standard Ubuntu). I think (but I am not sure) that Windows is installed in UEFI mode, which means that you should read carefully the links above about UEFI. Anyway, you ***must*** backup the data from your current E:, because it will be overwritten. And select ***Something else*** at the partitioning window. (The option ***Install alongside*** is dangerous because of a bug.)

As already described, you can use Ubuntu to move the files back to the disk space that used to be E: but is now Ubuntu's root partition. But Windows won't be able to access data on that partition.

---

### Post by oldfred on 2014-11-24
Post this to see your existing partitions:
sudo parted -l

Most Windows 7 systems use all 4 primary partitions with MBR(msdos). Only a few Windows 7 systems released just before Windows 8 used UEFI with gpt partitioning.  Gpt in effect has no limit on primary partitions. It does have a soft limit of 128 partitions as that is the size of its default partition table, but that can be expanded by the user.

Windows has to boot from a primary partition, but Ubuntu will boot from a logical partition without issue. And you can have an unlimited number of logical partitions, but one primary must be the container for all the logical and is called the extended partition.

---

### Post by nerdtron on 2014-11-24
If your data is important to you. Don't risk installing Lubuntu. 

Any OS you install (same with windows) that messes with partition will have big risks wiping data on disk. Especially when you are not very much familiar with the installation procedures. Backup your data whenever you attempt installing any operating system.

It would be much better if you have an extra hard drive and try to experiment on that one. Once you are comfortable with manual installation then you can try on your original drive.

---

### Post by yancek on 2014-11-24
> Ok can some1 help me i have made E drive Free completely and have 40gb i  am not able to understand what they do like sda1,2 etc someting home 				

If you go to the page below and scroll down to the "Partitioning dictionary" section it will explain the way Linux names drives/partitions.  Pretty much any new system will use sda, sdb and not the hda and hdb mentioned in this article as it is fairly old but still accurate otherwise.  Posting the output of the command suggested above by oldfred will allow someone to give you more specific suggestions.

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by aman4 on 2014-11-24
Ok below i have attached SnapShot of my drives --> [http://snag.gy/81iEH.jpg](http://snag.gy/81iEH.jpg)
I want to installl it on/dev/sda6 but i dont know what to select like someting like ext2,4 / swap area home this process i am not able to get this things even saw many tutorial but don't understand  ? can somone help me please

---

### Post by oldfred on 2014-11-25
You have to delete sda6 as it is NTFS. And if you want a separate /home you have to create 3 partitions / (root) of 20 or 25GB formatted ext4, swap of 2GB, and /home for the rest also ext4.
Since only 43GB total, I might just make one large / (root) and not have the separate /home.

Ignore any references to installing to a second drive or sdb. You still want to install grub2's boot loader to sda, not to any partition.

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

---

