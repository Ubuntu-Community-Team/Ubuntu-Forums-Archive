---
title: "Is it possible....?"
date: 2005-12-05
forum: Installation &amp; Upgrades
---

### Post by chakra_dude on 2005-12-05
Good day friendly people. I have a just recently upgraded from Hoary to Breezy successfully. But when i boot up my system, grub recognizes 2 Ubuntu OS'es. Ubuntu kernel 2.10 and Ubuntu kernel 2.16. I assumed that the 2.16 is my Breezy. My question is very simple. Is it ok to remove the older one? It makes my siblings confused everytime they boot up the PC. (I dual boot with WinXP).

Thanks!

---

### Post by timfrost on 2005-12-05
[QUOTE=chakra_dude]Good day friendly people. I have a just recently upgraded from Hoary to Breezy successfully. But when i boot up my system, grub recognizes 2 Ubuntu OS'es. Ubuntu kernel 2.10 and Ubuntu kernel 2.16. I assumed that the 2.16 is my Breezy. My question is very simple. Is it ok to remove the older one? It makes my siblings confused everytime they boot up the PC. (I dual boot with WinXP).

Thanks![/QUOTE]
Those kernel numbers don't match what I expect to see.  The kernel version should be something like 2.6.12-9 or 2.6.12-10.

What is displayed by
  grep '^title' /boot/grub/menu.lst

You should get something similar to:
```

tim@marvin:~$ grep '^title' /boot/grub/menu.lst
title           Ubuntu, kernel 2.6.12-10-386
title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
title           Ubuntu, kernel 2.6.12-9-386
title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
title           Ubuntu, memtest86+

```
(As you dual-boot, there should also be an entry for the WIndows partition).

The above example is for breezy, having applied the security updates, which include a kernel upgrade.

Once we sort out the actual details, you could choose to remove the older kernel form the list.


Tim

---

### Post by chakra_dude on 2005-12-05
Yep you're correct. I just typed them from memory. I'm sorry.
These are the kernel numbers:
2.6.12-9 or 2.6.12-10.
So it's possible to remove th old kernel from the list.
Won't it mess up the grub or mbr if i accidentally do something wrong?(just to be safe)

Thanks

---

### Post by Pablo_Escobar on 2005-12-05
It's safe to remove the old kernel if You have no problems running the new one.
It's recommended though to have at least 2 kernels installed, in case one of them gets corrupted somehow (just to be on the safe side)

---

### Post by chakra_dude on 2005-12-05
Thanks bro!

---

