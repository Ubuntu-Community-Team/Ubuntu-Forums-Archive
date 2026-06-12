---
title: "Cannot create ext3 filesystem"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by r4b on 2008-02-29
I am trying to install ubuntu 7.10 on a friend's Compaq Evo N400c. I have never installed linux before.

When trying to install I continually get the error that it cannot create the ext3 filesystem. There is one 20GB hard disk in the notebook, no other disks. 

In Gparted there is only one device, /dev/sda, with 3 partitions: 

/dev/sda1   ext3           17.81 GB
/dev/sda2   extended   839.33 MB
/dev/sda5   linux-swap 839.30 MB

/dev/sda1 appears as ext3 now that I tried to format it but I have the error

```
mkfs.ext3 /dev/sda1 
Could not stat /dev/sda1 --- No such file or directory
```

However, it is an internal hard disk, the only hard disk.

What does this mean and can anything be done about it? 

A bit of history, my friend (the idiot) has previously rebooted the machine during an installation AND physically removed and replaced the hard disk from the machine, if that makes any difference.

---

### Post by housam on 2008-02-29
use the manual way to  assign the partitions during the installation.

---

### Post by r4b on 2008-02-29
I'm completely new to this, what do I need to do?

---

### Post by dstew on 2008-02-29
> mkfs.ext3 /dev/sda1 
Could not stat /dev/sda1 --- No such file or directoryI am not sure what you are trying to do. Are you running this command from a running Ubuntu system? You shouldn't have to enter this command if you are using the installer.

If you are entering this command from an Ubuntu system, try **sudo** mkfs.ext3 /dev/sda1

---

### Post by r4b on 2008-02-29
I get the 'creation of ext3 filesystem failed' when running the installer, so I tried to format the partitiom myself with the partition editor. That's when I get the mkfs error

---

### Post by dstew on 2008-02-29
How are you running the partition editor? From a Live CD? Are you using gparted?

---

### Post by ajgreeny on 2008-02-29
Simply run the live ubuntu CD and go to Partition Manager.  You should now get a screen where you can chose the partition to change/shrink or whatever, then make a new one on the unallocated space and format it to ext3, plus a small one as swap.

An example.
1  Run Partition Manager using live CD on the laptop.
2  Select the 20GB partition on the disk and chose "Shrink"
3  Shrink partition to 10GB or whatever you want.
4  In 10GB unallocated space create a new partition of 9.5GB and a second of 0.5GB, format the 9.5GB as ext3 and the 0.5GB as swap.
5  Close Partition Manager
6  Install  Ubuntu and when you get to partitioning point, chose Manual, and use those two partitions as your install points, 9.5GB as / (root) and 0.5 as swap.

It should work, but if not there must be something strange about either the disk or the CD you're using.

---

### Post by r4b on 2008-02-29
I'm running from the Live CD

I already have 3 partitions
/dev/sda1 unknown 17.81 GB
/dev/sda2 extended 839.33 MB
/dev/sda5 linux-swap 839.30 MB

and I can't see a shrink option in any of the menus in Partition Mangaer

[IMG]http://img155.imageshack.us/img155/9585/dsc00501wo5.jpg[/IMG]

---

### Post by housam on 2008-02-29
delete the first partition sda1 and create it  as new with ext3 format.

---

### Post by ajgreeny on 2008-02-29
Sorry, I gave that info without looking in detail at a gparted screen first.  The **shrink** part is in fact **Resize/Move**, but on your pic it is greyed out, probably because the partitions are mounted.  Try right clicking on all of them and unmounting them and you may then be able to edit or change them.

In fact as there is nothing on the disk at the moment, or no files you want or need, (is that right?) you could simply delete all the partitions there at the moment and then make two new ones, an ext3 for root (/) using most of the disk, and a swap of about 0.5 - 1 GB, ie the rest of the disk.  The reason the installer is unable to make partitions could be because the disk is mounted at booting of the live disk or you have looked at the hard disk using nautilus when the live CD was running.  You can't do anything to a mounted partition in linux with gparted or the ubuntu installer.

The three partitions you see are an unknown partition and a swap.  The swap appears twicw as both sda2 and sda5 as it is an extended partition (sda2) containing a swap partition (sda5).  Ubuntu does this by default.

---

### Post by r4b on 2008-02-29
I deleted sda1 but I get the same error 'no such file or directory' when trying to create a new partition. Delete is greyed out for sda2 and sda5 =(. 
Could this be caused by the hard disk being re-inserted incorrectly?

---

### Post by bigblue2sea on 2008-03-01
I can sympathize, I had the same error message and just figured out what the problem was.

Edit: If you can't use GParted as described below, start the install and at the partition menu choose the option to
use the entire disk for the install (often the middle option). It will wipe the disk clean and create the ext3
partition and swap partition, and you won't have to direct the installer to the ext3 partition.

(I am assuming you do not have data on the hard drive, and can wipe it clean)

You already have a swap file of 800+mb, which is perfect.
Now you need an ext3 partition to install Ubuntu to.

Run the live cd and open GParted (System > Administration > Partition Editor)
Delete dev/sda1 and create a new partition formatted with ext3
Close GParted and double-click the installation icon.

After answering the questions, you will come to the screen asking how to partition - choose Manual.
then you will come to a screen that looks like this:
[IMG]http://i52.photobucket.com/albums/g8/bigblue2sea/AlmostReadytoInstall.png[/IMG]

Here's the part that was giving you a headache - you have to direct the installer to install Ubuntu to the ext3 partition.
Double click on the ext3 partition and you'll get a window like this:
[IMG]http://i52.photobucket.com/albums/g8/bigblue2sea/Directinginstallertoext3Partition.png[/IMG]

Under Mount Point, select "/" and select Ok
Now put a check in the box to format the ext3 partition (this is required). 
Your window should now look like this:
[IMG]http://i52.photobucket.com/albums/g8/bigblue2sea/ReadytoInstall.png[/IMG]
Click Forward

Everything should progress nicely now.
The next screen looks like this:
[IMG]http://i52.photobucket.com/albums/g8/bigblue2sea/ReadytoInstall_firstscreen.png[/IMG]
Click Forward
And you'll come to a screen like this:
[IMG]http://i52.photobucket.com/albums/g8/bigblue2sea/ReadytoInstall_secondscreen.png[/IMG]

That's it.

Note: The absolute easiest way to install ubuntu (if there is no data on the disk) is too delete all partitions and simply have the whole disk as free space. 
When you come to the Partition Manager screen, select the option to install to the free space. You won't have to direct the installer to the ext3 partition.

:)

---

### Post by r4b on 2008-03-01
Thanks for all the help, I finally got it working!

---

### Post by bigblue2sea on 2008-03-01
bravo :)

---

### Post by ma65p on 2008-05-14
Well, I have several partitions that I want to keep instead of deleting them. This is what I did.

Start installation like normal
Manually partition my disc
I deleted the partition I would like to install ubuntu. This is very important, do not just edit, DELETE the partition, make it become free space.
Create new partitions (ext3 and swap. I chose swap to be logical just in case I need another primary partition -> remember the limit of 4 primary partitions?)

Then I worked fine for me.

Excuse my English.

---

