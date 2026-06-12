---
title: "Problem with Grub"
date: 2005-06-29
forum: Installation &amp; Upgrades
---

### Post by renaden on 2005-06-29
Hey everybody!  Just wondering if someone would be able to help me with a problem I'm having.  I'm trying to install Ubuntu 5.04 from the install cd, but after completing the first stage, I get an error with Grub when restarting.  The error message is "GRUB Hard Disk Error".  I think this is just a problem with Grub though since it has failed on my computer when I installed it from Gentoo.  On the other hand, Lilo works fine, except I don't think there's an option for that in the Ubuntu install.  My computer is an Acer TravelMate C100 laptop, and I'm guessing the hardware for my laptop is kinda weird.  When booting the install CD for Gentoo, it is unable to detect any hard drives unless I specifically enable "doscsi" and "dopcmcia" in the kernel options.  Booting the Ubuntu install CD has no problems.  If anybody can help me out with this problem I'd appreciate it!!

Edit:  Funny how I only read the rules after I post.  I apologize for the mispost, and will welcome it if someone can move this thread to the appropriate section.  Thanks again!

---

### Post by Martin Witte on 2005-06-29
The ' noapic'  option is reported to do good work on laptops, although I did not had to add this myself on another model

---

### Post by renaden on 2005-06-30
Thanks for the reply!  I tried what you suggested and set the 'noapic' option when booting the installation cd.  Unfortunately it still gave me the same problem with Grub, being that it displays "GRUB Hard Disk Error" after rebooting from the first stage on installation.  I think the problem comes from Grub recognizing my hard drive however, rather than anything with the kernel.  If anyone can suggest something that might fix grub, or perhaps installing lilo as in alternative to grub, please let me know.

---

### Post by renaden on 2005-06-30
eh... well basically I figured out that you can install lilo using the expert settings in the install cd.  Case closed.

---

### Post by astronauta on 2005-10-13
Hi
-You must leave al least 8Mb of free space on your harddisk
- Install Ubuntu from CD
-Try to install GRUB in linux partition instead of MBR (I run in the same laptop Ubuntu  Hoary  and Windows).
- Reconfigure or add this entries in Monitor section of /etc/X11/xorg.conf archive because the screen appears too small. 
  
Section "Monitor"
	HorizSync	31-61
	VertRefresh	56-75
Those are the parameters that I tried to use and work properly.

I can not work with touchscreen, so if you make it please notice me.

Sorry for my English.

---

