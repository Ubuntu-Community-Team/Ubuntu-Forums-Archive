---
title: "Installation Problem Dell XPS 600"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by wreed on 2010-10-21
I have a old Dell XPS 600 with SLI Nvidia 7800s.  It has 3 gb of ram and has a 250 gb hard drive. 

I pulled down both 64bit and 32bit ISO's and burned them to DVDs.  I went through and tried to install either DVD and the system would hang on the Ubuntu with the red to white dots loading screen.  I read around and saw some information about running the install with nomodeset.  The installation goes through this way, I get all the way to the finished installation screen.  When I finish and it reboots this is where the system hangs.  I cannot get into Ubuntu.  I did see Kernel problems and saw that it was possibly a memory issue?  I ran the memtest last night and it came across no errors.

I did read something about "i915.modeset=1", would this pertain to the XPS 600 and do I do this at install?  I am at a loss as to why I can't install this OS.  BTW it's Ubuntu 10.10.  

Dell Stats.
Processor, 80547, Pentium 4 Prescott Dt, 640, SKT-T, Male
3gb RAM
Graphic, 256, 7800, GTX UHMGA13 (x2)

I can provide more error information if needed and will add more tonight.  Help! 

I did try the line about TRYING ubuntu without installing at the menu, when I did that it got into ubuntu but hung right before it finished loading the desktop.

---

### Post by wreed on 2010-10-21
Any ideas?  I cannot get it to install with other options besides nomodeset....

---

### Post by wreed on 2010-10-21
I got it to install on nomodeset but when it boots it just hangs....never makes it into ubuntu.
 
getting **Result**: **hostbyte**=**DID_BAD_TARGET**
 
Does that mean my drive is shot?  This machine hasn't had any problems with xp and vista....atleast hd wise.

---

### Post by wreed on 2010-10-22
Well I have since tried to do this...
Install on 250gb hd on sata0 with nomodeset - on reboot I can some call stack stuff an it just hangs
Install on 180gb hd on sata0 with nomodeset - on reboot I can some call stack stuff an it just hangs
Install on 180gb hd on sata2 with nomodeset - it hangs on reboot.
 
What gives, I just want this thing installed!

---

### Post by wreed on 2010-10-24
I was able to get into Ubuntu with adding this to the grub entry, took off quiet mode and put on 'single nomodeset i8042.nopnp' without the quotes.  I got into low graphics mode, then installed the nvidia driver and all was good.  The errors that show on the screen are so misleading, I thought I had a bad hard drive when all it was was an incompatible video driver.

---

