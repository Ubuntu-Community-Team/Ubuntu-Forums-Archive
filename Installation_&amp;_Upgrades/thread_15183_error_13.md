---
title: "error 13"
date: 2005-02-12
forum: Installation &amp; Upgrades
---

### Post by vbouw on 2005-02-12
I tried to install ubuntu I386 on a 350 cpu with 256 internal memeory.
Until reboot then it says: ERROR 13!
What does this mean?

---

### Post by kultuur on 2005-02-12
From the GRUB manual:
```
error 13 : Invalid or unsupported executable format
This error is returned if the kernel image being loaded is not recognized as 
Multiboot or one of the supported native formats (Linux zImage or bzImage, 
FreeBSD, or NetBSD).
```
It means that your boatloader (= GRUB) wasn't configured correctly during installation.

---

### Post by vbouw on 2005-02-13
And what about:ERROR 18?

---

### Post by kultuur on 2005-02-13
[Error messages reported by GRUB](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2%20errors) 
[GRUB Manual](http://www.gnu.org/software/grub/manual/html_node/index.html)

---

