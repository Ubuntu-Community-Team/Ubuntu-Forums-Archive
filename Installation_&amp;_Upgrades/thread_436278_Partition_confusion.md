---
title: "Partition confusion"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by geovino on 2007-05-07
What do you think I should do to solve the partition/hdd situation

View from GParted:

hdb: /dev/hdb1  7.81 GB ext3 (Warning: Unable to read the contents of this file system! Because of this some operations may be unavailable)

              hdb2 (extended) :  /dev/hdb5 (swap) 3.90 GB and /dev/hdb6  26.64 GB  ext2 

PCLOS ver. .92 is on the hdb6 partition. 

WinXP is on hda1 and Ubuntu 7.04 is on hda2 

Since I plan to install the Xubuntu 7.04 on this hdb hdd, would it be best to delete all these partitions and then install via live cd fresh and select use whole hdb hdd?

---

### Post by loserboy on 2007-05-07
1. are you trying to keep you pclos?
2. why a 3.9 gig swap?
3. that error on hdb1 means your going to have to format it anyway right?

looks like you could do like you said and just format all of hdb, whats on hd1 btw

---

### Post by geovino on 2007-05-07
I'm not trying to keep PCLOS, or may install new version later on.

There's nothing in hdb1 I don't remember how this happened. 

Can I just delete the partitions and then xubuntu will format and install?

---

### Post by floke on 2007-05-07
If you want to wipe entirely then yes - don't even think you'd need to delete - you should get the install option of using the whole disk.
To be doubly sure you could run an fsck on the partition - but it MUST be unmounted at the time!

---

