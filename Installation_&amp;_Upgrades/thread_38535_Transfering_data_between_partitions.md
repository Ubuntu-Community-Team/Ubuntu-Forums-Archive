---
title: "Transfering data between partitions"
date: 2005-05-31
forum: Installation &amp; Upgrades
---

### Post by AevaD on 2005-05-31
Hello, I just installed ubuntu and was wondering if there was a way to transfer data from my Win XP partition onto my linux partition without having to write many cds to do it. If there is a way to this, how so?

---

### Post by netrattler on 2005-05-31
I know a company called Paragon software make software that can do this, it's called paragon mount everything. I used to use when I was dual booting. They also make software so that Linux can write and read NTFS with no problems, think it's called NTFS for Linux. But that's if your willing to pay for it.

Joe

---

### Post by thrift on 2005-05-31
In short yes.  Just mount the WinXP partition from inside of Ubuntu.

Open a terminal and the type this command
sudo fdisk -l
enter your password

This will give you a prinout of your partition tables.  Locate your windows partition from this list and figure out what the device is from the list, then

sudo mount device /mnt

or for example if my device were /dev/hda1

sudo mount /dev/hda1 /mnt

If this works successfully you will have your WinXP files in the /mnt directory.  from the terminal, to test this:

ls /mnt 

when you are done copying over your files

sudo umount /mnt

to cleanly unmount the device from the /mnt directory.

Good Luck.

---

### Post by Xerampelinae on 2005-05-31
[QUOTE=AevaD]Hello, I just installed ubuntu and was wondering if there was a way to transfer data from my Win XP partition onto my linux partition without having to write many cds to do it. If there is a way to this, how so?[/QUOTE]
 You have to know your XP partition.  For example, if it is the first partition on the first (primary master) hdd, then it would be /dev/hda1.  If that's the case you could do

```

sudo mkdir /mnt/win
sudo mount -t ntfs /dev/hda1 /mnt/win

```

And then your files will all be in the /mnt/win directory.

---

### Post by jasmuz on 2005-05-31
[QUOTE=AevaD]Hello, I just installed ubuntu and was wondering if there was a way to transfer data from my Win XP partition onto my linux partition without having to write many cds to do it. If there is a way to this, how so?[/QUOTE]
 Hello!.
First off, what kind of partition do you have on you Windows system?...if its NTFS, Linux can write to it without messing it up. if its FAT32, its way easier.
If you do have a NTFS partition , you can download explore2fs, wich will let you read and copy files from your ext2 and ext3 partitions.
[www.uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](www.uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
If you do have FAT32, then mount it in /etc/fstab with the capability of RW.

---

### Post by thrift on 2005-05-31
[QUOTE=netrattler]I know a company called Paragon software make software that can do this, it's called paragon mount everything. I used to use when I was dual booting. They also make software so that Linux can write and read NTFS with no problems, think it's called NTFS for Linux. But that's if your willing to pay for it.
[/QUOTE]

or he could simply use the tools that come with Ubuntu.  They seem to work fine.

---

### Post by Xerampelinae on 2005-05-31
Geez, when I started responding to this, there were no answers.. then within the moment that I typed a response, there are like... 4!

---

### Post by thrift on 2005-05-31
[QUOTE=jasmuz]Hello!.
First off, what kind of partition do you have on you Windows system?...if its NTFS, Linux can write to it without messing it up. if its FAT32, its way easier.
If you do have a NTFS partition , you can download explore2fs, wich will let you read and copy files from your ext2 and ext3 partitions.
[www.uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](www.uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
If you do have FAT32, then mount it in /etc/fstab with the capability of RW.[/QUOTE]

He doesn't need to be able to write to it.  He needs to copy from it.
As well the NTFS drivers appear to be fine for write now.  I wouldn't use it for anything mission critical, but I've had reports of people copying bucket loads of files to NTFS partitions from within Linux without a problem.

---

### Post by AevaD on 2005-06-01
Thanks for the help so far, but after I mount the partition in to /mnt/win, I can't access it because I don't have enough permissions to. I think I need to be the root user, but how do I get those permissions?

---

### Post by thrift on 2005-06-01
Actually you don't want to be root for the fil copying, you just want to give yourself permission to the drive.  The easiest way to do that is to add two options to your mount command.

if your mount command were to be

mount /dev/hda1 /mnt

you could make it mount with a certain UID and GID for all the files on the driver, like this

mount /dev/hda1 /mnt -o uid=1000,gid=1000

to find what numbers you really want to use for the uid and gid you can open a terminal and 

cat /etc/passwd

and find a line that has your username on it, so for example mine:

thrift:x:1000:1000:thrift,,,:/home/thrift:/bin/bash


then the UID is the number after the x: so 1000

for the GID we open a terminal and

cat /etc/group

and a find a line that has your username(this is really your private group), so for mine:

thrift:x:1000:

then the GID is the number after the x: so 1000

so now we know the uid and gid to use when mount the drive, and can mount it so that i have access to it by adding the -o uid=1000,gid=1000 argument to the mount command.

You are going to have to umount the drive before you are going to be able to do all of this, so make sure you do that before you try mounting it again.

Good Luck.

---

### Post by Xerampelinae on 2005-06-01
Another way to find your user id is to type 'id' as whatever user.

---

