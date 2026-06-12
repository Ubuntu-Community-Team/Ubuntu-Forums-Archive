---
title: "rescue grub"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by mirinamulhaq on 2010-06-22
hi i had i a dual boot win. 7 and ubuntu 9.10,recently i had some problem in my windows os so i restored the c drive to factory settings since both operating systems where in c drive so when i tried to boot grub was showing problem.the information displayed was
loading grub,
the file does not exist
rescue grub>
so what should i do to restore grub so that i can boot again into windows 7 and ubuntu without loosing my data

---

### Post by darkod on 2010-06-22
If you restored to factory settings it probably destroyed your ubuntu partition. You didn't have ubuntu from factory, right?

Boot with the ubuntu cd in live mode, and to check the partitions in terminal run:

sudo fdisk -l (small L)

---

