---
title: "Absolute Minimal Install on USB"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by zer010 on 2011-02-03
My goal is to install the Ubuntu minimal image on a 4GB USB flash drive.  I'd like some suggestions on partitioning and how to build up from that.  I kinda want to have a GUI to build on and I was thinking of xfce4 or LXDE, but then again, there's options like this: [http://ompldr.org/vNnRveQ](http://ompldr.org/vNnRveQ) and this [http://ompldr.org/vNnRrNA](http://ompldr.org/vNnRrNA) which are really intriguing.  Any suggestions are greatly appreciated!

---

### Post by sanderj on 2011-02-03
My suggestion: Lubuntu on a persistent USB-stick installation


[LIST]
[*]get Lubuntu, burn to CD, boot CD
[*]after booting, start Startup Disck Creator (=GUI) or start "usb-creator-gtk" (=CLI)
[*]write Lubuntu to a 4GB stick, with as much as possible free / persistent space (see slider in lower part of screen)
[*]After writing, reboot from the USB stick, and enjoy Lubuntu from a USB stick
[/LIST]

---

### Post by zer010 on 2011-02-03
The only problem with running a LiveUSB is that it's not really possible(AFAIK) to do regular updates. I tried it earlier with Ubuntu and the update/upgrade process made the flash drive un-bootable. 
This time around, I'm just gonna install to the drive as if it were a normal HDD.  The thing is I'm not sure how much space I should reserve for "/" ,  "/home", and "swap".  I'm sure it will depend on what kind of Desktop Environment and Window Manager I use. To save space, I'm not really looking for a GUI login, I can just login at the CLI and "startx" when I want to.

---

### Post by sanderj on 2011-02-03
> **zer010 said:**
> 
The only problem with running a LiveUSB is that it's not really possible(AFAIK) to do regular updates. I tried it earlier with Ubuntu and the update/upgrade process made the flash drive un-bootable. 


I've had that problem on a 2GB USB-stick. I think it's a space problem; maybe you can try a 4GB USB-stick

> **zer010 said:**
> 

This time around, I'm just gonna install to the drive as if it were a normal HDD.  

I've done that once, and the result was terribly slow. So I look forward to your results.

---

### Post by beew on 2011-02-03
Actually I have installed Ubuntu10.10 on a 4G external hard disk before I did a full installation on my laptop. Except for the drawback of being bulkier to carry, installation in external hard disk works much better than usb (a lot faster) and it supports installation of propietary drivers and kernel updates as well. I needed these features because I used it to test my laptop's hardware before actually installing and the laptop uses propietary drivers.

Basically I just installed what I needed for my purpose and uninstalled whatever I didn't need to save space. For example, I uninstalled openoffice because it took a lot of space and I wouldn't use this installation for office anyway. On the other hand I installed a few media players because one thing I wanted to test was how well my laptop did multimedia stuffs in Linux because driver issues could be tricky.

---

### Post by C.S.Cameron on 2011-02-03
Google Chrome o/s might be a good starting point as it is based on Ubuntu and there is only a browser and Terminal, some versions will install stuff from Ubuntu repositories. 
Running an image installer will put the full version on flash drive.

For partitioning a Full install use 100 MB for FAT32, 3GB for /, 800 MB for /home, 100 for swap.
You can adjust partition size after using gparted.

You may not desire having /home and swap on a 4GB drive, may not be much use.

Best to disable internal HDD before installing.
Use manual partitioning to make sure boot loader grts put on the flash drive.

---

### Post by zer010 on 2011-02-04
Ok, I finally did the install. I used the Minimal image, but I guess I could have used the Alternate install.  I installed a CLI only base with this partitioning scheme: "/"=2GB, "/home"=1GB, "swap"=.25GB, and the rest I allocated to "/windows" as FAT32.  So far it's working pretty good. I installed xorg and now I'm just trying to decide what to install next. Of course I need to keep everything as small as possible.  I found this interesting tid-bit that I'm pondering .
> Display managers are different from window managers or Desktops.  Examples of display managers are kdm, gdm etc. While metacity, kwin and  sawfish are window managers. GNOME, KDE, Xfce and so on are called  desktops. A display manager provides the graphical login screen.
I'm not really interested in a graphical login, but I'd like a minimalistic GUI desktop.

---

### Post by Sylslay on 2011-03-25
I share a hint (some :-)) 

[http://ubuntuforums.org/showthread.php?t=1596497](http://ubuntuforums.org/showthread.php?t=1596497)

---

