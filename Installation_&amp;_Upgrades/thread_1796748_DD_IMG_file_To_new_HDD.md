---
title: "DD IMG file To new HDD"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by chetanzcool on 2011-07-04
Hi ,

I recently had to update my HDD since I needed more space .

Hence I backed up my old 20 GB Linux HDD using the DD command and created a 20 GB IMG file.

I used this IMG file to be transffer to a 100 GB partition , however it just used 20 GB on this partition as well ! IE only 20 GB of space is available on the new 100 GB HDD !

---

### Post by Ad@m on 2011-07-04
DD does not manipulate the partition size, it cannot resize/shrink.

So after copying your 20GB img file to your 100GB drive, you must now resize the partition. Use a live CD and Gparted, although I suggest keeping your 20GB img file incase the resize goes wrong.

---

