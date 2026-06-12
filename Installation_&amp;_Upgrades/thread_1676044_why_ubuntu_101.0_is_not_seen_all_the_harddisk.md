---
title: "why ubuntu 101.0 is not seen all the harddisk ?"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2011-01-26
I have just installed ubuntu 10.10.
I had about 270Gib available free to install ubuntu 10.10 on, but after the installation I can see only 141Gib ? how can I get the rest of the  free harddisk ?

---

### Post by psusi on 2011-01-26
How are you determining these values?  What is the output of the following commands:

df -h
sudo fdisk -lu

---

### Post by hoboy on 2011-01-26
> **psusi said:**
> How are you determining these values?  What is the output of the following commands:

df -h
sudo fdisk -lu

I think that I understand now what is going on.
I did a partition, windows on c: and I installed ubuntu on the other one called d:, during ubuntu installation i didn't choose use all the partition. when I launch  windows I can see that it still has the haf of the partition so nothing is lost.

---

### Post by Mark Phelps on 2011-01-27
If I understand what you said correctly, you installed Ubuntu using Wubi -- in which case, Ubuntu is installed INSIDE Windows to an already existing NTFS partition.

Make sure you mention Wubi-install in all future posts.  The procedures for fixing any problems with that can be quite different from the traditional its-own-partition installations.

---

### Post by hoboy on 2011-01-27
> **Mark Phelps said:**
> If I understand what you said correctly, you installed Ubuntu using Wubi -- in which case, Ubuntu is installed INSIDE Windows to an already existing NTFS partition.

Make sure you mention Wubi-install in all future posts.  The procedures for fixing any problems with that can be quite different from the traditional its-own-partition installations.

Nop I didn't use wubi.

---

### Post by kansasnoob on 2011-01-27
> **hoboy said:**
> I think that I understand now what is going on.
I did a partition, windows on c: and I installed ubuntu on the other one called d:, **[COLOR="Red"]during ubuntu installation i didn't choose use all the partition.[/COLOR]** when I launch  windows I can see that it still has the haf of the partition so nothing is lost.

With the 10.10 installer that's a very good thing:

[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)

Please post the output of this command:

```
sudo parted -l
```

And also the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you didn't hose Windows count yourself as a winner, slow down, and figure things out :D

---

### Post by hoboy on 2011-01-29
sudo parted -l
[sudo] password for luc: 
Model: ATA WDC WD6400AAKS-0 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      106MB   221GB  221GB   primary   ntfs
 3      221GB   340GB  119GB   primary   ntfs
 4      340GB   640GB  301GB   extended
 5      340GB   628GB  288GB   logical   ext4
 6      628GB   640GB  12,2GB  logical   linux-swap(v1)


:~$ cd Desktop/
:~/Desktop$ ./boot_info_script055.sh
Please use "sudo" or become "root" to run this script.
luc@luc:~/Desktop$ sudo ./boot_info_script055.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Finished. The results are in the file RESULTS.txt located in /home/luc/Desktop
:~/Desktop$

---

### Post by kansasnoob on 2011-01-29
Where do you see only 141GB?

Windows consists of three primary partitions totaling 340GB and Ubuntu consists of two logical partitions totaling 300GB.

I don't see a problem.

---

