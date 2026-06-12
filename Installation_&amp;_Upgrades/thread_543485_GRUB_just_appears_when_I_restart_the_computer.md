---
title: "GRUB just appears when I restart the computer"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by jrojfer on 2007-09-05
Hi all Ubunters!

I have a strange behavior of my laptop... I have XP and Ubuntu 7.04. When I turn the computer on the grub doesn't appear and Ubuntu starts (default option), then if I restart the computer, the grub appears and I can choose...

If the default option is XP, the same happens... 

It is a toshiba laptop and in the beginning it shows a menu to choose the physical device to start from (HDD,CD/DVD,USB,LAN,...) and I think that maybe there is some kind of conflict between them. I don't know how to disable this menu...

Anybody knows how to avoid it?

---

### Post by Aetherius on 2007-09-05
if you open up a terminal and type

```
sudo gedit /boot/grub/menu.lst
```

this will open up the grub menu settings for editing.

In it there will be the option 

```
hiddenmenu
```

add a # (hash) in front of it to comment it out if you want to see the menu.

Its very unlikely that the boot-device menu at the start will conflict with grub. A more likely cause is possibly some software or scripts that change the grub menu, for example BootLoader manager.

Hope this helped.

---

### Post by jrojfer on 2007-09-06
Thank you Aetherius,

hiddenmenu option was already commented,  so the problem is still there, I think I should find the way to disable the boot selection menu and just to have the possibility of select boot device  by means of the BIOS.

Because it seems the boot selection screen gets stuck until the timeout set in menu.lst expires... and load the default option... what I don't know is why this is not happening when I restart but just when I turn the computer on...

Thank you anyway...

---

