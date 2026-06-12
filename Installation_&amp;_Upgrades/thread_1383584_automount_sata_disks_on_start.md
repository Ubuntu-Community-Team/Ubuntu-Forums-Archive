---
title: "automount sata disks on start"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by thinking on 2010-01-17
hi all
i installed latest ubuntu server 9.10 on my mini itx board which i have 1 4gb IDE disk and 4x2TB sata disks attached
no i want those disks to automount on startup
is there a way without modifiying fstab?
the thing is, i want to expand the storage over time (next hard disks in a few months) and maybe a second mainboard in a year
so i need a simple way to mount everything without being to mainboard specific like doing fstab entries

any ideas for such a generalized problem?

thx

---

### Post by b0b138 on 2010-01-17
Well fstab entries have nothing to do with the mobo so that would be the way to go I would think,

---

### Post by thinking on 2010-01-20
excuse for my late response
ure right, fstab is not mainboard/hardware related - my fault

the problem i see with fstab is: its very tight bound to the OS
thus if i add hardware i have to check my harddisks for the UUID and modify the fstab

in the meantime i think i found the right direction
either i will use autofs or hal on my server
but im not yet sure how hal works on a server edition

from what i have read about hal the advante is that i have to install a few packages and copy a self made .fdi file in the correct directory
if i add a second box i can copy the exact same file and it works

well i hope it will work that way ^^
using this, in case a disk dies, i can format a new one e.g. on my local box, remove the broken disk from the removable hard disk drawer (hot plug) insert a new one and it will get automatically mounted

---

