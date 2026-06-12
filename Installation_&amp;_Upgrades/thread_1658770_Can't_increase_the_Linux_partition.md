---
title: "Can't increase the Linux partition"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by chuchi on 2011-01-03
Hello friends!! I have this problem. I wanted to add space to my Linux partition, from the Windows partition, so I booted with the Ubuntu CD, extracted 10Gb from Windows partition but it doesn't allow to increase the Linux partition, neither to the Swap partition. I'm only be able to allocate the new free space to the Windows partition again!!! Why???

Thank you very much!!

---

### Post by karthick87 on 2011-01-03
Open Gparted and post a snapshot of your partition information here..So that we can help you..

---

### Post by chuchi on 2011-01-03
Here is the snapshot. thanks

---

### Post by dino99 on 2011-01-03
as you can see, /dev/sda2 3 5 are locked, you need to unmount them first

---

### Post by chuchi on 2011-01-03
"umount /dev/sda2" doesn't allow umount /dev/sda2. It said /dev/sda2 is busy. I think it's due to I am working in Linux partition,i.e /dev/sda2. So I booted from Ubuntu CD again,  executed gparted and tried to resize /dev/sda2. Here is a new snapshot. As you can see, it allow me reduce, but doesn't increase /dev/sda2.

---

### Post by karthick87 on 2011-01-03
You can add free space to partition only if  it is immediately before or after the partition on the disk. The  partition table defines starting and ending points for a partition on a  disk.

---

### Post by chuchi on 2011-01-03
Ok! I solved! I moved the space to swap partition, and then from it to the Linux partition!! You were right karthick87. Thanks you very much to all!!

---

### Post by karthick87 on 2011-01-03
You are welcome :)

---

