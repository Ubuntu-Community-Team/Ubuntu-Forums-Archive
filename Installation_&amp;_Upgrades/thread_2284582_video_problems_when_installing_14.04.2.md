---
title: "video problems when installing 14.04.2"
date: 2015-06-30
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2015-06-30
I recently posted a video problem related to installing 14.04.2 (ubuntu-14.04.2-desktop-i386) on a Dell Inspiron 1501 with an 80Gb HDD
("Mp-bios bug:8254 timer not connected to io-apic error on 14.04.2 install ")
[http://ubuntuforums.org/showthread.php?t=2283568&p=13309731#post13309731](http://ubuntuforums.org/showthread.php?t=2283568&p=13309731#post13309731)

which was deftly resolved by MAFoElffen

I have been able to boot to Ubuntu cleanly ever since.

embolden, I swapped in a 320Gb drive into the same 1501 and tried installing the same ISO (using the suggested trick of adding radeon.modeset=0 noapic to the boot line before installing)

everything seemed to install smoothly, on restart I got to the password login screen when Zapp! my screen goes all coloured lines.

I'm stumped because I thought I had replicated the steps that installed successfully on the 80Gb drive.

any suggestions to get me onto the 320Gb drive (which would make this old clunky laptop at least more practical.)

Many thanks

Peter

---

### Post by ajgreeny on 2015-06-30
The fact that you added the boot option **radeon.modeset=0 noapic** before booting the live system does not mean that the same option is transferred to the installed OS, I'm afraid.

If you can not get to a GUI in which to sort this out you will need to use the command line.
At login acreen hit Ctrl+Alt+F1 to go to a tty command line and login there with username and password (password will not show on screen but it will be entered; just type and hit Enter).

Now use command ```
sudo nano /etc/default/grub
```Use cursor keys to move to the line
 ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` and change it to```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0 noapic"
```
Use Ctrl+o to save (or overwrite) the file then Ctrl+x to close it and finally run command ```
sudo update-grub
```
If those boot options ypou mentioned were needed to boot the system they will now be utilised at every boot.
Good luck.  Come back again if that does not help.

---

