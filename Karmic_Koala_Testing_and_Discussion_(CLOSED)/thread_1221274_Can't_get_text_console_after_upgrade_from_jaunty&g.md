---
title: "Can't get text console after upgrade from jaunty&gt;karmic"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by doctordruidphd on 2009-07-23
I have done three upgrades from jaunty to karmic, and all wind up with the same problem.
In the grub menu.lst file, I usually specify a vga=791 resolution, to get a decent text console. If I do that, I cannot get any text display at all. The uspalsh screen works, but there is no plain text. Hitting CTRL-ALT-F2, or choosing "console login" from the login screen, results in a black screen. Same trouble if I use the "vga=ask" option, and choose anything other than spacebar. The only way to get text is to leave the vga= option out of the kernel line in menu.lst altogether. 
This is a 64 bit system using dual NVIDIA 9800GT cards, and the latest 185.18.14 driver (I have also tried the new 190.16 driver, same results).
Has there been some change to grub or the kernel, such that this function no longer works, or is there a different way of doing it?
Thanks for any help on this.

---

### Post by wayne_cat on 2009-07-23
vga=XXX does not work with kernel 2.6.31. This feature has been removed.

---

### Post by doctordruidphd on 2009-07-23
Thanks for the info. Is there any other way to set text resolution for the console screens?

---

### Post by wayne_cat on 2009-07-23
I don't know if KMS works with the current kernel and NVIDIA.

[http://ubuntuforums.org/showthread.php?t=1193947](http://ubuntuforums.org/showthread.php?t=1193947)

---

### Post by doctordruidphd on 2009-07-23
Thanks for the info.

---

