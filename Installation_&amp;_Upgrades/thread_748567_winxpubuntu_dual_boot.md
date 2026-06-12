---
title: "winxp/ubuntu dual boot"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by Belak on 2008-04-07
My reccomendation would just be to change the default boot option in grub, and leave them in the same order, so when the core of Ubuntu (The Linux Kernel) is updated, the boot list won't have to be changed every time.

Here's how to change the default boot partition in grub:
Hit Alt+F2 (In ubuntu)
In the box paste in
gksu gedit /boot/grub/menu.lst

Then (If you only have Ubuntu and Windows installed) find the line that says
default		0
and change it to
default		3

The numbering starts at 0, so 0 will be the first entry, 1 will be the 2nd... etc.

EDIT:
If you want to do it the way you wanted to, you will have to update the list each time there's a Kernel update (I think)
But anyway,
Hit Alt+F2 (In ubuntu)
In the box paste in
gksu gedit /boot/grub/menu.lst

Then scroll down to something like the following (basicly the entry with the title Windows)
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
and move it above all your linux entries which should look something like the following:
```
title		Ubuntu 7.10, kernel 2.6.22-14
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2c552af7-35a5-4647-9648-3cbcc79d2eab ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
```

---

### Post by dorath on 2008-04-08
> **damd70 said:**
> After installing ubuntu on a winxp, I'm offering to select ubunto or winxp as a dual boot option.
How can I change the order of these options?

At present, I have ubuntu on top and then winxp. I need to move winxp on top.

any kind of help is much appreciated.

Just to be clear, are you using the Ubuntu or XP boot loader?

---

