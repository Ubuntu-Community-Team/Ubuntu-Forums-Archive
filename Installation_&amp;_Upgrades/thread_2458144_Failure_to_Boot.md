---
title: "Failure to Boot"
date: 2021-02-17
forum: Installation &amp; Upgrades
---

### Post by tmhoule on 2021-02-17
HI all.  I had a system running kernel 4.4.0-201 and it prompted me to do a release upgrade; I don't know the LTS version right now.  It upgraded to kernel 4.15.0-135 but won't boot.  After GRUB, it immediately dies.  I can use Grub->Advanced to select the older kernel and boot fine.  What's the path forward here? Do I fix or remove 4.15.0 kernel?  I'm a strong Mac guy, and know commandline/bash well, but don't know Ubuntu.

---

### Post by CelticWarrior on 2021-02-17
Welcome.

By the look of it you were still using the old 16.04.
Better backup your personal files and install fresh 20.04.

---

### Post by Impavidus on 2021-02-17
Failed release upgrades are hard to fix. Try running a live disk of Ubuntu 20.04.2. It will come with kernel 5.8. If it works, install. That will save you another release upgrade two years from now.

Naturally, make sure you've got backups, but I assume you made those before upgrading to 18.04.

---

### Post by grahammechanical on 2021-02-17
Have you loaded with the 4.4 kernel and then run update/upgrade (or run Software Updater)? It might or might not help if you used Software & Updates>Additional drivers to revert to using an open source video driver.

When Grub fails to load a Linux kernel we usually get a grub rescue command line. That is not happening? Is Grub loading the 4.15 kernel? At what point do things just die? Do you get to the Ubuntu purple splash screen. Or the log in screen.

Ubuntu 16.04 used Unity 7 as the desktop environment and user interface. Ubuntu 18.04 uses the Gnome 3 desktop environment and Gnome 3 shell user interface. You may have been asked to authenticate the removal of obsolete packages. If you gave permission Unity 7 would have been removed. I know this happens because it happened to me. You also may be been asked to choose between the Light Display Manager (LightDM) and the Gnome Display Manager (GDM). If like me you chose Light DM then you will not get a login screen (greeter) because it is looking for the Unity 7 greeter and it has been removed.. 

Regards

---

