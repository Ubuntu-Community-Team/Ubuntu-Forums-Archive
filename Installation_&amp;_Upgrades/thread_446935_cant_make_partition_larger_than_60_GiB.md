---
title: "cant make partition larger than 60 GiB"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by 24x30cl on 2007-05-17
Ive allready done an install of Kubuntu (Feisty) to get a feel of it all. So far so good, but now i want to do the install "for real"

i have a 500 GB Seagate (7200.9) disk on which my install is going.

i want to partion it something like the following:

primary1: /boot (100 MiB)
extended
logical1: / (5 GiB)
logical2: swap (1536 MiB)
locical3: /home (rest save 20 GiB)

problem is, during the (live/desktop) install when i try to make the large (400+ GiB) partition, it starts calculating everything, but then it turns out ALOT smaller (usually 62553 MB, but sometimes around 50 or 70 GiB).

im wondering: WHY?

i know it cant be a limit on ext3, and i havent found anything that states that it could be the Silicon Image Sil 3112A SATA chip on my mobo that limits anything..... so does any of you know whats going wrong?

(also QTParted wont let me repartition, since the swap partition stays mounted if i boot from the live cd)

thnx in advance

---

