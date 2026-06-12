---
title: "Display resolution is toasted after install"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by ttrimble on 2005-12-06
I just installed 5.10 under Virtual PC for the second time.  Even though I selected 1024x768 for the screen resolution, it came out to 1600 x 800.  Is there a way to change this under recovery mode?

---

### Post by Leif on 2005-12-06
sudo dpkg-reconfigure xserver-xorg, or just sudo gedit /etc/X11/xorg.conf and add the entries you need. you can also cycle through the available resolutions while linux is running using ctrl+alt+plus and minus - try that first

---

### Post by ttrimble on 2005-12-06
Well, the reconfigure process was pretty confusing (I'm a linux rookie.), and gedit does not run from the prompt (in recover mode).  I tried the ctrl+alt+ +/- and that did nothing.  

I'm excited about using Ubuntu due to the reviews and press, but I'm not interested in having to do a bunch of command line tweeking to get it to work.  I know this might be an issue of running under VPC, but it should still be able to detect the VPC configuration and go from there.

---

### Post by Leif on 2005-12-06
[QUOTE=ttrimble]Well, the reconfigure process was pretty confusing (I'm a linux rookie.), and gedit does not run from the prompt (in recover mode).  I tried the ctrl+alt+ +/- and that did nothing.  

I'm excited about using Ubuntu due to the reviews and press, but I'm not interested in having to do a bunch of command line tweeking to get it to work.  I know this might be an issue of running under VPC, but it should still be able to detect the VPC configuration and go from there.[/QUOTE]

try nano or vi instead of gedit then. the kind of problems you're having are uncommon, but yes, sometimes you do have to tweak to get things working.

---

### Post by ttrimble on 2005-12-06
Well, I tried nano /etc/X11/xorg.conf and the file is empty.  Any other ideas?

BTW: I appreciate your help on this.

Tim

---

### Post by Leif on 2005-12-06
did you do "sudo nano /etc/X11/xorg.conf" ?

---

### Post by ttrimble on 2005-12-06
Doh!  I added sudo and managed to get into the file this time.  I noticed that all of the configuration settings seemed to be fine.  So I did a little more research and discovered this site:

[http://vpc.visualwin.com/]("http://vpc.visualwin.com/")

Turns out that VPC won't work with the default bit depth of 24.  I changed it to 16, saved, and restarted. Now everything seems to work.

Thanks again for your help.

---

