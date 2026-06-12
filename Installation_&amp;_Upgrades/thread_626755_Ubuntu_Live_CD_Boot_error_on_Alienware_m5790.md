---
title: "Ubuntu Live CD Boot error on Alienware m5790"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by vvume on 2007-11-29
I tried booting off the kbuntu 7.10 live CD & gOS (latest version) on my Alienware m5790 (specs below) and both of them kept repeatedly crashing at the xserver startup. Fedora 8 (32-bit/64-bit) both booted successfully. I want to use kbuntu. Is there any incompatibilities between kbuntu and ATI x1800 graphics cards or the 1920*1200 screen resolution?

Alienware m5790
intel core 2 duo 2.167GHz
ATI x1800 mobility w/1920*1200 17" screen.
VIA SATA RAID (dual Hard Drives) - running in non-raid mode.
intel chipset/usb controller
hdd1 - seagate 100gb 7200rpm
hdd2 - toshiba 80gb 5400rpm

crash message. Unable to start xserver "the xserver restarted X times in Y seconds. do you want to continue?" (Fedora8 KDE Live DVD 32/64 boots ok).

---

### Post by crazywizzard on 2007-11-29
sounds like problems I used to have on one of my old machines.  If you get dropped to a terminal try running, as root:
```
dpkg-reconfigure xserver-xorg
```
and answer the questions based on your setup, select an ati driver or the vesa driver, I don't know what drivers are on the livecd.
For the screen you can always use the simple method and just tell it the size and let it guess the refresh rates, that should at least get you into x.

This is the way that always worked for me, but it might not for you.  Best of luck!

---

### Post by kjaada on 2007-11-29
I had a similar problem with my attempt to install any Ubuntu live DVDs 7.04,7.06 and 7.10 
other live cds worked ok.The problem was Bios settings.Set the bios to default setup and all is sweet.

---

### Post by Vyacheslav Sakhno on 2008-02-25
I have Alienware area-51 notebook with x1800.

After reading this manual:
[http://wiki.eyermonkey.com/My_Ubuntu_(7.10)_Installation#Booting_to_the_live_CD_with_Radeon_X1800](http://wiki.eyermonkey.com/My_Ubuntu_(7.10)_Installation#Booting_to_the_live_CD_with_Radeon_X1800)

i solved problem by doing:

sudo apt-get install xorg-driver-fglrx

and changing driver in xorg.conf from vesa to fglrx.

---

