---
title: "grubconf"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by tintix on 2007-01-16
Hi there! Need help. Where can I download grubconf .deb package? ](*,)  Can't find anywhere... :confused:

---

### Post by Fabioamd87 on 2007-03-05
true, where is it?

---

### Post by rsambuca on 2007-03-05
The website says it was "retired" in 2005 and suggests people use "gnome system tool" instead.

---

### Post by Fabioamd87 on 2007-03-05
i have gnome system tool, but i cant find this grub manager!?!?

:guitar:

---

### Post by tintix on 2007-03-10
AND I don't use GHOME.:mad:  I HAVE KDE!!! So where's the tool for KDE to configure grub??? :confused: :confused: :confused:

---

### Post by confused57 on 2007-03-10
Who needs grub.conf, when you have menu.lst to configure grub.

```
gksudo gedit /boot/grub/menu.lst
```

```
kdesu kwrite /boot/grub/menu.lst
```
menu.lst is short for menu.list

I'm not sure what the grubconf .deb package is, but configuring menu.lst should be all that's needed.

You might want to check out the grub section in the first link in my signature.

---

### Post by Fabioamd87 on 2007-03-10
i wont to configure grub without touching a line of code :)

---

### Post by rsambuca on 2007-03-10
> **Fabioamd87 said:**
> i wont to configure grub without touching a line of code :)

Is there a reason you are afraid of using the terminal?  It really isn't that difficult, and everyone is trying to help you here.

---

### Post by Fabioamd87 on 2007-03-10
yes i know, but for use my pc i dont need to know how grub work, only setup it by a GUI
(everything in Ubuntu have a GUI, why grub no?)

---

### Post by Herman on 2007-03-10
Hello Fabioamd87, 

How about this, 
**[SCRIPT: [B]GrubED** - GUI Grub editing - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?t=228104")[/B]


That should make you happy! :)

Regards, Herman  :)

---

### Post by Fabioamd87 on 2007-03-11
nice, when will be possible also to move the kernel in the list? is possible to implement it?
i have saved this apps :)

---

