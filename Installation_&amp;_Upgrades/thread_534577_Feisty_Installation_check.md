---
title: "Feisty Installation check"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by jdurand on 2007-08-25
This was originally posted in the beginners section, but apparently I'm past that.  :)

I am in the process of porting a small server over from OS X to Ubuntu, so I have experience in the Mac version of BSD (if you buy OS X Server, you spend a lot of time bypassing their "helpful" stuff).

I have installed Ubuntu on an ASUS P5VD2-MX SE motherboard and everything seems to be fine, I just want to check a few things.

1) I enabled the hardware RAID-1 controller on the motherboard. I use this with Windows all the time with no problem, but during the install Ubuntu showed two hard disks. It seems it should only see it as one (the array). How can I check that Ubuntu is actually using the RAID instead of only one disk, short of unplugging the other disk?  I also see there's a Linux VIA RAID driver from ASUS, but I don't know if I should attempt to install it.

2) The CPU fan on this system seems louder than our AMD Windows systems, does Ubuntu control fan speed? I've enabled all the automatic power saving options (like processor speed and voltage) in the BIOS, but I know the OS can override these.  Maybe the Intel processor is just hotter than the faster AMD ones?

3) I use RealVNC on Windows machines and CotVNC on OS X.  Using the default Ubuntu remote desktop, RealVNC works fine, but can't cut and paste (file transfer).  CotVNC runs REALLLLLLLLY slow and never did support cut and paste.  Any suggestions for which flavor of VNC server to install on Ubuntu?  The RealVNC encryption would be nice to enable, too.

---

### Post by jdurand on 2007-08-26
Additional info:  I'm now seeing hda:  Lost Interrupt messages so I'm guessing something definitely isn't right.

---

### Post by jdurand on 2007-08-28
I know nobody answered this (or even read it?), but I hate leaving a thread open.  

I did some web searching and found mentions of APM giving trouble, even though Ubuntu is supposed to disable it.  I removed the APM package from my install and there have been no more HDA errors (or errors of any other kind besides some with Evolution).  

I also read that Hibernate leaves the disk heads in the wrong state causing an emergency shut down of the disks.  I tried hibernate once and both disks shut down with a loud SNAP!, so I guess that's right.  As this is a server, I don't see a reason to use hibernate in the future, so this doesn't bother me, but I can see the concern for laptops.

The fan also sounds a bit quieter, so I think turning off the APM is allowing the fan control to work correctly.  Still noiser than our big AMD workstations, but this is Intel so I don't expect a lot.

---

