---
title: "New Install"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by 56BelAir on 2007-09-06
I attempted to install Ubuntu desktop edition on a formatted hard drive on my E-4400 Gateway PC. I went through the disc integrity check option when I boot up, the disc checked out fine. I started the install and  it went through the boot sequence. When it appeared to be done booting, there was a tan screen in the background with a cursor I could move with the mouse. There was nothing else visible on the desktop. I believe the OS is running from the CD, not the hard drive. When the CD is not inserted and I try to boot, nothing happens. Below is the output of the display I am using. I did not download the Ubuntu Live! version. Please advise on how to install correctly and what is going wrong. Maybe the M5 Checksum should be performed on a new download.

sudo fdisk -l VGA Compatible controller ATI Technologies inc rage 128 PF/PRO AGP 4X.

I can try to get some screen shots if it will help diagnose. 

Paul

---

### Post by merlinus on 2007-09-06
Video card problems. You might try the Alternate Desktop install cd. It is text-based, but quite straightforward.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

Once installed, you can get to a gui by changing the video driver to vesa from a command line, and then search for and install the correct drivers.

You might post system specs as well.

-merlin

---

### Post by dabl on 2007-09-06
Is the BIOS set to boot the CD drive first?  Did you notice where it said it was installing Grub, in the very last step of the installation process? Merlinus is probably correct that it is a video/driver issue, but I want to make sure about the fundamental stuff too.  ;)

---

### Post by 56BelAir on 2007-09-06
BIOS is set to boot from CD first. However, without the CD, it does not boot at all. So I am assuming the software is not on the PC.  I set it to boot from CD first so I could install it on a blank hard drive.

---

### Post by merlinus on 2007-09-06
Seems it did not install.  The opening menu has an Install option, but that will only run the os in RAM so you can try it out.  

To actually install from the live cd, you need to click the Install icon at the top-left of the desktop once ubuntu is up-and-running.

-merlin

---

### Post by Pumalite on 2007-09-06
How did you format your hard drive?, and what did you have there before?

---

