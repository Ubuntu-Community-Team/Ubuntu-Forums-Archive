---
title: "Ubuntu 8.04 on external HD wubi install"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by UWBernie on 2008-04-26
I'm new to Linux and I wanted to try it out so I started with a wubi install on my external HD (i have a laptop running XP w/only a 40GB drive) I went through the install and everything worked properly except I forgot my password, so knowing I didnt have anything but the base install the only thing I would loose was time i removed and attempted to reinstall.  

Now I cant get Ubuntu to boot.  I get an error 15 message from grub.  and when i tried to find the install path manually I cant find my External USB drive.  

Any Ideas. Thanks

---

### Post by goliath10 on 2008-08-26
I ran into the same problem, except cause my hard drive is full.
(Dell Dimension 4700, 2.8 ghz p4, 512 mb ram, 160gb WD sata internal hd, 


I suspect that at boot, even though the dell bios can read usb drives, but the grub is not by default configured to be able to read usb drives as the root drive.

for me (through winblows) the grub menu.lst file is located in H:/ubuntu/install/boot/grub/menu.lst

my grub knowledge is less than adequate, i installed it to a floppy about a year ago for a friend who needed to secretly have ubuntu installed. without his parents noticing.

im gonna boot into a live-cd and see if i can do a floppy, or find out where windows reads the first instance of grub from.

---

### Post by louieb on 2008-08-26
Not sure about a wubi install but if it were a traditional  install - to find where grub and your Ubuntu install are.

When you get to the grub menu** press c **to get a grub> prompt.
now let grub tell you where its at 
```
find /boot/grub/menu.lst
```

Ubuntuforums has a wubi sub forum - you may have better luck finding a fix there.

Goood Luck.

---

### Post by goliath10 on 2008-08-27
i found out at least my grub does not see the usb hard drive as a mounted drive, therefore since the grub files are on it, they cant be pointed to. 

hmmm.

---

