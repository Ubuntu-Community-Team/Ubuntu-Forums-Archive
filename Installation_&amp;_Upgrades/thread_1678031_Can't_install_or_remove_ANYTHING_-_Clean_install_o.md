---
title: "Can't install or remove ANYTHING - Clean install of 10.10"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by boopit on 2011-01-29
No matter what it is I'm trying to install, remove, or upgrade, I get the same error. 

InstallArchives() failed

I am running Ubuntu 10.10 off of a flash drive, made using the universal USB isntall from Pendrivelinux. 

What is the point of having Ubuntu 10.10 if I can't install anything? I can't even get my wireless drivers installed; I have to use this painfully ugly USB wireless thing. 

Please help; I really want to use Ubuntu, but it defeats the purpose when I can't use it for anything.

Thanks in advance.

---

### Post by boopit on 2011-01-29
*bump

Anyone? Please?

---

### Post by oldos2er on 2011-01-29
Can you run ```
sudo fdisk -l
``` in a terminal, and post the output here?
And the same with ```
sudo apt-get update
```

---

### Post by boopit on 2011-01-29
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5083d9ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       28310   227188736    7  HPFS/NTFS
/dev/sda3           28310       30389    16698368    7  HPFS/NTFS
/dev/sda4           30389       30402      105656    c  W95 FAT32 (LBA)

Disk /dev/sdb: 4063 MB, 4063232000 bytes
255 heads, 63 sectors/track, 493 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9867cd22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         494     3967968+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(492, 254, 63) logical=(493, 253, 16)
``````
[B]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5083d9ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       28310   227188736    7  HPFS/NTFS
/dev/sda3           28310       30389    16698368    7  HPFS/NTFS
/dev/sda4           30389       30402      105656    c  W95 FAT32 (LBA)

Disk /dev/sdb: 4063 MB, 4063232000 bytes
255 heads, 63 sectors/track, 493 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9867cd22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         494     3967968+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(492, 254, 63) logical=(493, 253, 16)
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en_US
Get:1 http://security.ubuntu.com maverick-security Release.gpg [198B]          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Get:2 http://archive.ubuntu.com maverick Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Get:3 http://security.ubuntu.com maverick-security Release [31.4kB]
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Get:4 http://archive.ubuntu.com maverick-updates Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Get:5 http://archive.ubuntu.com maverick Release [39.8kB]
Get:6 http://security.ubuntu.com maverick-security/main Sources [23.1kB]
Get:7 http://security.ubuntu.com maverick-security/restricted Sources [14B]    
Get:8 http://security.ubuntu.com maverick-security/main i386 Packages [75.0kB] 
Get:9 http://archive.ubuntu.com maverick-updates Release [31.4kB]              
Get:10 http://archive.ubuntu.com maverick/main Sources [829kB]                 
Get:11 http://security.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:12 http://archive.ubuntu.com maverick/restricted Sources [4,370B]          
Get:13 http://archive.ubuntu.com maverick/main i386 Packages [1,492kB]         
Get:14 http://archive.ubuntu.com maverick/restricted i386 Packages [5,992B]    
Get:15 http://archive.ubuntu.com maverick-updates/main Sources [77.9kB]        
Get:16 http://archive.ubuntu.com maverick-updates/restricted Sources [778B]    
Get:17 http://archive.ubuntu.com maverick-updates/main i386 Packages [213kB]   
Get:18 http://archive.ubuntu.com maverick-updates/restricted i386 Packages [1,797B]
Fetched 2,826kB in 2min 9s (21.8kB/s)                                          
Reading package lists... Done
[/B]
```There you go

---

### Post by |{urse on 2011-01-30
nice! Probably missing a symlink to somewhere. can you post the out put of this command?

sudo su
<password>
apt-get install nano && cat /var/log/dpkg.log | grep 'install'

I'm assuming that's still where dpkg keeps it's log. I'm using Intrepid still.

---

### Post by |{urse on 2011-01-30
Just an FYI if you really want to use Ubuntu I highly recommend installing it to hard disk! Those usb installations hardly ever work correctly. I'll check back tomorrow to see if you still want to work on getting apt fixed on the usb install. Nighters ^^

---

### Post by boopit on 2011-01-30
I actually found help yesterday. There was a file (can't remember exactly where, I'm running Windows at the moment) and I read that if you temporarily move it and install the new kernel, installation problems should be fixed. So I moved the file temporarily, and ran 

```
sudo apt-get update && sudo apt-get upgrade
```

And viola! Everything was fixed. 

I was starting to give up hope; that was like my 5th clean installation that day. :P

Thanks for helping anyways!

---

### Post by |{urse on 2011-01-31
glad u got things sorted ^^

---

