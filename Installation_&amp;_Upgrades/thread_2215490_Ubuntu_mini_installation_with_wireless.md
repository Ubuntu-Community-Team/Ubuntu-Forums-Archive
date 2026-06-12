---
title: "Ubuntu mini installation with wireless"
date: 2014-04-06
forum: Installation &amp; Upgrades
---

### Post by evan8 on 2014-04-06
Is it possible to do so or must I have to be connected directly through ethernet to download gnome-network packges or whichever I need? I have never tried minimal install before.Bur Have it looks like you need direct connection to start out

---

### Post by ibjsb4 on 2014-04-07
Yes, you must be hard wired to the net to use the mini iso.  The mini iso is all I use; what kind of build you got going on?

---

### Post by sudodus on 2014-04-07
At least it is much easier and recommended to use wired internet (ethernet) during the installation.

I don't think there are any drivers for wifi in the mini.iso, but I am not sure, so I would be interested too in a reply from someone who knows.

According to this link you need wired internet (I have edited that wiki page, but I did not write that particular instruction)

> 1. You need a wired Ethernet connection 

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

### Post by evan8 on 2014-04-07
Okay . thanks folks. it's what I figured. Just sucks because I have desktop and ethernet is in another room. 

I have have 2 desktops one is crappy but runs fine. It's sort of my guinea pig machine. Sadly my brother has my laptop in pawn right now. That would make things much easier to try heh.

---

### Post by sudodus on 2014-04-07
But remember that it is ***only during the installation, that you need wired internet***. After installation, it will be the same Lubuntu or Xubuntu, with the same possibility to connect via wifi.

If you reply to the question of ibjsb4:

- what kind of build you got going on?

and questions of mine about the computer, it will be easier to give good and detailed advice.

What are the computer specs?

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by evan8 on 2014-04-07
Okay. So, it will  install the network drivers for me? I know when i installed debian I didn't have one.

 My main PC uses
AMD FX-6300 Six-Core @ 3.5GHz
 GPU: AMD/ATI RS780L [Radeon 3000]
RAM: 878MB / 3431MB
                     

Test computer is a crapper with 1 gig of ram and intel. But runs xubuntu etc just fine. But I just want to learn how to do minimal since I don't need extra bloat at all.


RTL8111 on crapper for wireless. Uses USB for adpator

---

### Post by sudodus on 2014-04-07
If you install the basic system and then lubuntu-desktop you will be the normal Lubuntu.
If you install the basic system and then xubuntu-desktop you will be the normal Xubuntu.
If you install the basic system and then ubuntu-desktop you will be the standard Ubuntu.
If you install the basic system and then kubuntu-desktop you will be the normal Kubuntu.

This implies that you will get the system for wifi (after the installation has finished. However, you might need a proprietary driver for either or both of graphics and wifi, and that is easier while you are still connected via wired internet.

Your computer is powerful enough for any of the desktop if I understand correctly that you have 4 GB RAM.

---

### Post by evan8 on 2014-04-07
oh yeah. I custumed built my main PC. The other is a junker but it runs fine. But thinking would run even better on a minimal install.Just sucks I have to bring desktop into my living room to do so heh. thanks for help.

Oh and both my graphic drivers have worked out of box without propietary drivers needed. luckily

---

### Post by sudodus on 2014-04-07
I think it will run well enough with either of Lubuntu or Ubuntu Server (with a light graphical desktop or only text mode). Both of them can be installed from dedicated install iso files. If you need no proprietary drivers, you might try to install (some additional packages) via wifi, so that you need neither move the computer nor get a long ethernet cable.

An alternative if you want something really light is to install the basic system of ***Lubuntu Core Trusty*** using the experimental ***9w*** installer. See this link, posts #88 and #89 and the following

[http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586](http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586)

and like if you started with the alternate iso, you can install packages afterwards to get exactly what you want. You can even start with a text mode system.

These installed versions come with an advanced and portable network manager installed, and need no network connection during the installation.

---

