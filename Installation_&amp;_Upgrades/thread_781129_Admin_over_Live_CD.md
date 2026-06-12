---
title: "Admin over Live CD"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by mercury_may2112 on 2008-05-04
I currently have Windows XP and Ubuntu 8.04 each on separate hard drives and I'm getting GRUB 1.5 Error 21. I found a solution to the problem but I need administrative access over the Live CD. I know the password and everything but how do I load access? By the way this is my first Linux distro.

---

### Post by NightwishFan on 2008-05-04
Live cds run as root by default I believe.

---

### Post by mercury_may2112 on 2008-05-04
No. I need to save changes on /boot/grub/menu.lst but it won't let me.

I need to adjust all the Ubuntu things as hd0,0 and XP as hd1,0

---

### Post by NightwishFan on 2008-05-04
```
sudo gedit /path/to/boot/grub/menu.lst
```
or
press: alt+f2
```
gksudo gedit
```
Then open the file manually.

(remember anything on the live cd session itself isnt saved so you have to mount your ubuntu partition)

---

