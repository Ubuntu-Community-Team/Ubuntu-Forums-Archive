---
title: "Installing on Pre-partitioned system"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by hwedin on 2013-01-30
Hi

I'm wanting to install Ubuntu completely over windows on a computer of mine due to problems with windows.

The computer has two partitions on it both ~55 gb. The C drive is NTFS and the D is FAT.

I suspect that I'll need to reformat the FAT drive, correct?

What my main question is will I need to 'un-partion' the hard drive (and if so, how?), or will Ubuntu be able to 'see' the second partition?

Also, if possible, can you dumb down your replies as I'm new to Ubuntu. Just a couple of weeks playing with it using Wubi. 

Many thanks

---

### Post by dino99 on 2013-01-30
Welcome to our world  ;)

if your D: is empty (no data to save), then boot on partition tool like gparted, to remove it. Then you can follow my way:

here is how to set the partitions:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode ("Something Else" installer choice).
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start)

then when installing via the  iso, choose the "Something Else" installation (which is the manual mode)

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by ibjsb4 on 2013-01-30
If you are sure you want to remove windows just use the option on the Live CD to use intire disk.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by gifford on 2013-01-30
Yes, keep it simple. Let the Live CD remove windows and use the entire disk for Ubuntu.

---

### Post by hwedin on 2013-01-30
Cheers guys!

Thanks for your replies. I think I'll use the option in the live CD.
So glad that there was a simple solution!

Thanks again

---

