---
title: "[SOLVED] Stall during boot (v. 7.10)"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by susanto on 2007-10-21
Hi 

I did a fresh installation of Xubuntu 7.10 (I did also Ubuntu and Kubuntu with the
same result) for dual boot toshiba satellite laptop.

After GRUB, I got a message:
--> MP BIOS Bug 8254, timer not connected to IO-APIC

And the screen freezed. 
I wait for more than 10 minutes, nothing changed
I then hit alt-f1
I got a message:
kinit: name_to_dev .... try to resume image
kinit: no resume image, doing normal boot
.
A fresh reboot and as soon as the screen freezed I hit atl-f1.
The startup resume with another message:
--> 8139CP is not an 8139cp compatible chip

In both successful cases (after hit alt-f1), the system is operating normally,
but not if I didn't touch anything.

Any idea what is going on here and how to fix the issue ?

Thanks,

---

### Post by jbarnes53 on 2007-10-21
I am having the same issue...would appreciate any help in fixing it.  It boots fine after I press <alt> + F1, but if will stall with blank screen if I don't hit that key combination.

**Edit -- just figured out a work-around to my problem.  Went into boot/grub/ and edited menu.lst...removed "splash" option.  Now boots without delay.

---

### Post by susanto on 2007-10-21
Thanks for the solution. 
Also work for me.

---

