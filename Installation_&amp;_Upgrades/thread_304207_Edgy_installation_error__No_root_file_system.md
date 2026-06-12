---
title: "Edgy installation error : No root file system"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by Zombithium on 2006-11-21
Hi, 

I have used the two previous Ubuntu versions. Recently I had to change my motherboard and hence I wanted to reinstall Ubuntu because the previous versions won't boot (probably because of change in Chipset).

I have a dual-boot system with Window XP/ Ubuntu.

I am trying to install the latest Ubuntu without disturbing my old files kept in Windows and Ubuntu file system.
I had a dedicated 200 MB for /boot, around 500 MB for swap and around 10 GB for the root partition /.
When manually editing partition table, I chose the same options for the existing partitions with Reformat option selected for /boot and swap. Since I want to keep my files i didn't select this option for the root partition. Now I hoped that the root partition will be reused.
But when I press the next button it displays an error message saying - "No root file system".

Any ideas what am I doing wrong? (using the reformat option for the existing root file system also doesn't work).

[IMG]http://static.flickr.com/101/302925679_75362703ec.jpg?v=0[/IMG]

---

### Post by bulldog on 2006-11-21
Ubuntu will not overwrite any partition with data.
If there's no important data in your /home folder,just delete the old /root partition and create it again.

---

### Post by taurus on 2006-11-21
you also need to reformat your / besides /boot!

---

### Post by Zombithium on 2006-11-21
Yes, I do have some files on my old /home which I would like to keep. So is there no other option than to delete/format the old / partition?

If not, is there any way that I can atleast take a backup of my linux files on the windows file system before reformatting. Is it possible that I mount the current / and a windows file system (where I will copy the files), and copy the required files - when running with the live CD?
Could any one post the mount command for this process? I have a reiserfs file system on the / drive.

---

### Post by taurus on 2006-11-21
You have like 5 partitions for Windows!!!  Why don't you convert one of them to fat32 and copy all your personal files form /home to that new partition using the LiveCD...

---

### Post by Zombithium on 2006-11-21
The problem is not with the space - the problem is how do I mount one of those windows partition and the current /home so as to copy the files.
 
When i try to mount one of the windows file systems using 
$ sudo mount /dev/hdc8 /media/newfolder -t vfat 
it gives an error 
mount: special device /dev/hdc8 does not exist

any ideas how do i mount my hdc8(windows) and hdc3(my current/)?
thanks.

---

### Post by taurus on 2006-11-21
From the LiveCD, Applications -> Accessories -> Terminal, do

```
sudo mkdir /media/windows /media/ubuntu
sudo mount -t vfat /dev/hdc8 /media/windows
sudo mount -t ext3 /dev/hdc3 /media/ubuntu
```

---

### Post by Zombithium on 2006-11-21
That's what I did already. Please see my earlier post - the error when doing this is "mount: special device /dev/hdc8 does not exist".
I am guessing that it is not possible to mount partitions when using the live CD.

---

### Post by taurus on 2006-11-21
Yes, it is possible to mount partitions while you are using the LiveCD!  What is the output of this command then?

```
sudo fdisk -l 
```

---

### Post by Zombithium on 2006-11-21
Nothing !!!
It doesn't print anything... looks strange to me ...

---

### Post by cantormath on 2006-11-21
Got to say, the title of this thread is awesome.  No root file system is definitely an installation error. ::grin::

---

### Post by observative on 2007-12-31
And for me U7.10 on a w2k server with one hd and one partition, is still a  "no root file system" install error. Any insight would be appreciated as I have tried the recommends above, and the older validation.py fix that worked with 6.x, and they don't work for me. So I'm just going to take some of my beans and make some coffee and wait for an answer...I'm bound and determined to get off windows...if Gates is leaving so am I.

Added: I had to use the Ubuntu 7.10 Alternate iso to get a dual boot to work. I also had to pre-partition the drive and left free space for the install. Still had to use manually partition but it did take and now I have U7.10 and W2K server dual booting perfectly.

---

