---
title: "Can't edit menu.lst"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by mckinneycm on 2007-06-05
I'm trying to edit the \boot\grub\menu.lst file so that I have a Windows XP option, however, when I try to save the file it says I don't have permissions. How can I edit this file?? Thanks...

---

### Post by jfinkels on 2007-06-05
> **mckinneycm said:**
> I'm trying to edit the \boot\grub\menu.lst file so that I have a Windows XP option, however, when I try to save the file it says I don't have permissions. How can I edit this file?? Thanks...

Open it as root user:```
gksudo gedit /boot/grub/menu.lst
```Then edit to your heart's content and save it.

---

### Post by mckinneycm on 2007-06-05
> **jfinkels said:**
> Open it as root user:```
gksudo gedit /boot/grub/menu.lst
```Then edit to your heart's content and save it.

Thanks...I'm still learning this stuff. I can't wait until I can get rid of Windows.

---

### Post by jfinkels on 2007-06-05
> **mckinneycm said:**
> Thanks...I'm still learning this stuff. I can't wait until I can get rid of Windows.

I can't wait until you can get rid of Windows, either!

It takes some reading and experimentation to learn some of this stuff, but if you hang around the forums, you will learn a ton.

---

