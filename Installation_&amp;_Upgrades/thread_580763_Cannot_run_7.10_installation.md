---
title: "Cannot run 7.10 installation"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Brad Youngman on 2007-10-19
I upgraded to gutsy from fiesty. Gutsy ran fine. I tried different ATI driver settings for my ATI Radeon X800 SE display card, and now cannot log on to gutsy. I get a dark screen with vertical streaks. I can get a recovery mode # prompt. What do I do to reset my display settings to the original upgrade state, which worked?

---

### Post by DavidTangye on 2007-10-19
Replace /etc/X11/xorg.conf with an older one, eg xorg.conf.bak.
I **always** backup /etc/X11/xorg.conf before I change video settings, for this very reason.

---

### Post by Brad Youngman on 2007-10-19
Thanks for your reply. I am quite new to Ubuntu, and don't know how to back up the appropriate files - so no backup is available. What do I do now? Can I do: sudo apt-get install xorg-driver-fglrx fglrd-control ? Then sudo gedit /etc/X11/xorg.conf making sure that Driver ¨fglrx¨ exists in the file. I get this procedure from Sam's Ubuntu Unleashed, Installing Graphics Drivers, pg 71.

---

### Post by bigken on 2007-10-19
try this sudo dpkg-reconfigure xserver-xorg and select ati as your driver

---

### Post by Brad Youngman on 2007-10-19
Bigken - Thanks! I am up and running again. Your suggestion will undoubtedly be very useful in the future for other problems that I cause myself.

---

### Post by Shin_Gouki2501 on 2007-10-19
wasnt't bullet proof x supoosed to prevent such things(failsafe Mode)?!
Or did i get something wrong?!

---

### Post by bigken on 2007-10-19
> **Brad Youngman said:**
> Bigken - Thanks! I am up and running again. Your suggestion will undoubtedly be very useful in the future for other problems that I cause myself.


happy to see your up and running :)

---

