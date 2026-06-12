---
title: "How do I restore a prior kernel?"
date: 2005-12-04
forum: Installation &amp; Upgrades
---

### Post by wagdog on 2005-12-04
Long story short: When my kernel was automatically upgraded to 2.6.12-10 my CD-ROM and USB drives stopped working.  I found a bug report that seems to relate to this but none of the suggested fixes worked for me so rather than chase my tail I'd just like to go back to 2.6.12-9 (where everything worked fine).  Ploblem is, I have no idea how to do this.  Caveat: I'm a noob so please speak slowly and clearly.

---

### Post by bwog on 2005-12-04
Arent there options in the grub menu for each kernel?

---

### Post by wagdog on 2005-12-04
Thanks bwog for the quick reply!  What is a 'grub menu' and how do I get to it?

---

### Post by bwog on 2005-12-04
When you start the computer, one of the first screens you get is a menu that with options for the kernels and for windows (if you have windows installed). That is the grub menu, grub is the program that manages these choices. This screen is shown before ubuntu or windows starts.

---

### Post by doitashimashite on 2005-12-04
Take a look at your

/boot/grub/menu.lst

file (or post it here).

The bootable harddisk partitions each have a section, beginning with "title" (only count those without a "#" at the beginning of the line). The first section is number zero.

So the line

default 0

means: boot from first section.
Now lookup which section corresponds with the kernel you want to boot (your previous kernel) and change the zero in the line "default 0" into the corresponding section number.

You can also post your /boot/grub/menu.lst here, and I will help you out.

---

### Post by wagdog on 2005-12-04
bwog - When I start my machine it goes straight to the user login screen, no selections given.

doitashimashite - Thanks, I did as you suggested (changed 'default 2') and it worked perfectly, booted from kernel 2.6.12-9.  Unfortunately, it still didn't fix my problem (unable to mount CD-ROM and USB devices)!  Oh well, I guess it wasn't the kernel's fault after all (if I boot from the Live CD everything works perfectly as well).  Apparently, my quest continues.....

---

