---
title: "Split 1.6mb .img file?"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by linuxisevolution on 2008-11-30
I need to fit a 1.6mb floppy .img file into a single 1.4mb floppy, so I would like to know if I could split this across two disks? The laptop doesn't have a cdrom drive and it's a powerpc, so I'm trying a Debian network install...

---

### Post by oldos2er on 2008-11-30
"man split" should tell you what you need to know.

---

### Post by puppywhacker on 2008-11-30
It depends a bit on what you want to achieve.

with "split" you can split a file into equal blocks, but with "superformat" you can format a standard HD floppy to be bigger than the normal 1.44MB. If your floppydrives supports that you can fit up to 2MB

[http://www.togaware.com/linux/survivor/Format_Floppy.html](http://www.togaware.com/linux/survivor/Format_Floppy.html)

however, floppydisks have become obsolete by CDROM's USB-Sticks, Network cards, 1.6MB images shouldn't need too much trouble to get transfered.

goodluck

---

### Post by Mark Phelps on 2008-12-02
Have used HJ-Split to split and join files.  Runs from Java so there is nothing to compile or actually install.

See the following link for info:

[http://www.freebyte.com/hjsplit/]("http://www.freebyte.com/hjsplit/")

---

