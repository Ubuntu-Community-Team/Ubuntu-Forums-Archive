---
title: "Moving Ubuntu home folder to same place as windows My Documents"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by TheVegen on 2011-05-28
I have tried this about 4 times now and each time had Ubuntu's kernel panic and had to start over so this time I am going to ask for help to see what I am doing wrong. 

I have been using the document _[PartitionHomeMoving](https://help.ubuntu.com/community/Partitioning/Home/Moving#Setup Partitions)_ to help me with this.  

I am running a duel boot system with Ubuntu 11.04 Natty Narwal with gnome 2.32.1 and Windows 7. I have three partitions 1 40 gig for Windows one 30 gig for Ubuntu and about 500 gigs for a shared partition. 

Here is what my fdisk report looks like
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd3aa3374

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        5232    41922616    7  HPFS/NTFS
/dev/sda3            5233        9150    31463303    7  HPFS/NTFS
/dev/sda4            9151       77825   551631937+   7  HPFS/NTFS

```

/dev/sda4 is the shared drive that I want my home folder to mapped to

I have successfully remapped my windows My Documents folder to the shared drive located in Users/Kevin on the shared partition. 

I have used _[pysdm](http://pysdm.sourceforge.net/)_ to auto mount /dev/sda4 to media/Shared 

Here is a look at my fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                          /proc          proc  nodev,noexec,nosuid     0  0  
/host/ubuntu/disks/root.disk  /              ext4  loop,errors=remount-ro  0  1  
/host/ubuntu/disks/swap.disk  none           swap  loop,sw                 0  0  
/dev/sda4                     /media/Shared  ntfs  defaults                0  0
```

Do I need to add “,errors=remount-ro” after defaults? And what do the last two numbers mean I know I can have the last one as 1 or 0 and it works fine. 

Now I need to remap my Ubuntu home folder from the default location in my Ubuntu partition under home/kevin to the same place the windows one is now at media/Shared/Users/Kevin

Will having capital letter in the file path be an issue as I know Ubuntu will not let me install the home folder that has a capital letter in it. Will have have to rename that folder or any of the other folders in the file path such as the Users and Shared? Would it be better to have both operating systems go to home/kevin on the shared partition? 

Then there is the whole UUID thing. I know how to find it here is a copy of mine. 
```
/dev/loop0: UUID="6629384f-9628-4bb7-ad9a-2566fa68a341" TYPE="ext4" 
/dev/sda1: LABEL="System Reserved" UUID="B6CA556ACA5527BF" TYPE="ntfs" 
/dev/sda2: UUID="DEE664EAE664C47D" TYPE="ntfs" 
/dev/sda3: LABEL="ubuntu" UUID="5A1EF5BA1EF58EEF" TYPE="ntfs" 
/dev/sda4: LABEL="Shared" UUID="22C4CA3FC4CA1547" TYPE="ntfs"
```

when I change my fstab what do I change it to? I know in the help file it has the location changed twice first to media/home then to just home. In my case I know I will have to be putting something different there but I am not sure what. 

Thank you for the help I have have been at this for two days now.

---

### Post by coffeecat on 2011-05-28
There are two fundamental issues which mean that you won't be able to do what you are trying to do. Or at least not in the way you are trying to.

First:

> **TheVegen said:**
> I am running a duel boot system with Ubuntu 11.04 Natty Narwal with gnome 2.32.1 and Windows 7. I have three partitions 1 40 gig for Windows one 30 gig for Ubuntu and about 500 gigs for a shared partition. 

Here is what my fdisk report looks like
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd3aa3374

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        5232    41922616    7  HPFS/NTFS
/dev/sda3            5233        9150    31463303    7  HPFS/NTFS
/dev/sda4            9151       77825   551631937+   7  HPFS/NTFS

```

No, you do not have a conventional dual-boot system; you have a wubi system. The fact that you only have NTFS partitions (a Microsoft filesystem) is the giveaway. If you had a conventional dual-boot system you would have one or more partitions formatted with a Linux filesystem. Your 30GB "partition" for Ubuntu is sda3 - or more correctly it is inside sda3. Partition sda3 would appear as D: or E: in Windows, or whatever drive letter has been assigned. If you examine it in Windows, you will see a folder called "ubuntu". Let's say for illustration purposes that that drive is D:, then you will find, in Windows, a file D:\ubuntu\disks\root.disk. The file root.disk will be about 30G in size and that is the virtual Ubuntu partition. The file itself is formatted with a Linux filesystem and that is where your Ubuntu system runs from.

However, that's not the main problem. Your Ubuntu home folder contains, apart from your personal files, a large number of hidden configuration files and folders, some of which require special permissions. Those are Linux permissions which are different from Windows ones, and which Windows filesystems do not support. It is not possible to have a Linux home folder and contents on a NTFS partition. The reason that your home folder works in wubi inside a NTFS partition is that as far as the system is concerned, it's not in a NTFS filesystem - remember what I said about the root.disk file being a virtual partition formatted with a Linux filesystem.

The best you can do is to keep your shared files on the shared NTFS partition and set up symlinks (equivalent to windows shortcuts) between the NTFS partition and your home folder. In fact that is what many people do who have a conventional dual-boot with Windows and a shared NTFS data partition.

---

