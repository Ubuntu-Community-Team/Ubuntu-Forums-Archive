---
title: "Problems with Live CD/Xorg config"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by xMore on 2007-05-13
Live CD is booting fine, except I'm getting the "no screens found" error. After viewing the error log, I see that it is trying to use my DISABLED Intel integrated graphics. My current graphics card is an nVidia Geforce FX 5200.

I saw in the xorg.conf error log that it was attempting to use PCI bus 0, device 2, function 0, which is the integrated graphics chip.

I need PCI bus 1, device 10, function 0, which is my nVidia card. I tried editing xorg.conf, and overwriting, but it's not letting me overwrite.

Any help on this would be great. I need to get this installed ASAP.

---

### Post by Scheater5 on 2007-05-13
To overwrite xorg you have to have root privilliges.  If you are using Gedit, the quickest way to do this would be to enter ```
sudo gedit /etc/X11/xorg.conf
``` into a terminal.  On the live cd you will not be prompted for a password, but on an actually install you will.  You will then be able to save over the xorg file.
I have never had this particullar problem, and I'm not sure from reading your post if you get to a graphical interface or not.  If you do not, you will have to access a terminal ```
alt+ctrl+F1
``` and then edit xorg in a command line text editor, like nano or, if you are familiar with it, vi.  Simply replace "gedit" with "nano" or "vim" in the above command

---

