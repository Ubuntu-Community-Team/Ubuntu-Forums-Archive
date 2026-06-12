---
title: "upgrade failed -- dpkg broken"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tehk on 2009-10-04
I switched repositories to Karmic and did an apt-get upgrade (about 536 packages to upgrade) along the way, dpkg broke and I was told to run the following command to fix it, but that command itself also broke. Need help to get back on path!

```
$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu43) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-9-generic
cpio: ./sbin/modprobe: Cannot stat: No such file or directory
cpio: ./sbin/depmod: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.31-9-generic
dpkg: subprocess installed post-installation script returned error exit status 1
```

---

### Post by dino99 on 2009-10-04
verify the sources.list : all the lines might only talk about karmic, remove or comment all the additional repo such as ppa, sources driver, ...

first, be sure your system is clean:

- sudo aptitude clean
- sudo aptitude autoclean
- sudo apt-get autoremove
- sudo update-manager -d ( or the classic way: update, safe-upgrade)

actual kernel is 31-11 so i'm surprised you talk about 31-9.

verify twice your sources.list

I suppose you have dist-upgrade Jaunty, so add os-prober & grub-pc, then
- sudo os-prober
- sudo update-grub2
- sudo grub-mkconfig

---

### Post by tehk on 2009-10-04
Solved my own problem... 

When I removed KSplice from the system, it left the modprobe and depmod files as pointers to modprobe.ksplice and depmod.ksplice when the actual files where modprobe.ksplice-orig and depmod.ksplice-orig. Renaming the files from .ksplice-orig to .ksplice fixed the problem :)

---

