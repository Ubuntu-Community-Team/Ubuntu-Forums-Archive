---
title: "Having a persistent installation in USB"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by PhantomSAP on 2010-11-02
Hi,
 
   I am a beginner in ubuntu and wanted to try this OS. I have been using a USB as a live CD but its not a persistent drive and any changes (in terms of drivers and such) are lost on reboot. Is it possible to have the OS installed in a USB drive instead of the hard disk? If yes I would like some directions as to how this could be done or maybe a guide for it if there is one around. I am using a Ubuntu 10.10 USB live CD currently and my Laptop has Windows Vista as OS.
 
Let me know if there are any other details needed for this please, and thanks.

---

### Post by Tunnelrat81 on 2010-11-02
I'm currently playing with this as well.  Last night I ran the Ubuntu 10.10 .iso through "Universal USB Installer" to create a usable installation that utilizes the persistence feature.  I can't yet give much of a review as I've only played with it for a bit.  But here's what I've done.  

I installed it on a PNY 4gb flash drive, selecting 2gb for persistence data and was able to boot into the OS, install a few things, set background image etc....then shut down.  I tried rebooting on the same machine _after first booting back to my windows 7 install_ and the second time around it just hung with a black screen in the middle of the bootup.  I then tried jumped over to my wife's laptop and hers booted right into the USB OS and had retained my background image and installed software.  I'll take some time later on to troubleshoot the first (desktop) machine, but this seems to be working well enough.  

The USB install so far acts exactly like a Live cd, with the "Install Ubuntu" shortcut on the desktop, just seems to save settings and drivers unlike the CD.  So far I'm happy to be able to safely play with Linux again with this.  So many things that I miss about it, and yet the inevitable head scratching during setup.  =)

I believe the live cd also includes a USB installation process right off of the menu that probably works the same, maybe even better, but haven't yet tried that.  This first time around was an experiment for me, so I'm planning on spending more time with it.

-Jeremy

---

### Post by dabl on 2010-11-02
Except for the change to Grub 2 (and the differences in configuring it), I believe this guide is still accurate:

[http://kubuntuforums.net/forums/index.php?topic=3089474.0](http://kubuntuforums.net/forums/index.php?topic=3089474.0)

I personally prefer a non-persistent "Live CD" bootable USB, and since the Linux OS only needs less than 1 GB when you do it this way, I set mine up to have a FAT32 storage partition in the first partition, and the bootable Linux in the second partition, like this:

[http://kubuntuforums.net/forums/index.php?topic=3107512.0](http://kubuntuforums.net/forums/index.php?topic=3107512.0)

---

### Post by oldfred on 2010-11-02
Another alternative is a full install. If you only have 4GB it is tight and the persistence alternative may still be best, but if you have 8GB or more then a full install is easy to do. 

You do not have to encrypt it if you do not want to, the screens have changed slightly with Maverick. But it is not really any different than an install to a second drive.
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler
[https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes](https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes)

[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

