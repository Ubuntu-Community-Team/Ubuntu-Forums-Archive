---
title: "Viewing other partitions and HD"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by brk292 on 2005-07-10
Hi,

Since I can't edit fstab or  grub to make Ubuntu recognize other partitions or HD diferent than the "/", some one could helpe me ? 
(after Ubuntu Grub Install I lost the ability to boot my previos Linux distro)


My PC.

Dell Dimension  8300
Speed 3.0 Ghz
RAM 512 MB
Video nVidia GeForce 2 @ 128 MB
Sound SounBlaster Live!
HD  80 GB  hda1 30 GB FAT32 used to store files I shared with other OS
                  hda5 20 GB Linux Ubuntu
                  hda6 20 GB Linux Mepis 3.3.1 (It works until Ubuntu Install)
                  hda7 512 MB Linux Swap


Thanks, Paul

---

### Post by dave9191 on 2005-07-10
Why cant you edit fstab or grub ?

---

### Post by manicka on 2005-07-10
[QUOTE=brk292]
Since I can't edit fstab or  grub to make Ubuntu recognize other partitions or HD diferent than the "/", some one could helpe me ? [/quote]

sudo gedit /etc/fstab

sudo gedit /boot/grub/menu.lst

---

