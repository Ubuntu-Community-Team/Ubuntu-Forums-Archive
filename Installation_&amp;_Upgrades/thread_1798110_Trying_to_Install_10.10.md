---
title: "Trying to Install 10.10"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by Jaden* on 2011-07-05
I'm trying to install Ubuntu 10.10 Maverick Meerkat. I tried the regular download but it only offers 10.04 or 11.04, neither of which I want. I've been tring all day to get this thing done, I want to install it alongside my Windows 7 on my dell inspiron duo and I just can't figure it out. I found this page: [http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/) which might be what I need but I have no clue what to do from there. My laptop doesn't have a cd/dvd drive and I can't hook it up to one, so I need to do this either directly or via usb, please help. Any tips on installing alongside and partitioning would also be great too, thanks.

---

### Post by zvacet on 2011-07-06
From that site download **ubuntu-10.10-desktop-i386.iso.torrent** and after that read [this.]("https://help.ubuntu.com/community/HowToMD5SUM") If everything is O.K. Then see [here]("https://help.ubuntu.com/community/Installation/FromUSBStick") how to install from usb.You can partition this way

1. root=10GB                                   mountpoint /root
2. swap=~2GB
3. home= rest of free space                    mountpoint /home

format partitions as ext4 (except swap)

---

### Post by Kr0nZ on 2011-07-07
if you dont have a cd drive u will need to use a USB, I havn't burned a cd in years, I always install all operating systems using my USB stick. Just make sure you use a usb disk that is big enough, if you decide to use a bigger one you can set it up to be persistent, so it can be like a mini OS you can take anywhere and save your files too, unlike a cd that resets every time.

I use a program called [unetbootin]("http://unetbootin.sourceforge.net/") to make it. It even works for windows.
Also if I remember correctly a usb maker program comes with the Ubuntu disro, so you can just mount the iso, copy out the usb program and use that. Tho I have never used it.

---

### Post by mörgæs on 2011-07-07
> **Kr0nZ said:**
> 
Also if I remember correctly a usb maker program comes with the Ubuntu disro, so you can just mount the iso, copy out the usb program and use that.

Correct, the program is called USB Creator. If it for some reason does not work, try Unetbootin.

---

