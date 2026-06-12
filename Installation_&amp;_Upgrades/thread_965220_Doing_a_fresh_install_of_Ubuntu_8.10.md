---
title: "Doing a fresh install of Ubuntu 8.10"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by themusicalduck on 2008-10-31
Hey,

I'm planning to try and setup a dual boot with XP and Ubuntu 8.10. I'm thinking of either -

Partitioning my 250gb sata drive to fit windows and linux, and having my home folder stored on a seperate 80gb IDE drive.

or

Having the sata drive dedicated to linux (which I use the most anyway) and using the IDE for windows.

First off I want to make a backup of Linux so that I can keep at least my themes and configurations/menus. Drivers aren't so important since I feel like reinstalling them fresh anyway in the hope that some devices will work a bit better than they do currently.

Can I assume that if I make a backup of my home drive then most of the vital stuff/programs will be there? Is my home folder likely to fit on a 80 gb drive? This is a copy of Ubuntu studio with all ubuntustudio packages installed including a fair few windows games too like Orange Box and wow. If I look on properties for /home folder, it says the total is around 17gb.. which seems very unlikely for it to actually to be that small.

Any other tips or things I need to be careful about? Whenever I've installed things, I generally just have one drive dedicated to each OS.

---

### Post by rplantz on 2008-10-31
I have both a SATA and an IDE disk. I don't have Windows on any of the partitions, but do have various flavors of Linux, FreeBSD, and OpenSolaris. One of the problems I always need to fix when I do a fresh install is that grub seems to order the discs such that the IDE is hd0 and the SATA is hd1. I want my default to be the SATA and have set up my BIOS that way. So I have to go into /boot/grub/menu.lst each time and change hd1 to hd0 in the appropriate places.

When you first boot your system (before editing menu.lst) you can use the editing feature of grub to temporarily make the change so that the boot process will continue.

I'm sorry that I can't give more precise details here. I haven't done it for six months (about to do it again after 8.10 downloads), but hopefully this will alert you to a potential problem.

---

### Post by reiki on 2008-10-31
GRUB defaults to using IDE first when it's in a mixed system with SATA. This is not uncommon as older systems with mixed SCSI and IDE often exhibited this same behavior

---

### Post by meindian523 on 2008-10-31
/home is just your personal files.All the apps you installed as part of the ubuntustudio package don't reside on your /home,they reside in /usr or /bin.If you fresh install,you WILL lose all your applications and will have to install again(I'm assuming you mean a fresh install is a clean install from the CD)If you upgrade through update manager,you atleast have a chance of all your applications also being upgraded in the process.

---

### Post by themusicalduck on 2008-10-31
So my home folder only contains configuration files, wine programs and anything else I've put in it?

Most of my programs have been installed with the package manager. So if there is a way of keeping a record of what I already have installed, then could I get the package manager to reinstall everything after a fresh install?

Would this work if I installed with a standard Ubuntu CD? I had quite a few graphical problems with Ubuntustudio and would rather have the standard kernel instead of real-time, so it would be great if I could just reinstall Ubuntu and then install all my Ubuntustudio apps + other apps on top of that.

I also read somewhere that if I delete all of the hidden files in my /home folder then all settings and configurations would be reset. Is the case? Would it change anything else apart from configurations? Plus deleting wine programs? I might try and do that selectively for folders or all of them depending. The only configuration I really want to keep is my theme and compiz settings. But I guess it wouldn't be too hard to get those back to how I want if I lost them.

---

### Post by meindian523 on 2008-11-01
> **themusicalduck said:**
> So my home folder only contains configuration files, wine programs and anything else I've put in it?
Yes.
> **themusicalduck said:**
> 
Most of my programs have been installed with the package manager. So if there is a way of keeping a record of what I already have installed, then could I get the package manager to reinstall everything after a fresh install?
Synaptic,in Status>>Installed,will show you all the packages installed.I'm unsure of how you would save those markings though.
> **themusicalduck said:**
> 
Would this work if I installed with a standard Ubuntu CD? I had quite a few graphical problems with Ubuntustudio and would rather have the standard kernel instead of real-time, so it would be great if I could just reinstall Ubuntu and then install all my Ubuntustudio apps + other apps on top of that.
> **themusicalduck said:**
> 
I also read somewhere that if I delete all of the hidden files in my /home folder then all settings and configurations would be reset. Is the case?
Yes,that's correct.> **themusicalduck said:**
>  Would it change anything else apart from configurations?
AFAIK,no.> **themusicalduck said:**
>  Plus deleting wine programs? I might try and do that selectively for folders or all of them depending. The only configuration I really want to keep is my theme and compiz settings.
You can save your themes and compiz settings by backing up your .themes and .compiz folder(they are hidden in your /home/<username> folder.)

---

### Post by dcstar on 2009-02-02
> **meindian523 said:**
> 
........
Synaptic,in Status>>Installed,will show you all the packages installed.I'm unsure of how you would save those markings though.
........

Those are saved into a simple text file, which you can then use on a fresh system to have Synaptic reinstall *all* of the same packages you had in your old system simply by using the "File-Read Markings" function.

You simply save this Markings file onto a USB (or wherever) and use it when you have completed the fresh install and booted it up.

There is a command line apt-get way of doing this as well, but they both achieve exactly the same outcome and are ideal if you need to do a fresh installation of a version and have all the same packages installed as an old installation.

I found this feature extremely handy as I have a new Ubuntu install (same version) on my system to get around the pesky mouse-button freeze issue that is plaguing quite a few people.

---

