---
title: "Issue installing Ubuntu on older Compaq computer"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by jmbenson89 on 2008-01-10
I've search the other posts on the forum, and they are fairly informative.  But here's my issue:  I recently acquired several older iPaq desktop computers, and want to install Ubuntu (or Xubuntu) on them.

Specs (approx):
733 mHz Celeron processor
512 MB RAM
10 GB HD
USB mouse/keyboard
no CD/floppy drive

In the BIOS, I can boot to USB device, but it doesn't seem to recognize a bootable USB drive (I can boot from it on my newer desktop computer though).  Since there's no CD-drive, I removed the harddrive, placed it in my desktop as a second HD, booted from Xubuntu and installed Xubuntu on that HD.  When I replace it in the iPaq, it loads fine but hangs at "running local boot scripts (/etc/rc.local) [OK]".  I can CTRL-ALT-F1 to get a command line login prompt, but there seems to be a problem starting anything graphical (emacs, the desktop environment) but command line works (and VIM, etc.).

Does anyone have any suggestions?  Did I do something wrong by removing HD and installing w/ a different comp?  I was thinking maybe getting an external USB CD-Drive might solve the problem?

Thanks in advance.

---

### Post by Partyboi2 on 2008-01-10
Have you tried to reconfigure xorg?
```
sudo dpkg-reconfigure xserver-xorg
```
Choose your video driver from the list and answer all the questions it asks, if unsure just choose the default answers. If it does not work with your video driver then do it again but select "vesa" driver

---

### Post by jmbenson89 on 2008-01-10
Thank you, that worked to fix up X and start the desktop manager!

---

