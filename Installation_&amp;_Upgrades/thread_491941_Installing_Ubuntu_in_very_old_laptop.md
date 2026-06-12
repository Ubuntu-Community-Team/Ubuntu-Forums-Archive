---
title: "Installing Ubuntu in very old laptop"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by parrimin on 2007-07-04
Hey. I was helping a friend of mine to install a linux distribution on a very old laptop. I cant remember now the exact model, but the processor is a AMD K6 with only 55MB of RAM. Yes it´s a rare amount of RAM, but that is what it says when booting.
We were trying to install xubuntu, but it needs 128 MB of RAM, so the installation fails. Next, we tried to install Vector Linux, a very light distribution, and it successfully installed. Only the wireless pcmcia card fails. We were trying to compile the drivers, but no manner. You have to understand we both are noobies...

My only experience in Linux, is installing Ubuntu from LiveCD on a "normal" PC, so i only know how to configure wireless if my distribution installs all for me... Our thoughts are, if Vector Linux is based on Xfce, we would be able to install Ubuntu in console mode somehow, and next install Xfce, doesnt it? And i think if Xubuntu needs 128 Mb of RAM is because of the LiveCD. So... My question is, what steps should we try to install in console mode? I download Ubuntu Server Install CD, or alternate? And next, i can install Xfce from Xubuntu, or i try to configure my wireless conexion in cosole with iwconfig, and install xfce-desktop from apt-get?

Please some help...

We want Ubuntu, because, if i want anything, i only have to add repositories, and apt-get install, and all runs OK!

---

### Post by Shin_Gouki2501 on 2007-07-04
XFCE it selfs requires very little, im also interested if xubuntu would work on a 55 MB RAM Laptop.

I heard some people did it with 96 MB RAM.

I Did once a ubuntu server install onto a P1 233 with 128 MB RAM and IceWM as WM.

---

### Post by dptxp on 2007-07-04
Make a SWAP partition of 1-2 GB at the end of hard disk first using GPARTED (Download it, burn the iso and boot with it to make the partition).

TRy after that. The SWAP partition shall remain, do not try to change it later with Xubuntu Live or alternate CD.

---

### Post by parrimin on 2007-07-04
I have 512 MB os swap partition at the end of the hard disk, but, i think this partition is only used by the SO when installed, not when installing it, so, i cant boot from live cd in my laptop. I need another way to install ubuntu

---

### Post by Shin_Gouki2501 on 2007-07-05
did u try alternate cd?

---

### Post by dptxp on 2007-07-05
> **parrimin said:**
> I have 512 MB os swap partition at the end of the hard disk, but, i think this partition is only used by the SO when installed, not when installing it, so, i cant boot from live cd in my laptop. I need another way to install ubuntu

SWAP is used by Live CD too. I could install on a machine with low RAM after I made SWAP. 512MB may work. Try to remove SWAP when you install using Live CD, you will not be able to do it.

---

### Post by kerry_s on 2007-07-05
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by parrimin on 2007-07-05
> **dptxp said:**
> SWAP is used by Live CD too. I could install on a machine with low RAM after I made SWAP. 512MB may work. Try to remove SWAP when you install using Live CD, you will not be able to do it.

Does it? Ok I´ll try, but i think laptop will be more time swapping than executing processes...

>  did u try alternate cd?
No, i didn´t. I opened this thread because i dont know if i need to install alternate cd, or server. And when installed, is there no X? Will i be able to install with apt-get xfce or fluxbox?

---

### Post by dptxp on 2007-07-05
> **parrimin said:**
> Does it? Ok I´ll try, but i think laptop will be more time swapping than executing processes...


No, i didn´t. I opened this thread because i dont know if i need to install alternate cd, or server. And when installed, is there no X? Will i be able to install with apt-get xfce or fluxbox?

SWAP can only help, used when needed, it does not slow you down, it can only speed up.
It  frees RAM for more RAM intensive jobs.

---

### Post by Shin_Gouki2501 on 2007-07-05
**->did u try alternate cd? **
I think u misunderstand!!
The alternate install CD brings u a fully working DESKTOP ubuntu ( what ever) edition.
the "only" diffrence to the "desktop" CD is that u install it in "text" mode, IMO thats all.

So u dont install ANY diffrent ubuntu "edition" its just a diffrent install method.

:)

Maybe u try fluxubuntu?
wbr Shin Gouki

---

### Post by parrimin on 2007-07-05
> **Shin_Gouki2501 said:**
> **->did u try alternate cd? **
I think u misunderstand!!
The alternate install CD brings u a fully working DESKTOP ubuntu ( what ever) edition.
the "only" diffrence to the "desktop" CD is that u install it in "text" mode, IMO thats all.

So u dont install ANY diffrent ubuntu "edition" its just a diffrent install method.

:)

Maybe u try fluxubuntu?
wbr Shin Gouki

Thats what im looking for! Ill try this weekend, now studying for exam...

---

### Post by Shin_Gouki2501 on 2007-07-05
good luck ^^

---

### Post by regomodo on 2007-07-06
assuming that your internet works with no setup, i would do a ubuntu server install then run

$ sudo nano /etc/apt/sources.list

and add

```
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe
```

next 

$ sudo apt-get update
$ sudo apt-get xterm nedit menus kazehakase alsamixergui thunar conky pypanel wdm xorg
$ sudo dpkg-reconfigure xserver-xorg

optional extras

$ sudo apt-get feh wine update-manager vlc synaptic rhythmbox gaim


If you want IceWM

$ sudo apt-get install icewm

I would forget all the icewm editors as, to be frank, they are shite. copy all files from the /usr/share/icewm to your icewm folder and edit the menu, toolbar, and preference files in nedit. Read through and you'll find it very self explanatory

$ mkdir ./.icewm
$ cp /usr/share/icewm ./.icewm

You'll need to add a file for items to start at login (i.e pypanel, feh)

$ nano ./.icewm/startup

and add programs to it making sure to add a "&" to every item. you have to make it executable

$ chmod +x ./.icewm/startup

Done. You wont have a shutdown option but that can be configured in scripts.

If you want openbox

$ sudo apt-get install  openbox openbox-themes obconf

You'll have to create an autostart script like in icewm but i can't remember exactly how. search.

I would not in any case install either ubuntu-desktop kubuntu-desktop xubuntu-desktop

55MB is just too little. Saying this, with icewm (excluding the pypanel setup) i have 34MB ram used at startup.

That was a bit lengthy but i could have gone into a lot more detail.

**To summarise do not install xubuntu-desktop.**

---

