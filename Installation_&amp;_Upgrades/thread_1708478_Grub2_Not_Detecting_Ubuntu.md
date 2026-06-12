---
title: "Grub2 Not Detecting Ubuntu"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by kjkoec on 2011-03-16
Hey all,
Recently I installed ubuntu on a WinXP machine.  Wanting to save boot time with windows, I didn't let grub install to the mbr, but rather, to a usb stick.  Oddly enough, now when I try to "update-grub" or just "install grub", the ubuntu partition isn't found.  Both windows and ubuntu are installed into the same disk.  Ubuntu is sda5, bootable, but still not found.   Any ideas what's causing this or what can be done?

---

### Post by drs305 on 2011-03-16
What do you want to do now? Do you want to install G2 normally to the MBR and let it handle both Ubuntu and Windows? Do you only want Ubuntu to boot with the USB drive inserted/connected? Also, is this a normal installation (and not Wubi, which wouldn't install to the MBR anyway)?

If you want to install Grub to the main drive's MBR, boot a LiveCD and run the following:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Don't use the partition number in the second command.

If you are still having problems, please post the contents of RESULTS.txt, which you obtain by downloading and running the boot info script from:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

