---
title: "Triple boot with one OS on a separate drive"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by Nevon on 2008-01-22
Right now I've got a dual boot with Ubuntu 7.10 and Windows XP on the same harddrive. I love playing around with different Linux distributions - in a virtual machine right now. However, it's kind of boring not to be able to use 3D accelerated things. So now I want to install a new distribution on my second harddrive, alongside with XP and Ubuntu. 
Last time I did this, OpenSuse took over my computer for a while. When I started my computer I was thrown into OpenSuse's GRUB, where I could choose Ubuntu, which threw me back into my old GRUB. 
This time I would like to be able to boot into Fedora 8 (on the second harddrive) directly from Ubuntu's GRUB. If that's not possible, I'd like to at least get Ubuntu's GRUB FIRST, and choose Fedora's GRUB from there.

In short, I want to be able to choose between the following OS' in the same GRUB menu (Ubuntu's).
HDD 1:
Windows XP
Ubuntu 7.10
HDD 2:
Fedora 8

---

### Post by kellemes on 2008-01-22
You can let Fedora (or any other distro using Grub) install Grub, this will **overwrite** your current Grub-install from ubuntu.
You can fix this using [Super Grub Disk]("http://supergrub.forjamari.linex.org/") (download/burn/boot), you simply fix your Ubuntu-Grub-Install by overwriting the Fedora-Grub-Install.
So now you have your previous Grub-Menu back.

From Ubuntu you need to configure /boot/grub/menu.lst to list Fedora.
The best way to handle this is to simply point to the /boot/menu.lst Fedora created when it installed Grub. This way you create a nested-bootmenu, pretty cool.

The entry you need to put in you Ubuntu-menu.lst looks like this.
```

title Fedora
configfile   (hd0,0)/grub/menu.lst
```
The (hd0,0) you need to adapt to your situation, this depends on where Fedora is installed. It's need to point to the /(root)-partition of Fedora. So.. (disknumber, partitionnumber)

---

