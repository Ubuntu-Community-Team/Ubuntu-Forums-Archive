---
title: "Request advice 16.04 install/SSD/HDD:  disk mounts as removable"
date: 2016-05-06
forum: Installation &amp; Upgrades
---

### Post by m9ke2 on 2016-05-06
I am doing a fresh install on a newly built computer I am booting from an SSD, but having issues with the way my second disk (conventional HDD)  is mounting.  

I am not sure if this problem is because one of my disks is an SSD and the other a conventional HDD, or something wrong with the default partitions set up by the installer, or a BIOS setting.  Or something else...

I would greatly appreciate some help in figuring this out!

Results i am seeing after  Xubuntu install using installer defaults:
========================================
Computer starts and runs fine apparently
HDD icon  shows up on the desktop Unmounted.  Right-click > Mount works fine
HDD mount:  /media/my user name


So what's the problem?
===============
The conventional HDD is mounting the HDD on /media .  In the past I have seen these disks mount at /dev
The conventional HDD is an internal disk, which I will never want to eject from the computer.
Something appears to be misisng in my fstab (pasted below). 

i am installing Xbuntu on a new build I just finished.  There are no apps or data, so it's easy to reinstall.

Relevant system info:
==============
The SATA config in the BIOS has all SATA ports set to AHCI
Motherboard:  ASUS M5A99X EVO V2 (UEFI BIOS)
SSD:  Crucial BX-100 250 GB
HDD: Western Digital 2TB
CD burner:  ASUS
Graphics card ASUS GEForce GTX 960 (nvidia chipset)

Here is my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=5fa118c6-0d0d-4987-b0d9-a3ff8b673ad9 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=36C4-3FB7  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=d3554151-90ca-4cfd-828d-e86f48f749f3 none            swap    sw              0       0
```



Can you offer any guidance?

---

### Post by oldfred on 2016-05-06
If an internal disk, you want to mount partition(s) with fstab that you regularly use.
And other partitions,  set labels so you know what they are. I try to remember to label all partitions when partitioning, but reformatting or reinstalling a test install overwrites label and I usually use Disks or perhaps command line to label partition.

Post this:
sudo parted -l
       sudo blkid -c /dev/null -o list 

If you want to read ahead:
      
 [URL="https://help.ubuntu.com/community/Fstab"]https://help.ubuntu.com/community/Fstab
[/URL]
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. 

With my SSD & hard drive, I use smaller / (root) partitions, so I can have several on SSD, and then have test installs, large data partition, and several other partitions. But I link data partition folders back into /home, so my /home is tiny.

If a newer user often easier to just have /home on HDD. With data partition you have to format partition, create mount point, set ownership & permissions, & edit fstab. Not all that difficult, but can be an issue is not used to using Ubuntu.

If using UEFI be sure to partition HDD with gpt. And often best to have ESP & bios_grub partitions, so drive could be used later as boot drive, even if not planned now. Difficult to add those partitions when drive has lots of data.

 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413) 

[URL="https://help.ubuntu.com/community/Fstab"]
[/URL]

---

### Post by m9ke2 on 2016-05-06
Hi oldfred,  thanks for your post.  here are the two posts you requested:

First one:
```
m9ke@shadowbee:~/Desktop$ sudo parted -l
[sudo] password for m9ke:  
Model: ATA CT250BX100SSD1 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system     Name                  Flags
 1      1049kB  538MB  537MB   fat32           EFI System Partition  boot, esp
 2      538MB   233GB  232GB   ext4
 3      233GB   250GB  17.1GB  linux-swap(v1)

Model: ATA WDC WD2003FZEX-0 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4
```

Second one:

```
m9ke@shadowbee:~/Desktop$ sudo blkid -c/dev/null -o list
[sudo] password for m9ke: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  vfat             /boot/efi      36C4-3FB7
/dev/sda2  ext4             /              5fa118c6-0d0d-4987-b0d9-a3ff8b673ad9
/dev/sda3  swap             [SWAP]         d3554151-90ca-4cfd-828d-e86f48f749f3
/dev/sdb1  ext4             (not mounted)  3c381d35-23e1-41b8-b2e4-9541cf7c1757
m9ke@shadowbee:~/Desktop$
```

---

### Post by Dennis N on 2016-05-06
Here's a couple of suggestions:

I would change the partition table to GPT the 2nd drive while it is new. It is a better type of partitioning. Your SSD is already GPT. This will also allow more Linux OS to be installed there at some point, which will multiboot with the SSD. Then you should create an EFI system partition, at least one ext4 partition on it so it can be mounted 

The setup here is similar (but a smaller HDD): a 250 gB SSD, and a 500 gB HD.  At present, my HDD is used for data only. 

To get the HDD to automount on startup, I made this entry at the bottom of /etc/fstab of the OS that is booting. First line is an optional comment.

```

# Label=Common-Files at /dev/sdb2
UUID=8395cc9b-002c-4af5-9c49-e5908e4ede74 /mnt/Common-Files ext4 defaults 0 2

```

The last line mounts my HDD partition at /mnt/Common-Files on the booting OS. You can choose another name other than "Common-Files", of course.

You get the UUID with the command **[FONT=Courier New]sudo blkid[/FONT]** and look for the UUID of the partition you want to mount on sdb.

Once the correct line is added to /etc/fstab and saved, just reboot and it will be mounted.

If it's for your data storage, you need to change owner and group of the new file system before you can store stuff there. If it's for an OS installation, don't do this.

```
sudo chown -R user:user /mnt/Common-Files
``` 

Replace user with your user name, and /mnt/Common-Files with the correct mount folder.

---

### Post by m9ke2 on 2016-05-06
Thank you Dennis N.   Looks like i need to figure out what GTP is!  Looking into that now...

---

### Post by Dennis N on 2016-05-06
> **m9ke2 said:**
> Thank you Dennis N.   Looks like i need to figure out what GTP is!  Looking into that now...

You're welcome. If you need any further help, post again. gparted will take care of making the GPT partition table and partitions. You can conveniently run it from your new Xubuntu installation to work on the other drive - no live cd needed. you need to install gparted. 

Select the HDD drive in the drive selector (upper right)
Device > Create Partition Table > (choose GPT)

---

### Post by m9ke2 on 2016-05-06
Thanks once again Dennis N. That worked--my filesystem is no longer behaving like removable media.

 But my HDD is not showing up in my fstab and Home is on the SSD not the HDD. I am pretty sure i messed something up when previously trying to fix this.

It will be quicker to reinstall Xubuntu than to try to troubleshoot all that i had previously done.

I will start in the BIOS to make sure all that is good, and then need to use the "Do Something Else" part of the installer.and could definitely use some help with those settings, if you are up for it.

---

### Post by oldfred on 2016-05-06
Your partitions are also large.
My install of Ubuntu 

```
fred@Asusz97:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        24G  7.9G   15G  35% /
/dev/sda1       500M   21M  479M   5% /boot/efi
/dev/sdb4       385G  104G  262G  29% /mnt/data
/dev/sdc3        14G  4.4G  8.4G  35% /media/fred/sys32
/dev/sdc4        15G   13G  1.3G  91% /media/fred/data32
/dev/sda5       4.7G  3.3G  1.2G  74% /media/fred/iso_ssd
```

Note that I am only using 8GB of my 24GB / (root) partition. But all data normally in /home is in my /mnt/data partition. sdc is a flash drive with another bare install for emergency boot and some data backup.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by m9ke2 on 2016-05-06
Thanks oldfred.  
Starting with the BIOS I have 6 SATA ports.  Ports 1-4 are set to AHCI.  Ports 5 and 6 are set to IDE.  
My SSD is connected to one of the ports set to AHCI.   
My HDD is connected to one of the ports set to IDE. 
There are also SATA ESP enabled/disabled toggles for ports 1-4.  
I had to mess with these SATA ESP settings in order to get the SSD on AHCI and the HDD on IDE
Do these settings look okay?

---

### Post by Dennis N on 2016-05-06
> But my HDD is not showing up in my fstab...
Did you mean in your file manager?

> Home is on the SSD not the HDD
Unless you specify the file system of another partition to mount for you Home folder in /etc/fstab, it will be on the same partition as /.

I can't say about your ports - On my system, I just plugged the drive cables into SATA1 and SATA2 and both are AHCI.

---

### Post by oldfred on 2016-05-06
IDE is really only for very old drives. That is just an old compatibility setting.
You really should be use AHCI for all drives. 
And best to have in port order. I have skipped a port and my flash drive was sdf when plugged in, but on reboot it becomes sdb and every other drive changes up a letter. 
And if other ports are Asmedia that can be a problem, use only the Intel ports.

---

### Post by m9ke2 on 2016-05-07
Thanks oldfred and Dennis N.  I have figured out my BIOS settings and done a fresh install.  

All is still not exactly right with my fstab.  I am going to mark this thread closed and open a new one for my fstab.

Thanks again for helping me get to this point.

---

