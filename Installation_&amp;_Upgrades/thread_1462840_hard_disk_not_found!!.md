---
title: "hard disk not found!!"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by abhinav.p on 2010-04-26
my brand new laptop with ubuntu pre installed has an 80gb hard disk.however i dont find any  drives in /media except for cdrom and cdrom0.it says 8 mb free.how do i access my hard disk.its 80GB SATA disk.

---

### Post by dv3500ea on 2010-04-26
'/' is your hard drive.
You can access it from places -> computer then double click on File System.

Linux has one file system '/' which is your main hard drive. Any external hard drives or removable storage will show up in '/media'.

---

### Post by quadproc on 2010-04-26
> **abhinav.p said:**
> my brand new laptop with ubuntu pre installed has an 80gb hard disk.however i dont find any  drives in /media except for cdrom and cdrom0.it says 8 mb free.how do i access my hard disk.its 80GB SATA disk.
Your user files will be located in the directory /home/<your_user_name> while system files will be located in various directories on the system.  If you only have one disk then all of those files (yours included) will be located on that disk but you don't have to worry about the details - the file system keeps it organized for you.

Start up a terminal and type in
```
pwd
```
and you will see where your files are located.

The disk drive itself is known as /dev/sda if it is the only one in your system but you cannot directly access it through that path.

The /media directory is used for removable devices such as floppy disks or CDROMs.

quadproc

---

