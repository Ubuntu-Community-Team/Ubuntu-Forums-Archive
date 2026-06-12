---
title: "Partitioning problems for a dual-boot netbook installation"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by davidbr on 2010-12-31
Hello,

I got an Asus EEE PC 1015PEM netbook with 2GB RAM.

I wish to dual boot ubuntu (desktop edition; don't like netbook edition) and Windows 7. I also want a separate partiton for all my data, that would be accessible from both ubuntu and Windows (so I guess ntfs is the way to go).

After some reading on the web (mainly this [article]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")), I figured this might be a reasonable partitioning scheme:

Windows partition 30GB ntfs
Ubuntu partition 27GB ext4
Swap 3GB
Data ~180GB ntfs

This is what I did:

1. Boot from ubuntu live CD (USB).
2. Run Gpart (after updating it; it first crashed, possibly due to some known problem with some USB storage devices).
3. Delete all partitions so I have one big chunk of unallocated space.
4. Create an unformatted partition of size 30GB, starting at 30GB. This will be used for Ubuntu. Starting from 30GB ensures there are some 30GB of unallocated space at the beginning of the disk, that will be used for Windows later.
5. Create an ntfs partition on the remaining space at the end of the disk (some 180GB).
6. Boot from Windows DVD-on-USB and install Windows on the 30GB unallocated space at the beginning of the disk. This worked fine.
7. Boot from ubuntu live CD (USB). Installation only offered manual partitioning or deleting the entire HD. It didn't offer installing alongside another OS (should it offer that option?). Chose manual. I wanted to divide the 30GB partition (unformatted yet) to some 27GB ext4 mounted to / and 3GB swap. After doing the first step, the remaining space was "unusable". I couldn't solve this. So I tried deleting also the ~180GB ntfs data partition. At this stage I only have two ntfs partitions (100MB + 30GB; the firs small one is automatically created by windows). I allocated 30GB ext4 mounted to / and 3 GB for swap. As for the remaining space - I couldn't allocate it as ntfs. ntfs simply did not appear in the list of types. So I left it unallocated, thinking I will allocate this space post installation.
7. After the installation, I now see I can't use allocate the unallocated spaces since the "disk already contains the maximal number of partitions"...

What should I do?

Thanks!

---

### Post by Quackers on 2010-12-31
Did you create all the partitions as Primary?
Windows needs a primary partition but Linux doesn't. You can have all Linux partitions withi an extended partition.
The maximum number of primary partitions on any single hard drive is 4. You can't have 4 primaries and another logical partition. 
If you already have 4 primary partitions you will need to delete one and replace it with an extended partition, which can then hold many more logical partitions.
To be honest, what I would do is leave Windows partitions as primary and leave the rest as "unallocated space" then during the installation select the manual option and make the required partitions for Ubuntu myself - using an extended partition to hold the other logical partitions.

---

### Post by ajgreeny on 2010-12-31
I largely agree with Quackers, but would add the point that it will make your life a little easier if you install Windows first.  If you install it after Ubuntu you will have to restore the grub2 bootloader, as Windows will put its own bootloader on the disk in place of grub.

Otherwise all is as Quackers says, except:-

1.  Install Windows to the first 30GB partition, premade, and formatted if you wish to ntfs.

2.  Check that Windows will boot.

3.  Install Ubuntu from the live CD/USB.

That gives you a chance to make the logical Ubuntu partitions and the data partition before installing, from the live CD/USB using gparted, and in my opinion simplifies the process of installing, as you can choose "Manual partitioning" and then point to each partition in turn for / and swap.  You can make the ntfs data partition at the same time as you make the Ubuntu ones, but you will have to set it to mount as a shared partition later, after booting Ubuntu for the first time.

---

### Post by davidbr on 2010-12-31
Thanks Quackers and ajgreeny. I have successfully created the desired layout. Could you just explain how should I configure (mount?) the shared ntfs partition so it would be accessible from both Windows and ubuntu?

Thanks

---

### Post by Quackers on 2010-12-31
By way of bumping this thread, I would just say that I don't have a shared partition so I can't offer any advice on that point. I'm sure somebody will be along who can help.

---

### Post by ajgreeny on 2010-12-31
You can install ntfs-config and use that to ensure the partition is mounted at boot time, and has read/write permissions on its mount point.

You can then use the partition by making sure all your data files from Open Office, GIMP, etc etc are directed to the appropriate folder in that partition, or you can make links from your home to the folders in that data partition.  I would probably just do it all direct, if it were me, and not bother about links, but once you have it setup, it may just be less confusing for you to have everything apparently in your home, even if it actually resides in the data partition.

Come back again if you want more details on this.

---

### Post by zaikreign on 2010-12-31
This is how I layout my disk partitions using Windows 7 and Ubuntu 10.04 Netbook:

1st: 70GB - Windows 7 (sda1)
2nd: 150GB - Shared files (sda2)
3rd: 23GB - Linux (sda3)
4th: 2GB - swap (sda4)

I keep them all Primary Partition, as the disk only allows 4 primary partitions. I (1st) install windows on an empty drive, and (2nd) create another partition after it for my files. Install ubuntu, creating new partiotions for (3rd) linux and (4th) swap. After which, you can edit "/etc/fstab" to add your 2 previous partitions (sda1 & sda2).

You can do it by the terminal:
"sudo gedit /etc/fstab"
 -> enter your password and add this line
"/dev/sda1     /windows     auto     ro    0      0" 
 -> using "ro" (read only) keeps your windows file system intact in case you accidentally messes files within it. and
"/dev/sda2     /files           auto     user,defaults      0     0"
 -> defaults read/write attribute
 -> next is by creating the mount points for /windows and /files
"sudo mkdir /windows /files"
 -> finally to mount the volumes, hit
"sudo mount -a"

You can then open the mount points in nautilus and bookmark it so it will become easily accessible..

---

