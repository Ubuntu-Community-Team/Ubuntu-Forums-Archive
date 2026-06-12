---
title: "Installing Kubuntu 7.10 mashed grub for Ubuntu 7.10"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by -dean- on 2008-03-28
I had a good working grub for Ubuntu 7.10.
I then installed Kubuntu 7.10 to another partition that originally held Ubuntu Dapper.
The Kubuntu Grub recognized the Ubuntu installation and included the Ubuntu boot option (as well as the option for Win XP) but when I boot into Ubuntu I get an error message.
Checking /var/log/fsck/checkfs gives:

Log of fsck -C -R -A -a 
Fri Mar 28 10:00:34 2008

fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb1: 1798 files, 335502/1310160 clusters
/dev/sdb8: clean, 52742/1310720 files, 2249727/2620595 blocks
fsck.ext3: Unable to resolve 'UUID=5f698508-419d-474e-a650-844c1b074f09'

hdb6 Dapper Home: clean, 10452/1310720 files, 698792/2620595 blocks
fsck died with exit status 8

Fri Mar 28 10:00:37 2008
----------------

Further checking:

:~$ blkid
/dev/sda1: TYPE="ntfs" UUID="CAC875AFC8759A81" 
/dev/sdb1: LABEL="HDB1-FAT32" UUID="2475-5C3A" TYPE="vfat" 
/dev/sdb2: UUID="73288b08-e3af-409a-9b47-bef8887d932e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: TYPE="ntfs" UUID="C14F0B114F09F40" LABEL="hdb3-NTFS" 
/dev/sdb6: TYPE="swap" UUID="77823254-df42-45a1-a5a1-e7383ea6d08b" 
/dev/sdb7: LABEL="hdb6 Dapper Home" UUID="3a0d79f1-bc6d-49ee-9f35-f5d4d329fad4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb9: TYPE="swap" UUID="769bd7be-f8b5-4d0d-b711-19ccac531552" 
/dev/sdb5: UUID="2ad9ba8f-0058-468a-aa02-12c06e25d43f" SEC_TYPE="ext2" TYPE="ext3" LABEL="hdb5 Gutsy" 
/dev/sdb8: UUID="602a6ff4-eb84-48fb-b1c0-eab88e3052f1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="Phone" UUID="7F2D-6F01" TYPE="vfat" 

I cannot see in the blkid check any reference to the
 'UUID=5f698508-419d-474e-a650-844c1b074f09'
which shows up in the in the checkfs

Is there a kind soul who can help me to get back to booting Ubuntu 7.10 properly?
Thank you in advance

---

### Post by confused57 on 2008-03-28
What happened is that when you installed Ubuntu 7.10, the Dapper partition was mounted using UUID in your /etc/fstab.  When you installed Kubuntu 7.10 to the former Dapper partition, the UUID changed...therefore, when your partitions are mounted at boot by Ubuntu 7.10's /etc/fstab it cannot find the former Dapper partition's UUID.

What you can do is mount your Ubuntu 7.10 partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_a_reiserfs_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_a_reiserfs_filesystem)
read the instructions in the link, but it will be something like:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/xxx /media/ubuntu
```
replace /dev/xxx with your Ubuntu 7.10 partition.

Then you can edit your /etc/fstab & insert the correct UUID:
```
gksudo gedit /media/ubuntu/etc/fstab
```
or you can temporarily comment out the incorrect mountpoint(place a # in front of) for your former Dapper partition(or where Kubuntu is currently installed)...if you had a separate home for Dapper, this partition would need to be commented also.

---

