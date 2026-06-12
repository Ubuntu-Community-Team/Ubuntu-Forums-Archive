---
title: "Grub fails"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by collier on 2011-01-20
I have, for reasons I need not explain, completed a clean installation of Ubuntu 10.04.  As part of that process I reorganised partitions on my Ubuntu hdd.
Boot now gets to checking DMI pool data and reports "no such device", and falls back to "Grub rescue".
I have followed through the "official" Grub2 guide, and several other guides to reconfiguring, re-installing and oherwise tweeking Grub  -  to no avail.  I purged Grub2 and installed Grub.  It made no difference.
fdisk -l shows the partitions as they are.  All good.  But apparently there is somethihng wrong someplace.
At one point I saw a note about dbus uuid . . . I followed it to the man page and was less than enlightened.
Clearly, I am no afficionado.
Can anybody suggest a course of action that might resolve this problem?
John.

---

### Post by wilee-nilee on 2011-01-20
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by collier on 2011-01-20
Thanks for your prompt response wilee-nilee!
Problem is that I am working here on a different machine than the one that is in trouble.
In a while I may be able to get this thread up on the troubled machine.  I'll get back to you as soon as I can.
John.

---

### Post by collier on 2011-01-20
Well!  Not everything is gloom and doom!
After mucking about with this for hours, I decided to re-install taking the opportunity to make the root partition at the start of the disk.  It had prreviously been at the end.
Now we have a working installation again.
Any insight as to why this might be?

---

### Post by Bucky Ball on 2011-01-20
Don't know but rule of thumb is this order:

/ = first
/any-other-partitions
/swap = last

---

### Post by Bucky Ball on 2011-01-20
Don't know but rule of thumb is this order:

/ = first
/any-other-partitions
/swap = last

---

### Post by collier on 2011-01-20
Thanks.  I guessed there might be some such convention.

---

