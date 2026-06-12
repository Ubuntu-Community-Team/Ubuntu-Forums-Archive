---
title: "floppy"
date: 2005-06-04
forum: Installation &amp; Upgrades
---

### Post by tikal26 on 2005-06-04
whe I try to use my floppy it saya that it cannot mount it. when I can see it but cannot open it because it says that it cannot mount. any ideas.

---

### Post by BabyUbuntu on 2005-06-04
try it.

mount /dev/fd0 /floppy
umount /dev/fd0 /floppy

/dev/fd0   --->                3.5-inch diskette in a: (1.44 MB)


thx

---

### Post by mingus on 2005-06-04
[QUOTE=tikal26]whe I try to use my floppy it saya that it cannot mount it. when I can see it but cannot open it because it says that it cannot mount. any ideas.[/QUOTE]

Places/Computer

Right-click on Floppy, click mount.  Icon will change to show mounted, double-click to open.  This requires the floppy to have been formatted with a file system that can be read.

If floppy is not formatted, go to Applications/System Tools/Floppy Formatter

---

### Post by tikal26 on 2005-06-04
[QUOTE=mingus]Places/Computer

Right-click on Floppy, click mount.  Icon will change to show mounted, double-click to open.  This requires the floppy to have been formatted with a file system that can be read.

If floppy is not formatted, go to Applications/System Tools/Floppy Formatter[/QUOTE]
 that's it it was not formatted, but how come? when I use my thumb drive I can go from windows to mac to linux with no prblem. maybe its a stupid question

---

### Post by mingus on 2005-06-05
My experience has been that the floppy mounts as long as it has been formatted with a *recognized* filesystem - my guess, any that can be used with #mount.  Basically, same as with Windows, whatever the OS can read.

Media can be written to without formatting.  For example, grub can be written to a floppy without formatting, and so the binaries written to it are not seen by Ubuntu or Windows.

My USB stick drive is different.  It has its own driver, which is recognized by both Linux and Windows.  Not the same as formatting.

---

