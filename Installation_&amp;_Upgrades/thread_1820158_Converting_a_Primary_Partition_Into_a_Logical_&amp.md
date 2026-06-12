---
title: "Converting a Primary Partition Into a Logical &amp; Dual Booting Windows &amp; Ubuntu"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by Sache on 2011-08-07
Hi, I need help with dual booting Windows 7 and Ubuntu on a HP dv6  laptop. The problem is that there are already four primary partitions  installed on the harddrive, so I can't create an extended partition to  put my logical partitions in.

200MB - System
572GB - Windows
23.5GB - Recovery
100MB - HP Tools

From  other posts that have expressed similiar concern I have concluded that  most people just wants to backup and erase HP Tools. Though I hate HPs  built in stuff and would just like to reinstall Windows, I'm afraid that  I would lose important drivers, and would have a hard time updating  them after reinstallation. So I would not like to erase HP Tools but is  it possible to convert the Windows partition to a logical so I can  create more logical partitions? I found a program, Partition Wizard,  that should be able to do it but I don't know for sure and don't want to  try out blindly.

I would also gladly hear what you have to say about the setup I'm planning to use.

/dev/sda1 ntfs 200 MB - System
/dev/sda2 extended
/dev/sda3 ntfs 23.5 GB - Recovery
/dev/sda4 fat32 100 MB - HP Tools
/dev/sda5 ntfs 150 GB - Windows
/dev/sda6 ext4 50 GB - Ubuntu
/dev/sde7 swap 8 GB - Swap
/dev/sda8 ntfs 364 GB - Share

The  Share will be used for accessing all my data from both Windows and  Ubuntu. It is going to be backed up to a portable drive using Déjà Dup.

At  first I was going to have root and home separate but one of my friends,  who is an avid linux user, thought it was not necessary since I was  going to have my stuff in Share anyway.

Thanks in advance!

---

### Post by oldfred on 2011-08-07
I would not move a windows install to a logical partition. It would work since you are booting from a primary, but if you ever damaged the boot/recovery partition, you could not easily then repair the main partition to boot. We have had many users delete the sda1 boot/recovery and then could just fix sda2 to boot. Windows will not directly boot from a logical partition.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

