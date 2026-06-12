---
title: "Trouble installing"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by xEyce on 2007-11-11
So, after hours of trying to figure a bunch of stuff out, I've FINALLY been able to make an Lx3 Partition on my hard drive. 

What I've got here, is a 240GB Hard Drive, with now 4 partitions.  C: Windows, D: Games, F: Storage, and my U: Ubuntu Lx3 partition.

So, my problem is this. I've tried Ubuntu 7.10 Live CD, Alternate CD, and GParted Live CD.

All of them show that I have two hard drives, with 111GBs? It also says it's all unallocated space. 

This is what it looks like, on all of these things, and even when I go to INSTALL on the Live Ubuntu CD it looks like this. 

[IMG]http://img.photobucket.com/albums/v633/MakoSephiroth/Screenshotcopy.jpg[/IMG]

So, why are none of these picking up my correct hard drive and partitions? 

Thank you for all help!

---

### Post by taurus on 2007-11-11
You need to create a partition with that unallocated space, /dev/sda1, first.  Format it whatever filesystem you want.  Then, the installer will pick it up and convert it to ext3 filesystem for / and swap for /swap.

---

### Post by xEyce on 2007-11-11
I don't get it...

The Unallocated space shouldn't even be there in the first place, I have 4 partitions taking up all of the hard drive.

If I mess with those unallocated things on the live cd, wouldn't i be at risk of tampering with my partitions?

---

