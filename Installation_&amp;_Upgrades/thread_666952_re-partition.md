---
title: "re-partition"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by TangoRom on 2008-01-13
Hello Linux World,

Is there any way I can re-partition the existing partition whitout loosing data ? (I mean w/o re-installing ubuntu from the scratch ?)
As you probably know already I'm new with Linux and I believe I reserved to much of a space for the  OS when I installed Ubuntu on my PC. (I have 2 sata 350gb/each and I installed ubuntu on a 80gb partition. rest is dedicated for storage/files...).
Do you have any suggestion how this could be done in a better way ?

Thx everyone

---

### Post by Partyboi2 on 2008-01-13
Use gparted on the live cd to resize the ubuntu partition to the size you want. You shouldn't have a problem, but like they say always best to backup your important stuff just in case.
So if you are wanting to decrease the size of ubuntu partition.
You would boot up with the live cd and start partiton editor (System>Admin>Partition Editor)
highlight the partition you want to shrink and click on "resize/move"
then enter the amount you want for that partition then "apply"
then with the space that has now been created after shrinking ubuntu you can resize one of your other partitions to take that space.

---

