---
title: "Partitioner"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by trappleye on 2007-10-25
I have a HP Pavillion 9205us that came with vista installed, and I created a 10GB partition that I want to install Ubuntu on. I have downloaded 7.1 64 bit version as both Live CD and Text versions and burned them to disks. I experience different problems with both disks, but neither will let me install ubuntu. 

When I try to load the Live CD it will load the linux, but I don't think it is able to control my laptop monitor because after it boots to linux I get a white screen that slowly fades to black. I have tried loading in safe graphics mode with no success either. 

With the text version I get hung up at the partitioner. I don't want to run the guided partitioner because I don't want to format the whole HD, just the 10GB partition I set up for the install. However when I get to the manual install it shows the partition I want the install on, but I can't figure out how to tell it to use that partition. I have set the mount point at "/" and I get an error that says "not a fully-functional Unix file system" but if I put anything else in there ie "/ext2" I get a "no root file system is defined please correct this from the partition menu" error. I'm stuck

I have looked at [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing) but it describes how to do it with a live CD, and [https://help.ubuntu.com/community/forum/installation/Partitioning](https://help.ubuntu.com/community/forum/installation/Partitioning) says to use guided partition. 

If you have any suggestions please let me know.

Here's the info on my computer:
    * 17-inch screen
    * 1.6 GHz AMD Turion 64 X2 TL-50 dual-core processor
    * 120 GB hard drive
    * 1 GB installed RAM (2 GB max), 
    * multi-format/dual-layer LightScribe DVD drive
    * 54g Wi-Fi LAN (802.11b/g), 10/100 Ethernet
    * Nvidia GeForce Go 6150 video card with up to 288 MB shared memory
    * Pre-installed with Windows Vista Home Premium

---

### Post by joao82 on 2007-10-25
Did you format the new partition to ext3 when you created it?
you can't install Ubuntu on a blank unformatted partition, I think.

---

### Post by trappleye on 2007-10-25
it is formatted to fat32

---

### Post by joao82 on 2007-10-25
format it to ext3 and try again.

---

