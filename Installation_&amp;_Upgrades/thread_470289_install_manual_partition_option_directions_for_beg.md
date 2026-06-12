---
title: "install manual partition option directions for beginner"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by doobey on 2007-06-10
Dell Inspiron 1300 40GB, 22GB unused. (Note: I am an absolute beginner and an figuring this out on the fly)

I need to use manual partition option during install and I need detailed instructions or I'm afraid to do it. 

Background story: I want to have a _dual_ boot setup so option one, "Guided use of entire disk" is out. "Guided re-size" option does not come up, and "Guided  use the largest length of contiguous space" gets an error message saying not enough space (this may be because when I defraged a large block of used space, about 3GB, is on the right side of the horizontal graphic in windows defrag when done...?)

What install partition is asking now: I need to "specify a partition for the root system file (mount point "/") with a min size of 2 GB, and a swap partition of at least 256MB"

Note I would like to downsize ntfs to about 18GB, leaving me about 18GB for Ubuntu.

Here is what the partition menu in istall says:
/dev/sda1 fat16 /media/sda1 41MB(size)/ 33MB(used)
/dev/sda2 ntfs /media/sda2 36479MB/12800MB
/dev/sda3 fat32 /media/sda3 3479MB/3100MB
free space 8MB

Do I start with the "Edit partition button"?????

Thanks! d

---

### Post by zbeckerd on 2007-06-11
Go here.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I prefer using a Virtual Machine on my laptop.  Also there are lots of VM appliances for running ununtu on win.

But go ahead with dual boot.  Just make sure you have backup of anything important to you.

---

