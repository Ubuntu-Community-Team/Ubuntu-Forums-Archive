---
title: "cdemu"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by fireeee on 2007-03-10
Today i installed cdemu but it seems i have a little problem and i need some help.
when i try to load an iso i get this 

```
home@Asenov:~/Downloads$ cdemu 0 quake.3.arena.linux.sharereactor.MiCRo.iso
home@Asenov:~/Downloads$ sudo mount /dev/cdemu0 /mnt/cdrom
mount: mount point /mnt/cdrom does not exist

```

---

### Post by sup on 2007-03-11
for ubuntu it is /media/cdrom - but only if you do not have an actual cdrom in your drive.

you can also make a mount point:
```
sudo mkdir /media/cdemu_cd
```
or whatever you want instead of cdemu_cd

but for isos, you do not need cdemu, just
```
sudo mount -o loop /path/to/image.iso /media/cdrom
```
should work

---

### Post by fireeee on 2007-03-13
thanks very much \\:D/

---

