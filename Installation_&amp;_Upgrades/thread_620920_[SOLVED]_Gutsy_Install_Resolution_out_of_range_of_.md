---
title: "[SOLVED] Gutsy Install Resolution out of range of my Monitor..."
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by Mangrove on 2007-11-23
Trying to install Ubuntu 7.10 Desktop or server on a new computer.

CD boots to Install menu, I select "Start Install or Upgrade", the Ubuntu Nightrider screen comes up, then a curser in the upper left-hand corner, then blank screen and a floating message from my monitor "Unsupported resolution".

I have an embedded Nvidia Geforce 6100 (video card, detected by the nv driver) and a RCA l32wd22 HDTV as my monitor (I have an older smaller Xerox LCD that I swapped in to figure this much out). 

Is there a way to change the resolution of the install (and subsequently xorg) once it has started?

I had the same problem when installing CentOS, Dyne:bolic and other distros. I just want to not have to learn Magic to install a Linux Distro...

<b>**EDIT**</b>

I resolved this problem by digging up an old 17" LCD panel I had, Installing Ubuntu, Updating the Nvidia Driver (which gave me more "Screen Resolution" option), then setting the resolution to 1024x768x56 which I know works with my HDTV as my Windoze computers are set to those values.

Why the Ubuntu install program was set to 1280x1024x60 (when most people install Linux on older machines barely capable of 1024x768) is beyond me...

Thanks to all who bravely gave their support...

---

### Post by derby007 on 2007-11-23
Can you press: Ctrl-F1 or Ctrl-Alt-F1, to get you into a terminal screen, then login from there, and then modify with: sudo vim /etc/X11/xorg.conf.
Or maybe youve tried this already....

---

### Post by Mangrove on 2007-11-23
I can indeed get to a Terminal screen that way, but I haven't installed anything yet so there is no xorg.conf file to edit yet.

Is there a way to change the Install Gui resolution?

---

### Post by derby007 on 2007-11-23
Do you mean 'edit' the install disk, I know you can edit or create your own .iso file (google it !) but this requires a bit of knowledge/magic. 
Did you try the alternate CD ?

---

### Post by Mangrove on 2007-11-23
I would prefer not to edit the install disk (but I'll do it if that way works)...is there a command to change the resolution I can enter before selecting "Start or Install"?...

---

### Post by Mangrove on 2007-11-26
Bumping this for those who also had this problem. The Solution is in the EDIT of the OP...

---

