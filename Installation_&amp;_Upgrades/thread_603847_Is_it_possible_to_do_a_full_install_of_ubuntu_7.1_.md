---
title: "Is it possible to do a full install of ubuntu 7.1 to a USB/SSD drive?"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by Alchemist42 on 2007-11-05
All,

My apologies if this is a simple question...  Id like to do a FULL INSTALL of ubuntu onto a flash drive (2gb, 4gb, etc) so I can use have the full environment available.  

Ive already setup a USB with a persistent version of the live CD using the pendrive instructions and that works fine... but im looking to do a full install so i can play with software and install other software as many apps I try to install using Add/Remove simply give an error when they run which im thinking is due to the nature of the live cd versus a full install (lazarus for example). 

What Ive tried so far... 

I pulled my hard drive out of my e1505 notebook (paranoid the install might screw up my hd if i made a mistake) and booted from the 7.1 live cd... then did an automated install to a 2gb USB drive (sandisk cruzer) 

The install started fine and got thru about 68% of the copying files stage then the window simply closed.  No error message, no complete message and looking at the flash drive it was empty although it showed activity during the whole install process.

So...  was the drive not big enough?   is there something else going on?  

When this didnt work I used the pendrive instructions to create the casper partition, etc. and got that working without a hitch... and it boots fine... but still cant install most software or try out the advanced desktop effects, etc.   so looking to do a full install.   

Is this possible? 

Thanks... i develop for a living but kinda new to linux so any help would be appreciated.

---

### Post by Bliepo32 on 2007-11-05
To answer your question: you should be able to install it on a USB-stick (although I wouldn't advise it), as long as it is big enough.

Of course, your installation hangs (at 68%). My question is, do you happen to have little RAM, and does the installation hang when configuring anthy? If so, then please read the following [http://ubuntuforums.org/showthread.php?p=1948173#post1948173](http://ubuntuforums.org/showthread.php?p=1948173#post1948173)

---

### Post by Alchemist42 on 2007-11-05
Thanks for the quick reply....  

I suppose I should have supplied some more details on my system, etc.

Im using a Dell e1505, core-duo (32-bit) 2ghz, 2gb 667mhz RAM, x1400 video... and attempting to install on a 2gb Sandisk Cruzer USB stick.

During the install... I go thru all the initial setup (location, etc) and it starts copying files.   The install says 'Copying Files' and has a progress bar displayed...  gets to 68% then the window with the progress bar closes and im back in the livecd desktop...  no error message... nothing saying what happened.  

It did move fast thru the first 40% of copying files then ran very slowly (45+ minutes which seemed odd going to a flash drive to get to 68% and exit. 

Why do you recommend against doing a full install to a USB drive?   

Basically im wanting to have the whole environment available and do some development testing and such on it without disturbing my current development system.   

Thanks again

---

### Post by Alchemist42 on 2007-11-05
Has anyone successfully done a full install of Ubuntu to a USB drive?

---

### Post by Nick Payne on 2007-11-08
See [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/"). I've tried this on an 8Gb Kingston flash drive and it works as advertised. Configuration changes you make are persistent across boots, and the flash install boots correctly both on an HP machine I have at home and a Dell machine I have at work.

---

