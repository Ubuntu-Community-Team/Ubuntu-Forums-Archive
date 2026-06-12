---
title: "How can i resize my ubuntu partition!"
date: 2011-06-20
forum: Installation &amp; Upgrades
---

### Post by lebron15 on 2011-06-20
Hi to everyone,i am very glaad to be here,ubuntu is great but i have a problem and i would like your help.

I recently tried the ubuntu and i like it very much so i want it as my primary OS but i made the partition for ubuntu only 20gb because i didnt know if i would like that.Now i want to resize partition to 70-80 gb and i dont know how to do that,i searched but i didn't find a step by step guide,so i ask for your help,the only thing i know is that i must use a program called gparted,i would like you to tell me which is the easiest way to resize the partition,thank you very much!

---

### Post by sanderd17 on 2011-06-20
You can't edit a partition that is "in use" so you need to do this from a live CD.

From a live CD, open gparted (it's installed in the live CD), right click on the partition that you want to shrink, select resize, drag the grip to shrink it, press OK, right click on the partition that you want to enlarge, drag the grip, press OK and apply with the green V.

If some options are greyed out, you may need to unmount the swap or any other partition (from the same right-click menu).

Partitions have a fixed spot, so you can't take space of the beginning and add it to the ending. When you have messed something up (e.g. deleted a partition or shrunk a wrong partition), just close gparted and begin again. As long as you don't press the V, nothing happens.

Resizing can take a lot of time. Don't interrupt it or you will end with broken partitions.

---

