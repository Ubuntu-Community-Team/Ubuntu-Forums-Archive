---
title: "Partitioning problems with 14.04 using gparted live, can't shrink partition"
date: 2014-09-12
forum: Installation &amp; Upgrades
---

### Post by pack2 on 2014-09-12
Hello everybody.  I'm trying to dual boot with Ubuntu 14.04 and Kali Linux and I'm having partitioning problems.

I did already do a search but I couldn't find a solution, though there are a lot of similar issues.  I have a Dell Latitude x86 running Ubuntu 14.04.  I did do an install of Kubuntu-Desktop and I think I have a few problems with kde that I'm not sure are relevant.  

I'm trying to repartition my hard drive using gparted live installed on a USB drive and it seems to load fine.  Gparted shows I have three partitions:
/dev/sda1 - Boot
/dev/sda2 - Unnamed 
And it looks like sda2 has sda5 as a sub-partition.  I'm not sure if I'm saying that right so [here's ]("http://imgur.com/a/qB0ot")an album to show what I see.  

So here's the problem, when I click on sda5 and click Resize/Move, I can't change the partition size.  I can't drag the arrows left or right.  I can't type in a different volume size.  I can't do anything. Because this is a live boot, the partition shouldn't be mounted.  I also know that it's not even close to being full (maybe 5GB/146GB) so I feel like it should have room to defragment.

Any ideas?

Thanks in advance for any help,

-P

---

### Post by egeezer on 2014-09-12
sda2 is simply your extended partition, and at the present sda5 occupies the whole partition.  What you can do is delete sda5, then make any number of new partitions in the unallocated (extended partition) space.

---

### Post by pack2 on 2014-09-12
Is that my only option?  I would prefer to not to delete the previous install.

---

### Post by egeezer on 2014-09-12
You can see in your Resize/Move picture that the minimum and maximum sizes are the same.  There will be no permitted size change in sda5 as long as that full lvm is in effect, and it is currently showing as completely used.  I've not used lvm's since about Fedora 13, so I don't see the mount points I'm used to, and I see no way to divide that single partition.  You might do best looking at the the Ubuntu documentation pages

[https://help.ubuntu.com/](https://help.ubuntu.com/)

and doing a search on lvm.  Maybe there is a way to reassign space within the logical volume, which is now the full size of the physical volume.

---

### Post by oldfred on 2014-09-13
I have never used LVM, but some links on more info.
LVM is/was a work around for the 4 primary partition limit, but is a logical overlay over the physical partition.

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
Issues on very large 19TB LVM ext4 64 bit partition
[http://ubuntuforums.org/showthread.php?t=2213785](http://ubuntuforums.org/showthread.php?t=2213785)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by yancek on 2014-09-13
The IBM site below has an explanation of how to resize LVM partitions.  I don't use LVM so much of it is meaningless to me.  Worth reading.

[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

---

### Post by pack2 on 2014-09-13
Okay, so it sounds like LVM isn't the ideal partion file system.  I think I'm going to just reinstall Ubuntu 14.04 but reformat my drive in something besides LVM.  What is the format of choice?  ext4?

---

### Post by oldfred on 2014-09-13
If not ever planning on installing Windows on this drive, I also suggest using gpt as then you do not have the 4 partition limit and have a backup partition table for reliability. If drive may ever be moved to a new system with UEFI include an efi partition at beginning also.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)

---

