---
title: "Installed on another laptop, moved Hdd."
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by Faithtoken on 2007-11-09
Hello :KS, I have a "Sceptre 7300" laptop, I want to install Xubuntu or Ubunto on it, Since there is no floppy and no cd-rom drive, me and some friends figured we could always put the hdd in a computer that has one, we install, and so far all right. :D
The problem comes when we move it back to my computer there is nothing on the screen, only black after booting Xubuntu, it probably has to do with the drivers being all wrong, but if I load in recoverymode, I can reach the console, could I do anything from there? :confused:

---

### Post by confused57 on 2007-11-09
> **Faithtoken said:**
> Hello :KS, I have a "Sceptre 7300" laptop, I want to install Xubuntu or Ubunto on it, Since there is no floppy and no cd-rom drive, me and some friends figured we could always put the hdd in a computer that has one, we install, and so far all right. :D
The problem comes when we move it back to my computer there is nothing on the screen, only black after booting Xubuntu, it probably has to do with the drivers being all wrong, but if I load in recoverymode, I can reach the console, could I do anything from there? :confused:
You could try:
```
dpkg-reconfigure xserver-xorg
```
Select "yes" to autodetect in the first screen.

---

