---
title: "PXE ubuntu 10.04 install problem"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by Razor512 on 2010-07-03
Hi, I am trying to install ubuntu 10.04 on a toshiba portege M200 

It does not have a cd drive, it does not support booting from USB drives

I tried to do a PXE boot in order to install on the PC and everything seems to go fine until the install finishes then all I get when I boot is a command line (it can run various commands) (at startup it will ask me to log in but I never get any GUI)

Startx does not work to getting me to a actual GUI

how can I get a normal ubuntu UI and get everything set up properly?

I am using these instructions [http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows](http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows)

but with the ubuntu 10.04 netboot files

I uploaded my tftp folder to mediafire if anyone wants to look at it

[http://www.mediafire.com/?j52niytymqz](http://www.mediafire.com/?j52niytymqz)



Is there any way for me to get a full ubuntu install just like I would if I was install directly from a CD (and is there a way to pxe boot directly from a ubuntu cd or iso image?

---

### Post by gordintoronto on 2010-07-03
It appears that you installed the Ubuntu installer, not Ubuntu itself. Ubuntu is the size of a CD, somewhere around 600 MB.

---

### Post by Razor512 on 2010-07-04
the site said that it was suppose to automatically download the rest of the needed files. 

it probably did not do that for some reason. if there any way to complete the installation through the command line to get the full Ubuntu?

I wish someone could make a simple program kinda like linux live usb [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
but for PXE installs in which someone can just direct the app to a ISO file and it handles the rest of the PXE stuff.

---

### Post by naxovr on 2010-09-08
Is that the subject has stopped 3 months but maybe used to other people like me that I had to learn on my own.

The problem we have is not bad you've downloaded the files. If there is a step in the installation that tells you to install programs. Find and select Ubuntu Desktop and continuing with the installation. When you finish and you will have installed Ubuntu version 4.10 LTS Desktop Edition. That is, the normal version.

Greetings and I hope it helps someone ;)

Sorry for the English but is translated with google

---

