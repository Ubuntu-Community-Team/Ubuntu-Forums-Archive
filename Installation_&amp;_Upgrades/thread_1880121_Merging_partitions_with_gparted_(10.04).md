---
title: "Merging partitions with gparted (10.04)"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by flaptop on 2011-11-13
i would like to dedicate my hard drive to ubuntu. I would like to merge sda6 and sda1 together. how would i go about doing this? i have attached a screenshot of gparted.

[IMG]http://i.imgur.com/bfVfZ.png[/IMG]

---

### Post by raja.genupula on 2011-11-13
Hi go with this

[http://askubuntu.com/questions/66000/how-to-merge-two-partitions](http://askubuntu.com/questions/66000/how-to-merge-two-partitions)

---

### Post by dandnsmith on 2011-11-13
The advice so far will help once you've managed to get 2 adjacent partitions of the same type.
First I suggest you shrink sda6 to the right to create space enough to copy it's data elsewhere. Then shrink the extended partition sda2 to the right (you'll have to stop those swap partitions being used to unlock sda2). Next create a new partition in the gap, and copy the sda6 data into it.

Once you're happy that the data has arrived safely, you can delete sda6 and get on with the rest. 
You can probably use the advice in that link to perform the join (make sure there's no gap first).
Do think about each step - it's your 'data' which is at stake here - and query anything abou which you have doubts.

---

