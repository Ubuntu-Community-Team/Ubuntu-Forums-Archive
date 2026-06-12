---
title: "sda1 mounted on /cdrom while booting from cd"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by oneindelijk on 2010-05-05
Hi, 

I'm trying to install Lucid on a computer with windows already present.
When I ran trough the install procedure no drives show up at the partitioning stage. 
So I check some things out and it turns out that /dev/sda1 is mounted to /cdrom and I can't umount it because it says the disk is in use.

I'm booting with the live-cd downloaded from ubuntu.

Why is this happening ? Previously with older live-cd's I always have to mount the HD manually if I wanted to access it for any reason ?

---

### Post by oneindelijk on 2010-05-05
At first I tried installing this with unetbootin utility, which of course didn't work because than the iso is mounted from sda1.
So now I put all these files in a subfolder and tried booting from the livecd again, 
but sda1 is still being mounted...

---

### Post by oneindelijk on 2010-05-06
Still having problems ....
I downloaded and burned a ubuntu 9.10 cd and with this one I was able to resize the windows partition.
Then I tried to install Lucid, booting up through unetbootin...
At the partition layout section from the installer, now the HD shows up, 
saying something like ```
sda1 is mounted to /cdrom because it contains you install media, but you can still install ubuntu on partitions this disk contains blabla
```
So I go ahead, run through the whole procedure until ubuntu gathers all the information and then it says
```
Can't write to partition table on mounted /cdrom
And can't unmount
```
So I fire up gparted and create a primary ext4 and a swap so my disk layout looks like this:
```
Disk /dev/sda: 41.0 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x126ee653

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2687    21583296    7  HPFS/NTFS
/dev/sda2            2688        4806    17020867+  83  Linux
/dev/sda3            4807        4982     1413720   82  Linux swap / Solaris
```

I return to the installation procedure, but even when I only set sda2 as /
without formatting, resizing or creating partitions or anything, I still get this error...
Any ideas ?

---

