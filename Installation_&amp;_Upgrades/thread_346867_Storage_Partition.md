---
title: "Storage Partition"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by jake3988 on 2007-01-26
Hi.  Apparently my Ubuntu partition (despite what I told it to do) only takes up 40G of space.  My hard drive is 250G

So... since I can't resize my partition, obviously, I was wondering if it was possible to create a new partition with no OS, simply there to mount with fstab and use as additional storage.

Thanks!

---

### Post by taurus on 2007-01-26
Yes.

---

### Post by Nik_Doof on 2007-01-26
Exactly what i've done, 15gb for /, 20gb for /home and 200gb for /media/sda5, really could do with remounting it in a better location, but it works for the mo :)

---

### Post by jake3988 on 2007-01-26
It needs to be a primary partition, correct?

---

### Post by taurus on 2007-01-26
No, they don't.  They can be logical partitions.

---

