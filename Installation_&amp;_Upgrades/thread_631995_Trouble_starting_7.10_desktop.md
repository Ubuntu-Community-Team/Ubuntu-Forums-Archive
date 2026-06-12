---
title: "Trouble starting 7.10 desktop"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by abrunett on 2007-12-05
I'm trying to get going with Ubuntu 7.10 desktop.  I'm fairly familiar with Linux and Unix in general, longtime user of fedora and CentOS.  I am trying to install into a fresh partition, but can't get Ubuntu to completely boot off of the DVD to begin the process. More precisely, I think it boots, but I can't get a user interface. 

When I try to start the 7.10 install, the dvd  load proceeds until it runs /etc/rc.local, which reports OK.  It then appears to hang.  When I either power off, or hit control alt delete, it looks like Gnome is shutting down.  I can't seem to get past this.  I'm guessing it is having trouble starting X or finding the display. 

This is on a machine that is giving me fits with Fedora, too, so I suspect I've got a hardware config problem.  The machine is one I built myself, with an Intel 6600 core 2, Intel motherboard, and an ATI video card.  The fedora install is giving me fits with (I think) the SATA configuraiton, as Grub is having trouble locating the install.  

If this sounds familiar to anyone, I'd appreciate any hints or pointers.  I've checked out the hardwarew by booting knoppix, and everything is physically findable (for example, I can find and vi grub.conf), but I don't know where to go from here.  Knoppix works fine, so I think the hardware is OK at some minimal level.

Edit:
I should add, it's a 2 GB RAM machine with oodles of disk, 156 GB in the linux partition, the video card has 128 MB.  There aren't resource problems here.

---

### Post by sinsaru on 2007-12-05
I'm having what I believe to be a similar problem.  The problem occurs with both x64 and x86 versions.  I'm running on an Athlon64 3000+ chip, 2GB of RAM, and a Radeon x1650 GPU.  I've done some trolling and seen that the x1650 can have problems with desktop enhancements like Beryl but nothing this far.  I have tried running in safe mode install and also tried removing the Splash option to no avail.  The screen flashes several times; the first time my monitor tells me that the system is trying to send a resolution not supported (it supports up to 1600x1200) and then after several more flashes I'm told that the display system has had to reboot 6 times in 90 seconds. 

I am fairly new to linux but am familiar with UNIX through use of Mac OS X but this has me stumped.  Any help would be appreciated.

---

### Post by abrunett on 2007-12-05
Yeah, I'm suspecting the video card as well.  I've had video card issues with Fedora on this machine as well, and I'm also getting the monitor resolution message from my monitor.  I think X is having trouble getting to the monitor.  I may swap out the video card to see if that affects anything.

---

### Post by Pumalite on 2007-12-05
With an ATI, it's better to install with the Alternate CD.

---

### Post by Therion on 2007-12-05
This might help...  Try changing the resolution in /etc/usplash.conf to 1024x768:
   xres=1024
   yres=768

Then use: 
```
sudo update-initramfs -u -k `uname -r`
```

---

### Post by abrunett on 2007-12-06
While I haven't tried this with Ubuntu yet, I found the fix for the X problems for the fedora install, and I suspect this underlies my ubuntu issue as well.  I had to download and install the ATI drivers for the video card, after which X windows quit misbehaving.  Get the driver from ati.amd.com, and after running the installer, run "aticonfig --install -f" from a console.

---

