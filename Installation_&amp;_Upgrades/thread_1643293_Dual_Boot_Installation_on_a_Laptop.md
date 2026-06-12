---
title: "Dual Boot Installation on a Laptop"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by Rheged on 2010-12-11
Hi all,

I'm a complete an utter newbie on this forum, and indeed to linux/ubuntu in general so pardon me in advance if some of my question makes no sense/sounds silly/makes you want to exterminate all noobs.

Basically, I've had bad experiences (i.e. had to use my recovery system) trying to install a dual boot system with OpenSuse and want to get some sound advice before I proceed with installing Ubuntu, instead of having to go through the agony of formatting and recovering Vista HP again, and consequently trying to teach it all over again how to suck less.

Okay, so less waffle and more questioning. Background information is that the laptop is a Compaq F560. It has at present Win Vista 32 HP on the primary partition (C), with a recovery partition on (D). It has a very basic, almost un-alterable BIOS, 1.5Gb of RAM, 120Gb HD, standard CD rom, integral nVidia 6100m graphics card, a broadcom wireless network adaptor and various other bits n' bobs.

When installing OpenSuse last time I found 2 huge flaws with my method. First one is, that I didn't have wired networking available to me at the time, and foolishly forgot to get hold of the wireless adaptor drivers before installing Suse. No biggy you say, just go back to windows and download from there. Great, except I'd bozzed up the MBR too, so couldn't do that. Suse, for it's part, ran fine. Very smooth. I just couldn't do anything with it. 

What I'm now looking to do, is give Ubuntu a shot, as part of a dual boot system, with Vista on the other half. I want to make vista the default boot system. I DONT want to have to go through my compaq's recovery system again, if possible. To meet these objectives, I would very much appreciate step-by-step instructions aimed at a complete linux noob. 

Ultimately, I'd like to transfer all of my operations across to Ubuntu, but I'm too windows-dependent at the moment, though some sort of windows-emulator wouldn't be a bad idea if anyone knows where/how/what.

Looking forward to your replies,

Rheged ;)

---

### Post by restorator on 2010-12-11
First thing you should do is run it from the live cd (select try without any changes to your computer) and see if it has any problems with your wireless or graphics, both common areas of concern. Use it for a while like that. If it works fine and you are satisfied then go ahead and install. If it works from the live cd it should work fine installed. If it doesn't work from the cd it likely wont work after install without some fiddling at the very least.

As far as installing, if you already have a partition from suse you don't want anymore, during the installation select to delete/overwrite (I forget the exact wording of the installer) and use that partition for your ubuntu install. As long as you DO NOT do anything with the windows partition everything should pretty much "just work". 

If you DO NOT have a separate partition you need to shrink your existing one. You can do that from the live cd. Use (System>Administration>Gparted) gparted and shrink the existing ntfs partition to allow for space for ubuntu. Don't forget to hit "Apply" and wait for it to give success messages. You can leave the space you newly created unallocated and when you get to the installer select "use the largest free space" (again i forget the wording). continue the install and again it should just work.

*However anything CAN go wrong, unlikely in his scenario, but it can, so you may want to backup some things or everything before you try the installation.

Good luck!

---

### Post by Rheged on 2010-12-14
Thanks very much! Will prob start giving it a shot soon. Will let you know how it goes :)

---

### Post by Mark Phelps on 2010-12-14
If you download and install Macrium Reflect in your Vista OS, you will have the ability to back that off to an external drive, and to make a recovery CD to use to do a restore if needed.  They have a free version you can download.

---

