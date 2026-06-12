---
title: "dual boot"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by sametime on 2008-04-25
I have installed ubuntu and afterwards xp on the second partition.  That made xp the only active OS and have lost any contact with ubuntu. How do I get the dual boot screen up ? The ubuntu partition is shown as unknown in xp. 


[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

---

### Post by logos34 on 2008-04-25
Reinstall grub to the mbr:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Boot back into ubuntu and add an xp entry to the bottom of menu.lst:

gksudo gedit /boot/grub/menu.lst

> title         Windows XP
root          (hd0,1)
makeactive
chainloader   +1

---

### Post by sametime on 2008-04-25
I really appreciate your help , thanks.

---

### Post by logos34 on 2008-04-26
> **sametime said:**
> I really appreciate your help , thanks.

Sure thing.

Mark thread as 'Solved.'  Enjoy ubuntu.

Oh, and windows will be able to read/write to ubuntu partitions if you install **fs-driver**.

---

