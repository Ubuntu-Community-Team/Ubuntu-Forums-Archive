---
title: "hda now showing as sda"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by tmbigrigg on 2007-04-29
When I was using 6.10 my hard drive was listed as hda when I upgraded to fiesty the drive had changed to sda... does anyone know why that is occuring?

---

### Post by floke on 2007-04-29
AFAIK its a standardisation change in the new kernel and nothing to worry about whatsoever.

---

### Post by matto3c on 2007-05-13
Standardisation ?

Now it's impossible for me to tune my harddrive performance by the HDPARM. The disk operation are more slow than before this upgrade and:

root@matto:/home/matto# hdparm -u1 /dev/sda

/dev/sda:
 setting unmaskirq to 1 (on)
 HDIO_SET_UNMASKINTR failed: **Inappropriate** ioctl for device

Some ideas?

Matto

---

