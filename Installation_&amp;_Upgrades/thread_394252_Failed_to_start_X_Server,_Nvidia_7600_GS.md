---
title: "Failed to start X Server, Nvidia 7600 GS"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by Musicalmidget on 2007-03-26
Hi

I'm attempting to install Ubuntu to my secondary hard drive and dual boot it with XP Home.  For the moment, I'm using Ubuntu 5.10 as it's the only version I currently have an installation CD for.

I keep running into the error "failed to start x server".  After looking around the net for a while, I believe this is likely because my new graphics card (Nvidia 7600 GS) requires new drivers.  Unfortunately, I'm not sure about how to go about solving this problem.

The x server output shows the error "fatal error: no screens found".

If anyone can tell me what to do from here, I would very much appreciate the help.

Thanks. :)

---

### Post by zvacet on 2007-03-26
ctrl+alt+F1
```
sudo dpkg-reconfigure xserver-xorg
```
replace **nvidia **with **nv**
When you have GUI install nvidia drivers with Envy script

---

### Post by tgunner on 2007-03-26
Your just asking for trouble with such an old version of ubuntu. I doubt the newer nvidia drivers will run in it, and also doubt that the "nv" driver will support the 7600gs. For temporary video, you can do this:

1. At start up, select ubuntu 5.10 Recovery Mode from the GRUB menu

2. When that's done loading, run the command "sudo nano /etc/X11/xorg.conf"

3. Scroll down the to the Video card section, and change the driver to "vesa"

4. Press Ctrl + O, then Enter, and finally Ctrl + X

5. Run "sudo reboot now"

You should be able to get basic (800 x 600, 1024 x 768) graphics now.

---

### Post by Musicalmidget on 2007-03-26
> **zvacet said:**
> ctrl+alt+F1
```
sudo dpkg-reconfigure xserver-xorg
```
replace **nvidia **with **nv**
When you have GUI install nvidia drivers with Envy script

I've just given this a try.  Unfortunately, selecting nv had no effect.  I'm still getting the same error.

> **tgunner said:**
> Your just asking for trouble with such an old version of ubuntu. I doubt the newer nvidia drivers will run in it, and also doubt that the "nv" driver will support the 7600gs. For temporary video, you can do this:

1. At start up, select ubuntu 5.10 Recovery Mode from the GRUB menu

2. When that's done loading, run the command "sudo nano /etc/X11/xorg.conf"

It seems that /etc/X11/xorg.conf is completely blank and I'm unable to modify anything. :s

I'm not against upgrading to 6.10 if it's the only way to fix the issue.  I've just been trying to save a little time for the moment.  If I were to upgrade however, how should I go about doing so?  I'm assuming that simply formatting the disk and installing the new version isn't the best method since I'm dual booting and GRUB is installed on the other drive.

Thanks for the help so far. :)

---

### Post by tgunner on 2007-03-26
If GRUB is on the other hard drive, then you should not have too much trouble with reinstalling... I think, I haven't worked much with GRUB.

---

### Post by Musicalmidget on 2007-03-27
Hi again.

It seems when I was attempting to modify the /etc/X11/xorg.conf file, I wasn't capitalising the X in X11.  I've now successfully modified the file now and do indeed now have 1024x768 graphics now.

I'll now set on upgrading to the latest version.

Thanks for the assistance. :)

---

