---
title: "GRUB menu"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by milesofjazz on 2006-11-13
I need some help with the GRUB menu when my computer boots. I have Windows XP on one hard drive and Ubuntu on the other. what I would like to do is have Windows boot automatically instead of Ubuntu (I'm sorry, I've just began using Ubuntu and still do most of my work on Windows). I've tried to edit my menu.lst file so that Windows will boot but Ubuntu says that I don't have permissions to edit the file because I am not the owner. Is there another way to edit the GRUB menu? That's the only way I've found and it doesn't seem to work for me.

Thanks,
milesofjazz

---

### Post by taurus on 2006-11-13
Open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo cp /boot/grub/menu.lst  /boot/grub/menu.lst.bak
gksudo /boot/grub/menu.lst
```
Now, change the "default" value from "0" to whatever entry your Windows is on, usually 3--the fourth entry...

---

### Post by ThrobbingBrain66 on 2006-11-13
type
```
sudo gedit /boot/grub/menu.lst
```

to edit the file.

at this point, you just have to edit the line that says 'default     0'.  you have to change the '0' to whatever partition your XP is on.

REMEMBER: 0 = the first partition, 1 = second partition

EDIT:  arg, you beat me to it.

---

### Post by taurus on 2006-11-13
> **ThrobbingBrain66 said:**
> type
```
sudo gedit /boot/grub/menu.lst
```

to edit the file.

at this point, you just have to edit the line that says 'default     0'.  you have to change the '0' to whatever partition your XP is on.

REMEMBER: 0 = the first partition, 1 = second partition

EDIT:  arg, you beat me to it.
It's a good idea to use gksudo instead of sudo when you use gedit...  And if you want to use sudo, then use it with nano.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by linuxuser28 on 2006-11-13
Is it different if you are using Kubuntu, because it is not working for me. ](*,)

---

### Post by taurus on 2006-11-13
> **linuxuser28 said:**
> Is it different if you are using Kubuntu, because it is not working for me. ](*,)
Open a terminal and type

```
sudo nano -Bw /boot/grub/menu.lst
```

---

### Post by streeto on 2006-11-13
It's safer to put the "Windows XP" partition first in the list, and leave '0' as default. That is, put windows entry before the statement

### BEGIN AUTOMAGIC KERNELS LIST

This way, if a system update inserts another kernel entry, grub will not boot the wrong partition by mistake.

---

### Post by milesofjazz on 2006-11-13
Thanks for all the input everyone, I am brand new to this Linux stuff.

One more question, does it matter that Windows is on a seperate HD? I seem to think that actually makes things easier, but does anyone know of any particular problems in reltionship to the changing the GRUB menu I night run across because of this?

Thank again,
milesofjazz

---

### Post by infoseeker on 2006-11-13
My WinXP is on hda1 (was there from before Kubuntu days) and my Kubuntu is on hdc1 (second harddisk) and my Ubuntu is on hdc6 (because it seems more popular than Kubuntu so I had to try it too :) ).  Still trying to find out which I prefer, Kubuntu or Ubuntu....but I'll keep trying :).

Works fine for me.

---

