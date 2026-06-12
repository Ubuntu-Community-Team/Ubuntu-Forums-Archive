---
title: "[SOLVED] Update manager Stalled... help!"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by Spoonite on 2008-06-03
Hi,

I was just doing a routine update of all packages with the Update Manager and now I have a tricky situation where the installation of the updated packages has stalled/paused. 
The reason for this is because it updated my kernel to 2.6.24-18 and when it asked me if i wanted to replace my menu.lst file i selected something like "open in new shell..." (i can't quite remember exactly). But anyway, when i clicked that the window froze up and went that dark blackish sort of colour. I waited a while but it was not doing anything and it did not revive itself. So i forced it to quit. 
The problem now is that the update manager is waiting for feedback about the menu.lst file... but it cannot get it. So it has just hung.

Here is the current output from the 'Installing Software' window:

[COLOR="DimGray"]Preparing to replace linux-headers-generic 2.6.24.17.19 (using .../linux-headers-generic_2.6.24.18.20_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
root@spoon-laptop:/# [/COLOR]

Does anyone know what I can do??? 

I don't really want to have a heap of installed packages lying around the OS.

---

### Post by Sam Lars on 2008-06-03
In the terminal, if you do a
```
sudo apt-get upgrade
```
Do you get the same thing?  Does it install any of the other packages that are waiting around?

---

### Post by Spoonite on 2008-06-03
It essentially just says that it is locked and cannot be used because the update manager is already running.

Here's a printscreen...
[IMG]http://brendan.carne.googlepages.com/ApplyingChanges.png[/IMG]

thanks!

---

### Post by Bubba64 on 2008-06-03
You probably have to run sudo dpkg --configure -a in the terminal to get it running the upgrade again, then run the sudo apt-get update then
sudo apt-get upgrade. you always have to run update for upgrade to work as far as I know the dpkg instructions may not be needed but they will not hurt anything.

---

### Post by Spoonite on 2008-06-03
Thank you so much. That worked perfectly. sudo dpkg --configure -a got the update manager going again (after i shut it down). It's all working great!

Thanks to both of you for your quick responses!

---

### Post by Bubba64 on 2008-06-03
> **Spoonite said:**
> Thank you so much. That worked perfectly. sudo dpkg --configure -a got the update manager going again (after i shut it down). It's all working great!

Thanks to both of you for your quick responses!

That little bit of info will save your booty in many situation so make sure you save it.

---

