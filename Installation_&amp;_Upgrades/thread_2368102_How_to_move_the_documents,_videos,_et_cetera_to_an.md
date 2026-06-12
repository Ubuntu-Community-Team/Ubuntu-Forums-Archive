---
title: "How to move the documents, videos, et cetera to another folder / Ubuntu 17.04 + NTFS"
date: 2017-08-07
forum: Installation &amp; Upgrades
---

### Post by user_of_gnomes on 2017-08-07
Under Windows I can point the libraries to another folder by right clicking on the relevant folders, clicking properties and then changing the location under the location tab. How would I go about doing so under Ubuntu? 

I have a dual boot and I managed to share my Firefox and Thunderbird profile but I don't know how to relocate the personal folders. I'd like for them to point to the folders I created on my secondary hard drive so that Windows and Linux can both use the same folders. NTFS-3G seems stable enough nowadays.

I can't find any information on it on-line, no clue what keywords to query for.

Thanks

---

### Post by ajgreeny on 2017-08-07
It will probably be easiest for you to create a new shared partition using NTFS if you don't already have such a partition available.  Windows will automatically find that and the files within it; Ubuntu will need to have the NTFS partition mounted automatically at boot by adding a line to /etc/fstab which we can help you with if necessary.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Once the partition is mounted you can make symbolic links from the folders in the NTFS partition to the appropriately named folders in your Ubuntu home.

Show us your current partitions with command ```
sudo fdisk -l
``` and we may be able to help you more.  With luck you may not need to actually move any of your files around, but that will depend very much on the availability of space in existing partitions, and exactly what you are hoping for.

---

### Post by user_of_gnomes on 2017-08-08
Thanks for the reply! I have already created a shared NTFS partition. It also auto-mounted through the fstab-file. 

```

# Automount NTFS 
UUID=22DA3CDFDA3CB141 /media/gebruiker/22DA3CDFDA3CB1411 ntfs-3g defaults,auto 0 2 
```

I couldn't get the garbage bin to work yet, though. Seems rather complex to get that to function on an NTFS partition or maybe I'm mounting it wrong.

I have two drives: One SSD and one HDD. Windows 7 and Ubuntu reside on the former and the NTFS partition (plus swap and /var) reside on the HDD, here's the output:

```
Disk /dev/sda: 223,6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xc47211c0

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 225282047 225075200 107,3G  7 HPFS/NTFS/exFAT
/dev/sda3       225284094 468860927 243576834 116,2G  5 Extended
/dev/sda5       225284096 227282943   1998848   976M 83 Linux
/dev/sda6       227284992 468860927 241575936 115,2G 83 Linux

Partition 3 does not start on physical sector boundary.


Disk /dev/sdb: 596,2 GiB, 640135028736 bytes, 1250263728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf98d6e74

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdb1             2048 1225256959 1225254912 584,3G  7 HPFS/NTFS/exFAT
/dev/sdb2       1225259006 1250263039   25004034  11,9G  5 Extended
/dev/sdb5       1225259008 1233850367    8591360   4,1G 83 Linux
/dev/sdb6       1233852416 1250263039   16410624   7,8G 82 Linux swap / Solaris

```

So all I'd now is create a symbolic link in the Ubuntu documents, videos and other folders? I've kind of been trying to avoid the subject of links because they make no sense to me on a Linux system.

---

### Post by ajgreeny on 2017-08-08
Here's an example of how to make a symbolic link from the documents folder on the NTFS disk or partition.
It doesn't matter which disk or where the folder is, all you need is the mountpoint of the partition.

First remove the current Documents folder in your home then run command
```
ln -s /media/gebruiker/22DA3CDFDA3CB1411/Documents /home/gebruiker/Documents
```This assumes the documents folder in the NTFS partition is called **Documents**; if it is **documents** or something else just edit my command. 
Now all the documents in the NTFS partition will appear to be sitting in the Documents folder in your Ubuntu home.

Repeat for all other usual home folders.

---

### Post by user_of_gnomes on 2017-08-13
Hey, that is a really neat solution! Thanks!

---

