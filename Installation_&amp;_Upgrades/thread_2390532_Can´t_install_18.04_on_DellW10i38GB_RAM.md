---
title: "Can´t install 18.04 on Dell/W10/i3/8GB RAM"
date: 2018-04-29
forum: Installation &amp; Upgrades
---

### Post by francisco.cerna on 2018-04-29
Hello,

I've been trying to install Ubuntu 18.04 on my Dell Inspiron 11 3000 Series 2-in-1, but it always freezes on installation (while installation, I mean). It always happens on this moment:

[https://i.imgur.com/Yicodk2.jpg](https://i.imgur.com/Yicodk2.jpg)

[https://i.imgur.com/GnXJDn6.jpg](https://i.imgur.com/GnXJDn6.jpg)

(On selection of types of installation)

You can check the characteristics of my laptop here: [https://www.youtube.com/watch?v=8WUgc2P9ReQ](https://www.youtube.com/watch?v=8WUgc2P9ReQ) Basically, it's an Core i3 laptop with 8 GB of RAM memory (originally 4, but I added 4 more GB) and a 500 GB hard drive. It has Intel HD Graphics 520 and Windows 10 (64-bit).

I have a 100 GB partition for Ubuntu (because I wanted to have both Windows and Ubuntu in dual boot). And I've already tried many things, like installing an older version of Ubuntu (like 12.04) or using different programs to make the bootable USB (Rufus, Universal USB Installer and LinuxLive USB Creator), and, as a I read, using this command 'nomodeset'. Nothing has worked so far, which is weird because I can use Ubuntu without installing it with no problem. But I have noticed that whenever I'm booting from the USB, the computer's processor works really hard because of the sound of the fan and the heat (which doesn't happen on Windows unless I open a lot of apps or play a game with good graphics).

Can you tell me what else can I do? As I said, I would like to dual boot Windows10-Ubuntu.

Thanks

Francisco

---

### Post by yancek on 2018-04-29
Which windows are you using?  Better to shrink your windows partition(s) to create unallocated space for Ubuntu as you will have to format the space on the partition for Ubuntu in any case.
Did you verify the download of Ubuntu before putting it on the usb.  Explained at the Ubuntu download site, md5 checksum or shasum.

---

