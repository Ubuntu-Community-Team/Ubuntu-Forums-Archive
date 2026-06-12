---
title: "New here and have some questions"
date: 2005-08-22
forum: Installation &amp; Upgrades
---

### Post by MdaG on 2005-08-22
Hi all!

First I'd like to apologize if this is the wrong forum to post this.

I'm a former Gentoo user (been using Gentoo since Nov 2004) and I've recently become fed up with all the hassle of running a clean system with Gentoo. It's just too easy to break your system if you're not reading up on the current state of the packages and I don't have time to do that. I've read a lot of good stuff about Ubuntu. It says that Ubuntu is
[list]
[*]Customizable
[*]Up to date packages
[*]Easy to maintain
[*]Just works!
[/list] 
If that's true, then it sounds like a distro for me. I've downloaded version 5.04 (install CD) and I was hoping to do a dual install together with my gaming system (Win XP). This is the setup I'm hoping to do:

Windows: /dev/hda1 *ntfs*
Boot:       /dev/hda2 *ext2*
Ubuntu:   /dev/hda3 *reiserfs*

Is that possible or does Ubuntu need a different setup?
The boot section is insurance that I'll be able to reach my Windows system if I break my Linux system. My computer is a DELL Latitude D800 laptop with a wide screen.

---

### Post by odin on 2005-08-22
Well everything you heart about ubuntu it's true plus having the best comunity in the whole linux world!!!

About the config,it should be ok.I assume you didnt forget your swap partition so yes it should work.

Welcome!!!

---

### Post by MdaG on 2005-08-22
Ah swap oh yes.

Windows: /dev/hda1 *ntfs*
Boot: /dev/hda2 *ext2*
Swap: /dev/hda3
Ubuntu: /dev/hda4 *reiserfs*

Now it's right. Is there a way to edit the boot loader during the install sequence? I'm used to grub. I usually use fdisk to setup the partitioning tables and I've heard that Ubuntu's is automated. I don't want to kill my current bootloader if something happens... if that happens I won't be able to reach my Windows system (internet).

Thanks for the welcome!  :)

***EDIT***
Installed the hoary hedgehog  :grin: 
I have to say that I'm impressed. Autodetection all the way, even my screen resolution was found and put as default (1680x1050)! Now I'm just gonna get aquanted with my new best friend. So far I've noticed that Ubuntu is noticably slower that Gentoo, but that's probably because I'm now running Gnome and not Fluxbox as I did on my Gentoo system.

Stuff to do:
[list]
[*]Find out the differences between portage and APT.
[*]Find out what this "sudo" is all about
[*]Set up my working environment (Anjuta, Nvu etc.)
[*]Import my backup
[*]Learn where all the config files resides on my new Ubuntu system.
[*]Turn off the annoying PC speaker!
[/list]

---

### Post by odin on 2005-08-22
then your config is right and I'm not completely sure about your question but here([http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)) you can find some information about this topic.It also explains how to copy your mbr so you can restore it if you have any problem.

hope this can help you a bit.

---

### Post by mcmuffy on 2005-08-22
> 
Find out the differences between portage and APT.


About 3 hours per program  :razz: 

Sorry, I could not resist  :grin:

---

### Post by odin on 2005-08-23
[QUOTE=MdaG]
[*]Find out what this "sudo" is all about

[/QUOTE]


try this link [https://wiki.ubuntu.com//RootSudo](https://wiki.ubuntu.com//RootSudo)


you can also find some information about many things in [www.ubuntuguide.org](www.ubuntuguide.org) and of course in [https://wiki.ubuntu.com](https://wiki.ubuntu.com)




 :grin:

---

