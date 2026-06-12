---
title: "Ubuntu 8.04 install problem"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by prc292 on 2008-07-16
Hey guys,

im having a weird problem with the install of 8.04. im going to dual boot with windows. i have a partition for windows a 2nd partition for docs and media that is ntfs and a free space for ubuntu. so i go into the installer and get the manual partitioner going and make a 4 gig root and 11 gig home and then the rest of the space that should be for swap becomes unusable. no matter how i try to congigure the partitions the 3rd always becomes unusable. ive seen this problem plenty in google searches but haven't really seen an answer.

if anyone has an idea of what i did wrong, help would be much appreciated.

thx in advance

---

### Post by Pumalite on 2008-07-16
You are breaking the 4 primaries per drive rule. Put Ubuntu and /swap inside of an extended partition.

---

### Post by prc292 on 2008-07-16
That was the fastest response ive ever gotten in a forum!!!!

thx

did some searching i think i get what you mean. ill do some rearranging and give it a shot.

thx again

---

