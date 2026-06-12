---
title: "Wacom Bamboo Connect scroll button not working?"
date: 2012-03-06
forum: Installation &amp; Upgrades
---

### Post by TheFsm on 2012-03-06
So yeah, I bought a Wacom Bamboo Connect tablet last week and installed on Windows, and today I ran through the forums and found that I couuld use it on ubuntu as well; so I installed the patch, but, the problem is: I cannot scroll with the pen, I must use the scollbar (Click the pen's button and grab up and down)

Help would be appreciated! :D

Also, when I'm drawing with it, it's like drawing with a mouse, the pressure sentibility disappeared, why?

---

### Post by Favux on 2012-03-06
Hi TheFsm,

Welcome to Ubuntu forums!

Which release of Ubuntu are you using?  Which patch did you install from where?

What application don't you have Pressure in?

Linux Wacom does not support scroll with the stylus side buttons.  You can either install a plug-in for FireFox or Chrome to grab the page and move it around or install EasyStroke and define a stroke for scroll.  That's one of the examples at the EasyStroke site.

---

### Post by TheFsm on 2012-03-06
Um, thank you very much! :)

I'm using Ubuntu 11.10 Oneiric Ocelot

[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562) is the patch I used;

I. Install input-wacom-0.12.1's wacom.ko (the USB kernel driver); with a first generation BambooPT (October 2009) you can skip this step if you have Natty or Oneiric, it's not needed unless your model or a feature is not supported by the default wacom.ko
Copy and paste each line into a terminal (Applications > Accessories > Terminal) and hit enter after each line (except the ones in parenthesis). Careful, some lines extend past the right side of the "box". Get all of them. Now download, compile, and install the wacom.ko.:

```
cd Desktop

wget http://prdownloads.sourceforge.net/linuxwacom/input-wacom-0.12.1.tar.bz2

sudo apt-get update

(For Mint use libX11-dev instead of libx11-dev in the following command)
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev autoconf libtool

sudo apt-get upgrade

uname -r

(If you have the generic kernel which most do.)
sudo apt-get install linux-headers-generic

(If you have the rt or pae kernel.)
sudo apt-get install linux-headers-rt
or
sudo apt-get install linux-headers-generic-pae

tar xjvf input-wacom-0.12.1.tar.bz2

cd input-wacom-0.12.1

./configure --prefix=/usr

(If you are in Lucid or Maverick.)
sudo cp ./2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
or
(If you are in Natty or Oneiric.)
sudo cp ./2.6.38/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

sudo depmod -a
You now need to restart.
```

And it's GIMP and Evernote(I ran it through Wine).

---

### Post by Favux on 2012-03-06
For Pressure with Gimp go to Edit > Preferences > Input Devices > Configure Extended Input Devices... > select stylus and change Mode to Screen.  If you get the spurious lines then install the NoGhostLines PPA mentioned in the Oneiric release specific notes.

Evernote on Wine may be a problem.  Some versions of Wine don't support Pressure and some versions need some configuration.  You'll have to google your version and see what you can come up with.

You may want to checkout Xournal and CellWriter.  If you're interested in graphics also try MyPaint and Inkscape.

---

### Post by TheFsm on 2012-03-06
Alright, thank you very much!

---

