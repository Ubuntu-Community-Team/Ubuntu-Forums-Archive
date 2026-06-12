---
title: "Just installed ubuntu-19.04-desktop-amd64 and no text is visible"
date: 2019-07-13
forum: Installation &amp; Upgrades
---

### Post by gohokies95 on 2019-07-13
I just installed ubuntu-19.04-desktop-amd64.iso. Clean HD, brand new install.  After boot, I squeaked by the login screen and get windows with no text. In the screenshot, the purple blob in the top left is a gnome-terminal after ls -la<enter>.  Usually the middle white rectangle is a welcome to ubuntu?  How do I fix?
[ATTACH=CONFIG]283619[/ATTACH]

---

### Post by gohokies95 on 2019-07-13
Interesting symptom: Back on login screen there is usable input/output, and when I click on the power icon in the top right, I get the Volume control. I can log in on pw screen. but the previous screenshot still prevails

---

### Post by oldfred on 2019-07-13
Strange graphic?

What brand/model system?
What video card/chip do you have?
If you can get to terminal:
lspci | grep VGA

Have you updated UEFI from vendor. 

Is Ubuntu fully updated?
sudo apt update
sudo apt upgrade

---

### Post by gohokies95 on 2019-07-16
nothing was updated.  It is a stock AMD 64 HP Pavilion.  Updated or not, these are initial screens out of box from a fresh download (of yes experimental ver) ubuntu-19.04-desktop-amd64.iso.  I am confused, how would UEFI effect a working version of the OS.  Would't a bad UEFI mean that it wouldn't boot at all?

---

### Post by oldfred on 2019-07-16
UEFI interacts with drivers.
       Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching.  
Both Windows & Linux kernel have been updated, and will probably need future updates as new variants seem to be found.

---

