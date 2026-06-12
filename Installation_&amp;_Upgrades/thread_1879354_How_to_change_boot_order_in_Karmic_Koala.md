---
title: "How to change boot order in Karmic Koala"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by Theophylact on 2011-11-11
This may have been answered elsewhere, but I can't seem to find it.

I've got Ubuntu 9.10 (32-bit) installed on an old Toshiba Satellite, double-booting with Windows XP. The boot order defaults to Ubuntu, and I'd like to change it to Windows.

I looked on Linux Questions, where the [answer to a Ubuntu 6 equivalent problem]("http://www.linuxquestions.org/questions/ubuntu-63/how-to-change-grub-boot-order-456724/") involved editing boot/grub/menu.lst, but that file doesn't seem to exist on my system. And "grub-menu.lst", which *does*, is only a sample file.

---

### Post by raja.genupula on 2011-11-11
get grub customizer from signature and by installing it you can do many operation on grub.

---

### Post by oldfred on 2011-11-11
Ubuntu 9.10 was the first with grub2 as the standard. Some may have grub legacy if the upgraded from an old verison. So if you do not have menu.lst you have grub2.

Grub Customizer has been updated for the very newest verison of grub2, but I would expect it to work on your version.

HOWTO: Grub Customizer Updated for grub 1.99
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html) 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Rubi1200 on 2011-11-11
Ubuntu Karmic Koala was the first Ubuntu to move from legacy-GRUB to GRUB2. As such, menu.list was no longer used.

The way to edit the correct files can be found here:
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

An easier way would be to use Grub Customizer:
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

However, I am not sure if it works with Karmic so you may want to ask in that thread first before installing and using it.

edit: and oldfred beat me to it :-)

---

### Post by Starfleet on 2011-11-11
What about using 'Startup Manager'. It allows just what you are looking for and is very easy to find and load in the software centre or Synaptic. You can also alter other settings too such as the default time spent in the boot menu giving you more time to select the OS you want.

---

### Post by oldos2er on 2011-11-11
> **Starfleet said:**
> What about using 'Startup Manager'. 

Startupmanager is no longer being developed, and its author recommends using Grub Customizer. 

[https://launchpad.net/startup-manager/+announcement/8300](https://launchpad.net/startup-manager/+announcement/8300)

---

