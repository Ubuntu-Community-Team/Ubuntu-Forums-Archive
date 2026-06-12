---
title: "Creating a bootable USB image based on a running system (NOT LiveCD)"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by sansbury on 2010-09-02
Hi and thanks in advance.

Let's say I have a system built and running in exactly the basic configuration I want, with my recompiled kernel, extra packages, special drivers, everything works, life is good. 

What I want to do is take this exact setup and create an image I can copy onto a bootable USB stick. Is there a way to essentially take the contents of my hard drive and copy that onto a USB stick and then boot directly from that?

The use case behind this is that I am building an embedded system of which I may have hundreds of boxes with identical hardware and software configurations. Instead of hard drives, I am going to use USB sticks for cost efficiency and maintenance. My idea is that when it's time to upgrade, I could just image a hundred new sticks and go out and swap them.

My issue is that a standard LiveCD install gets me maybe 25% of the way to a finished system. I need to recompile the kernel for realtime support with my CPU, add some fidgety drivers for some specific hardware, and install a whole bunch of additional packages. I suppose I could create a makefile(s) to replicate all the manual steps of the buildout but that seems like a lot of unnecessary complexity IF I can just image that running system as it is.

---

### Post by oldfred on 2010-09-03
If your flash drive is 8GB or more you can just to the full install to that. You still will want some special settings on the flash drive.

Standard full install to flash or SSD - you do not have to do encrypted:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You can use 
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[]("http://www.geekconnection.org/remastersys/remastersystool.html")[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by C.S.Cameron on 2010-09-03
I have cloned from hard drive sda to flash drive sdb using dd:
dd if=/dev/sda of=/dev/sdb
You should shrink the hard drive partition to the size of the flash drive first.
I'm not sure this method is fast enough to make hundreds of drives though.

---

### Post by sansbury on 2010-09-03
Thanks guys! Lots of good ideas I hadn't heard of in there. I don't need to do hundreds right away--a half dozen would be enough to prove the concept. Even if the process is a little slow, there are ways to make that scalable.

---

