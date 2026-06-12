---
title: "Problem encountered deleting windows partition"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by qiemem on 2006-12-03
I recently deleted my windows partition. Here's what my partitions look like now:
/dev/sda1    ext3    25.00gb <--- my old windows partition, reformatted
/dev/sda4    unknown 7.84 mb 
/dev/sda2    ext3    28.59gb <--- my current linux partition
plus linux-swap

How can I merge sda1 and sda2? Right now, I can't use any of the space I freed up by deleting the partition! And I can't figure out how to move it with that unknown sda4 in the way (I was advised to leave it on there as it might contain important hardware troubleshooting software). Anyway, help with this would be much appreciated; I'm down to 150mb of space left on sda2 and so need theextra space pretty soon.

---

### Post by dcstar on 2006-12-04
> **qiemem said:**
> I recently deleted my windows partition. Here's what my partitions look like now:
/dev/sda1    ext3    25.00gb <--- my old windows partition, reformatted
/dev/sda4    unknown 7.84 mb 
/dev/sda2    ext3    28.59gb <--- my current linux partition
plus linux-swap

How can I merge sda1 and sda2? Right now, I can't use any of the space I freed up by deleting the partition! And I can't figure out how to move it with that unknown sda4 in the way (I was advised to leave it on there as it might contain important hardware troubleshooting software). Anyway, help with this would be much appreciated; I'm down to 150mb of space left on sda2 and so need the extra space pretty soon.

You may want to delete the new sda1 partition, and then try and move the sda4 partition to either the start or end of the disk (preferably the start).

If that works, then boot up off the Live CD and try and expand/move the sda2 partition into the space freed up by moving the other one.

---

### Post by qiemem on 2006-12-04
Unfortunately, I can't move sda4. In fact, I can't do anything with it except delete it or format it. Doesn't really make sense that it would've ended there in the middle like that though, does it? Anyone know if its safe to just delete it?

---

