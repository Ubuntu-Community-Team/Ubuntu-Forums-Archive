---
title: "i find it weird that a -Floppy Drive- shows up in Nautilus"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by madjr on 2010-04-22
my computer(s) dont have floppy still they show up in nautilus

i mean who still uses that?

am on a 3rd world country and not even us would touch that

looks yucky ew..

---

### Post by linuxman94 on 2010-04-22
Check your BIOS and see if you have it set for a floppy drive.

---

### Post by Brian Vaughan on 2010-04-22
I'd been noticing that logwatch kept listing errors for my floppy drive, since I upgraded to Lucid Lynx. I almost never use it anyway, and I think there's some glitch with the hardware, so I disabled the floppy drive in my BIOS. An icon for it still appears in Nautilus, however.

---

### Post by bigsmitty64 on 2010-04-23
I had this problem a while back and It was fixed by going to  /etc/fstab  and  add a "#" to the beginning of this line:

```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```so it becomes this:

```
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```make sure to put a space after the #.  :) good luck,
Smitty

---

