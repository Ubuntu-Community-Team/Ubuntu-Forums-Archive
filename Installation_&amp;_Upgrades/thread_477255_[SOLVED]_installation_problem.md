---
title: "[SOLVED] installation problem"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by cyke on 2007-06-18
Hi, i have a toshiba laptop with 256mb memory and a windows xp home edition.  I run the ubuntu live cd from the cdrom drive and click the first option.  I managed to get thru the desktop although ive seen some error msg "buffer I/O error on drive fd0, logical block 0".  There are two icons on the desktop, "examples" and "install" so i click install to install ubuntu onto the hard disk.  after going thru more than 30 mins of installation including the video driver install, i restarted the laptop without the CD.  The OS would not boot at all.  What did i miss?  I want a fresh install and i can live without the Ms windows.  right now, im running ubuntu from the CD. 

im on it for 6hrs now, i think i need help already... :D

---

### Post by cyke on 2007-06-18
okay finally after my 3rd try in installing from the CD.  I got it to boot up but not into the graphical menu.  only up to the login prompt with an error failed to load module "nvidia" (module does not exist, 0.   I guess this is a video driver error.  how do i install a video driver?

---

### Post by Pumalite on 2007-06-18
> **cyke said:**
> okay finally after my 3rd try in installing from the CD.  I got it to boot up but not into the graphical menu.  only up to the login prompt with an error failed to load module "nvidia" (module does not exist, 0.   I guess this is a video driver error.  how do i install a video driver?

I assumed you have installed already and this is a boot problem due to 'Graphical Interface'. Use your live CD. Download from NVIDIA appropiate xxx.run file driver, place it in /home/<username>. Quit. Reboot. AT the prompt follow this:

[http://ubuntuforums.org/showthread.php?t=470821](http://ubuntuforums.org/showthread.php?t=470821)

Installing the driver is:

sudo sh NVIDIA-Linux-x86xxxxxx.run

The driver will compile the module and reconfigure your xorg file.

---

### Post by Pumalite on 2007-06-18
Assuming you have an NVIDIA card. Otherwise go to appropiate site.

---

### Post by Pumalite on 2007-06-18
Another solution, if you don't want to install propietary drivers:

At the command prompt: type sudo dpkg-reconfigure -phigh xsever-xorg

Then just select vesa as your video driver and use the space bar to select the resolutions
Then reboot.

---

### Post by cyke on 2007-06-19
thanks.  got it to work now.

---

