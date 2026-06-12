---
title: "disk space is too small in default installation"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by Sergeig on 2010-03-31
G'day,

I installed 9.1 under VMWare workstation with 10G disk space as single file. I want Java+Eclipse but can not install jdk6 as there is no space available, see below. 

Q: How can I install ubuntu with proper disk space that I specify?
>>>>>>>>>>>>>>>>>>>>>>>>>>>>
ubuntu@ubuntu:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
aufs                   261M   219M    42M  84% /
udev                   261M   222k   261M   1% /dev
/dev/sr0               724M   724M      0 100% /cdrom
/dev/loop0             701M   701M      0 100% /rofs
none                   261M   193k   261M   1% /dev/shm
tmpfs                  261M    33k   261M   1% /tmp
none                   261M    95k   261M   1% /var/run
none                   261M      0   261M   0% /var/lock
none                   261M      0   261M   0% /lib/init/rw


ubuntu@ubuntu:~$ df -h /boot
Filesystem            Size  Used Avail Use% Mounted on
aufs                  249M  244M  4.9M  99% /

root@ubuntu:~# fdisk -l

Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
 
I guess I miss something fundamental...thank you ahead, 
sergei

---

### Post by john newbuntu on 2010-03-31
As the last error pointed out, was the partition table created correctly?  You may have to try re-creating the partition with gparted or re-installing from a liveCD.  Please wait for a second opinion on this.

---

### Post by gmargo on 2010-03-31
> 
aufs                   261M   219M    42M  84% /
It looks like you are still running off of a LiveCD.  "aufs" is a filesystem used on LiveCDs or bootable USBs, not on normal hard disk installations.

---

