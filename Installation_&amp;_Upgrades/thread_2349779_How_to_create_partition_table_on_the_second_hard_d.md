---
title: "How to create partition table on the second hard drive"
date: 2017-01-18
forum: Installation &amp; Upgrades
---

### Post by tevang2 on 2017-01-18
Greetings,

My laptop is Asus ROG GL552VW and you can see its specifications here:

[http://www.ultrabookreview.com/8975-asus-rog-gl552vw-review/#a1](http://www.ultrabookreview.com/8975-asus-rog-gl552vw-review/#a1)

It has two hard drives, /dev/sda is HDD 1 TB big and /dev/sdb is SSD 234 GB big. Because SSD is faster I thought that it would be wiser to install  the operationg system on the second hard drive. However, the installer does not let me to create a partition table on /dev/sdb. Therefore I created the partition table on /dev/sda and mounted /dev/sdb to /opt. Is it possible to create the partition table on the second hard drive?

---

### Post by TheFu on 2017-01-18
gparted.

---

### Post by tevang2 on 2017-01-18
Have you done this before? Because I booted Ubuntu live from a USB stick by I couldn't do it even with Gparted.

---

### Post by laurent85 on 2017-01-18
Open a terminal and post the command results :
```
sudo parted --list
sudo lsblk -o name,size,fstype,label,uuid,mountpoint
```

---

### Post by TheFu on 2017-01-18
> **tevang2 said:**
> Have you done this before? Because I booted Ubuntu live from a USB stick by I couldn't do it even with Gparted.

many times.  

If the disk isn't recognized, look for other HW issues or incompatibilities.  I'd search for the specific model + "ubuntu" - if that didn't find anything, relax to "linux."  If nothing is found, look for disk controller issues for the specific model.

---

### Post by tevang2 on 2017-01-18
> **laurent85 said:**
> Open a terminal and post the command results :
```
sudo parted --list
sudo lsblk -o name,size,fstype,label,uuid,mountpoint
```

I booted from Ubuntu live CD and issued the commands you listed. Below is the output:


```
ubuntu@ubuntu:~$ sudo parted --list
Model: ATA HGST HTS541010A9 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  500MB   499MB   fat32                 boot, esp
 2      500MB   32.5GB  32.0GB  linux-swap(v1)
 3      32.5GB  82.5GB  50.0GB  ext4
 4      82.5GB  1000GB  918GB   ext4


Model: ATA HFS256G39MND-230 (scsi)
Disk /dev/sdb: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  256GB  256GB  ext4


Model: General USB Flash Disk (scsi)
Disk /dev/sdc: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start  End  Size  File system  Name  Flags


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: HL-DT-ST DVDRAM GUE1N (scsi)                                       
Disk /dev/sr0: 1594MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      1582MB  1584MB  2458kB               EFI
```


```

ubuntu@ubuntu:~$ sudo lsblk -o name,size,fstype,label,uuid,mountpoint
NAME     SIZE FSTYPE  LABEL      UUID                                 MOUNTPOINT
sdb    238.5G ext4               6560d5f4-6e59-4dda-a19f-c60af34b20c1 
sr0      1.5G iso9660 Ubuntu 16.10 amd64
2016-10-12-21-27-43-00               /media/ubu
loop0    1.4G squashf                                                 /rofs
sdc     29.8G iso9660 Ubuntu 16.10 amd64
2016-10-12-21-27-43-00               /cdrom
sda    931.5G                                                         
&#9500;&#9472;sda4 854.7G ext4               e6c918b5-bfb9-4fef-a30d-11ec6703f7c5 
&#9500;&#9472;sda2  29.8G swap               f31ac313-463b-4f21-937a-338ee18c3312 [SWAP]
&#9500;&#9472;sda3  46.6G ext4               9b6c5298-4420-42f2-bae2-be3a4b1f5321 
&#9492;&#9472;sda1   476M vfat               AAA1-E1D5  

```

---

### Post by TheFu on 2017-01-18
Please use "code tags." Too hard to read otherwise.

---

### Post by oldfred on 2017-01-18
You have sdb mounted as a loop device.
But then it is unpartitioned, which is not advised.

Is SSD the new NVMe type?
If so you need gparted to be at least version 24. Current directly downloaded is 27 (a couple of weeks ago).

Have you updated Asus' UEFI to latest version?
Some have reported that helps.

Several Asus models need pci=nomsi boot parameter.
 Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

You can test boot parameter as you boot like adding the nomodeset parameter. Then it it works, you can permanently add it in grub's configuration file.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu & after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 


This user used a lot of parameters, not sure all now required with newer Ubuntu version.

 ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)

---

### Post by laurent85 on 2017-01-18
Issue the following command _only if you don't need to beforehand backup valuable data located on ssd drive sdb,_ that will create a new gpt partition table on sdb,_ all data will be lost on ssd drive sdb_, copy paste following command into terminal:

```
sudo sgdisk -Zo /dev/sdb
```

---

### Post by tevang2 on 2017-01-18
So the trick was "sudo sgdisk -Zo /dev/sdb". After than I partitioned sdb and installed the boot loader on the second hard drive. The first hard drive was mounted to /opt. After the installation I rebooted but there was no boot menu, namely Ubuntu started booting immediately. When I was propted for my password and entered the screen did not change, the cursor was moving but nothing else was displayed. Do you think this is because I installed the bootloader on the second hard drive? Is it recommended to install the boot loader on the first hard drive but the whole operating system on the second?

---

### Post by laurent85 on 2017-01-18
generate a boot-info report, boot a live session and open a terminal,

install boot-info:
```

sudo add-apt-repository ppa:yannubuntu/boot-repair
apt update
apt install -y boot-info
```

provide the online link pointing to the report:
```
boot-info
```

---

### Post by TheFu on 2017-01-18
It appears the SSD had a file system put on it before it was partitioned. Don't know how that happened.

There are many cooks here each with different opinions. Please pick one to follow and let us know which you'll use.

If I were doing this, I would wipe the SSD and setup my partitions and reinstall. If it got confused again as to where to place the boot flag and EFI partition, I'd start over and disconnect the drive I didn't want installed onto.  There are good reasons to choose both methods. Just depends on your desire.

---

