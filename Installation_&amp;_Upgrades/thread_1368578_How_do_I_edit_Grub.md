---
title: "How do I edit Grub?"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by Selur_Ku on 2009-12-30
I've got XP,Win 7 and ubuntu 9.1 on triple boot.

The grub menu defaults to Ubuntu, but I need to change the Default to Windows.

All the instructions I found said that I need to Edit the file /boot/grub/menu.lst

but there is no such file on my system.

I tried editing /boot/grub/grub.cfg using gksudo gedit /boot/grub/grub.cfg , but it wouldn't let me save changes

Is there some other way to do this ?

Thanks

---

### Post by Revolutionary101 on 2009-12-30
Install the program start up manager. It offers an easy way to edit Grub. To get it type this into terminal.

```
sudo apt-get install startupmanager
```

---

### Post by Moozillaaa on 2009-12-30
...unless he wants only to edit the GRUB menu:

> sudo gedit boot/grub/menu.lst

---

### Post by oldos2er on 2009-12-30
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by oldos2er on 2009-12-30
> **Moozillaaa said:**
> ...unless he wants only to edit the GRUB menu:

A fresh install of 9.10 uses grub2, which doesn't use menu.lst.

---

### Post by Moozillaaa on 2009-12-30
> **oldos2er said:**
> A fresh install of 9.10 uses grub2, which doesn't use menu.lst.

Yep - he did say that he doesn't have that file oops :oops: !

I kant reed to gud - publik skool grad!

---

