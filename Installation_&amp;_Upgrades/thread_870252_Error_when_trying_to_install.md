---
title: "Error when trying to install"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by jaaekfre on 2008-07-25
After I select the size of the partition (going for a dual boot with xp) and try to create it, an error comes up saying that the partition size isn't big enough. The partition size is 15 gig for Ubuntu. Isn't this enough? If so, what's going on?

---

### Post by Pumalite on 2008-07-25
What are you using to partition? Dual boot with XP or Vista?

---

### Post by jaekfre on 2008-07-25
dual with xp

---

### Post by jaekfre on 2008-07-25
correcting the above:

i've got 17.2 gigs for ubuntu and the error says "too small size"

---

### Post by Pumalite on 2008-07-25
What did you use to partition?
Post:
sudo fdisk -lu

---

### Post by jaekfre on 2008-07-25
i'm sorry, but i'm totally new to this stuff. all i can tell you is that i was going through the ubuntu install with the cd and i tried to set up the partition with XP having about 25 and Ubuntu about 17. Then the error came up when it was starting to make the partition.

---

### Post by avtolle on 2008-07-25
One query: did you defrag your XP first?

---

### Post by jaekfre on 2008-07-25
sure did

---

### Post by Pumalite on 2008-07-25
Get Gparted Live CD or use the Partition Editor to shrink XP ahead of time. In the 'free space', make 2 partitions: all minus 1 GB for '/'. The rest for /swap. Then install, go Manual and use the prepared partitions.

---

### Post by jaekfre on 2008-07-25
thanks, i'll try that

---

