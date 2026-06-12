---
title: "Ubuntu partitioner doesnt show all partitions!"
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by ziphnor on 2005-04-12
I have a serious problem installing Ubuntu 5.04. Ive booted up from the CD with no problems, and now im at the "Partition disks" screen. It lists 2 device IDE1 master (hda) 123.5GB and IDE1 slave (hdb) 20GB which is correct. However there is only 1 partition shown in the list, a 20GB fat32 partition + 8.2MB free space, its hard to tell from the way the menu is set up, but i assume the 20GB part is from the 20GB drive.

I happen to know that the 120GB disk contains a linux boot partition, a linux swap partition, a ReiserFS partition(containing my old gentoo install), a large fat32 partition and an NTFS partition with windows XP pro on it.

What i want to do is overwrite my gentoo install, using its partitions for Ubuntu. And i want to do this WITHOUT erasing the 120GB drive.

If i choose the 120GB drive, im informed that this will create a new empty partition table, which is not what i want.

Im confused. Is the partioner only showing me info for the 20GB drive? Is there some way to switch the view to the 120GB HD's partitions? 
Any help would be much appreciated!

Update: I took a screenshot of what the installer is showing me:
[http://i4.photobucket.com/albums/y133/ziphnor/ubuntu_part.jpg](http://i4.photobucket.com/albums/y133/ziphnor/ubuntu_part.jpg)
and what fdisk says:
[http://i4.photobucket.com/albums/y133/ziphnor/fdisk.jpg](http://i4.photobucket.com/albums/y133/ziphnor/fdisk.jpg)
Hope that can help someone help me :)

---

### Post by Xian on 2005-04-12
[QUOTE=ziphnor]I happen to know that the 120GB disk contains a linux boot partition, a linux swap partition, a ReiserFS partition(containing my old gentoo install), a large fat32 partition and an NTFS partition with windows XP pro on it.[/QUOTE]
Ubuntu uses parted for the partitioning section of the installer and my advice would be to check this 120GB HD while in Gentoo with the parted application. Emerge parted if it is not already installed and then issue that command (parted) from a terminal while su. Check to see if there are any errors or warnings issued at that time.

---

### Post by ziphnor on 2005-04-13
parted from Gentoo(actually Gentoo livecd, i forgot the root pw for my installation) says: Using /dev/hda
Warning: Unable to align partition properly. This probably means that another partitioning tool generated an incorrect partition table because it didnt have the correct bios geometry. It is safe to ignore but ignoring may cause (fixable) problems with some boot loaders.

It then outputs "Error: Unable to satisfy all constraints on the partition" and then gives me a "(parted)" prompt.  I never used parted before, so i tried help, then tried print but that gives me the same error.

Is there anything i can do about this, apart from writing a new partition table and destroying all contents?

---

### Post by ziphnor on 2005-04-13
I could really use some help here :) 

Is it possible to skip the partitioning stage, and assign partitions another way(since i already have the correct partitions set up)?

I was really looking forward to trying ubuntu, but perhaps ill just have to bite the bullet and fix/reinstall my Gentoo installation....

---

