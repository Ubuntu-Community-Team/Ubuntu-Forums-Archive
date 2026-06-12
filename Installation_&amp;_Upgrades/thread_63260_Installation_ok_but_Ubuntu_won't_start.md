---
title: "Installation ok but Ubuntu won't start"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by old_ford on 2005-09-07
I installed ubuntu on a compaq presario v2310 laptop with an AMD turion64 processor. The installation appears succesful but after I login to teh computer freezes on the splach screen.

Any Ideas????

---

### Post by Martin Witte on 2005-09-07
Could be a video issue. Try first the first step, if this is not the solution try the 2nd.

1 - Try to boot in failsafemode, edit the file /boot/grub/menu.lst (first make a backup, edit with command sudo gedit /boot/grub/menu.lst). Find the Ubuntu section here, it should look something like:

title Ubuntu
root (hd0,4)
kernel /boot/vmlinuz-2.6.10-5-686 root=/dev/hda5 ro vga=771 quiet splash
initrd /boot/initrd.img-2.6.10-5-686
savedefault
boot


make sure the line starting with 'kernel' has the vga=771, this is the setting for laptops.


2 - Try to boot in failsafemode, edit the file /etc/X11/xorg.conf (first make a backup, edit with command sudo gedit /etc/X11/xorg.conf), find section 'Device' - change entry 'Driver' to 'vesa' if it is something else. The vesa driver seems to work with most hardware.

Good luck!

---

### Post by old_ford on 2005-09-08
Method 2 solved my problem, thanks a million!

---

