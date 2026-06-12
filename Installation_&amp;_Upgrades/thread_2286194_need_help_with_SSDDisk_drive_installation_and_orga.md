---
title: "need help with SSD/Disk drive installation and organization"
date: 2015-07-10
forum: Installation &amp; Upgrades
---

### Post by Lloydb39 on 2015-07-10
In my next build, I want to use an SSD for Linux and put my data on a large hard drive. Question is, where on which disk will Ubuntu put the software? If I have to designate where, should they be on the SSD with the OS? All on one partition? And roughly how large a drive would I need if everything but data is going to be on it? Can anyone point me to instructions or a tutorial on this if there is one? (I hope this is the right forum and it hasn't been answered. I searched.)

---

### Post by Dennis N on 2015-07-10
Ubuntu's root partition is where Ubuntu will install all the applications you install from the software center or repositories. 

Generally, I allow about 25-30 gB per OS and I don't use separate home partitions. But do use a large separate data partition shared between all the OS installs on the system. I have 6 on here right now.

---

### Post by Dennis N on 2015-07-10
Here are the partitions on this computer so you can see the sizes. Partition 4 on sda is the common data partition.

```
dmn@Sydney:~$ sudo parted -l
[sudo] password for dmn: 
Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32                 boot
 2      538MB   42.5GB  41.9GB  ext4
 3      42.5GB  46.7GB  4194MB  linux-swap(v1)
 4      46.7GB  90.7GB  44.0GB  ext4


Model: ATA WDC WD10EZEX-22B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  211MB   210MB   fat32                 boot
 2      211MB   33.8GB  33.6GB  ext4
 3      33.8GB  38.0GB  4194MB  linux-swap(v1)
 4      38.0GB  58.9GB  21.0GB  ext4
 5      58.9GB  86.2GB  27.3GB  ext4
 6      86.2GB  113GB   27.3GB  ext4
 7      113GB   141GB   27.3GB  ext4

```

---

### Post by oldfred on 2015-07-10
I do the same as Dennis N.

I have / (root) partition of about 25GB including /home. But hidden settings in /home are small. My /home is a bit larger as I use .wine for Picasa so my /home total is about 2GB. And total including /home in my 25GB / is 14GB. I then have large data partition, backup partition, partitions for ISO and other test installs on hard drive.

       One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)

---

### Post by Kale_Freemon on 2015-07-12
I recently redid my Ubuntu install to accommodate a two drive system. Ubuntu itself, and software, are all installed onto the 120GB SSD. However, my /home partition is the 500GB HDD. Works for me. Allows me to have the speed of the SSD without losing the storage space of the HDD.

Honestly, though, it all depends on what you're trying to achieve. Ubuntu tends to work pretty well on small partitions as the other two posters have touched on.

---

