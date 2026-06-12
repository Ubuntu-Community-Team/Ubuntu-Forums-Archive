---
title: "Ubuntu Install Error"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by T1125P on 2011-08-14
Hi all. I'm new to Ubuntu 11.04 I know only some commands and other tweaks, I'm mostly a Win 7 expert LOL Anyway I wanted to install Ubuntu on my Netbook using a 32GB SD card. I download the wubi installer, used 30gb for installation size on the SD card, rebooted fine, but when it got to the ubuntu screen, it just sat there loading. I disconnected the internet to maybe speed it up and it did nothing. It was pissing me off lol so I just hit the power button. But now it shows a dual boot on my C drive, but I didn't have it on C it was on my SD card. I even uninstalled it from windows took out eveything, so now I get this \ubuntu\winboot\wubildr.mbr  when windows boot, I dont want this lol I need to take this entry out.. Need some help....Thanks

---

### Post by madjr on 2011-08-14
ok, it didnt get to the second installation screen.

the first time it reboots from windows it should take like a minute or 2 and then load the second part of the installation.

it could hang sometimes if the computer is a bit slow or hardware not being detected properly...

so can windows still boot?

to check if its not a hardware detection problem, what you can do is test/try it from an usb stick (live version. 2gb usb recommended) and see if everything works.

instructions:
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

you can also try an older/lighter version (10.04 or 10.10)

---

### Post by T1125P on 2011-08-14
Hi, thanks. After messing with this for half the day haha. I have managed to merge 2 partitions I had, in disk management. This was weird as I did not have them before one said recovery. Well now its fine boots as normal to Win 7. I will try again this week, to install ubuntu on my 32gb card. I really like it so far very fast, stable no sypware viruses no need to even defrag this is great. I actually have it on my work pc at work, using libre office and its great. So far Im loving it.  I love windows for games as I am a gamer :) But thanks again.

---

### Post by madjr on 2011-08-14
yea i know what you mean, i had to do some maintanace on windows yesterday, wow what a chore..

still need to run the spyware scanner later.

all that just for 2 games i couldnt get working in ubuntu (but i usually do get many of them to work). :p

anyway we are here if you need further help :D

---

### Post by T1125P on 2011-08-14
Yeah I know how windows is, it can be a pain. lol. I downloaded Doom 3 for linux  I have Win version Im curious to see how it will run. Well thanks again, glad i found this forum its really great.  Will post again once I get Ubuntu running. Thank you :)

---

### Post by varunendra on 2011-08-15
T1125P,
If you want to install Ubuntu on sd card, why are you bothering with WUBI? You can install it normally on it. The only thing to be cautious about would be to make sure to install grub on the sd card, not the internal hard drive which would most probably the default choice for grub. To install grub on the sd card, you'll need to go into "Advance" option in the manual partition steps.

This will ensure that both operating systems have zero interference with each other, plus ubuntu would be able to work in its free, natural way, with no restrictions as in wubi setup. To boot ubuntu, you'll have to plug in the card and select to boot from it in the BIOS boot menu. When the card is not plugged, win7 will boot normally and there would be not even traces of any ubuntu installation on the netbook.

Of course you'll need a Live USB key to install Ubuntu without WUBI. You can create one using the Universal USB Installer that Ubuntu official site offers, or [Unetbootin]("http://unetbootin.sourceforge.net/"). If you have Vbox or VMware installed, you can boot a VM directly from the Ubuntu iso and install it on the SD card.

If you have any specific reason to install through WUBI, I'd like to know.

---

