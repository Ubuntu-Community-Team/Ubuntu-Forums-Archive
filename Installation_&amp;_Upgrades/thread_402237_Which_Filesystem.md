---
title: "Which Filesystem?"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by matty_b_1000 on 2007-04-05
At the risk of sounding like a noob, which filesystem do I use for the root and swap partitions, and how big do the partitions need to be?

---

### Post by tkjacobsen on 2007-04-05
ext3 is usually a good idea. If you have a seperate /home/ partition the root don't have to be larger than 5gb. I usually use 10. Swap has to be about twice the size of your ram -- and don't uses a filesystem - just has to be of type linux swap.

---

### Post by matty_b_1000 on 2007-04-05
Thank you very much. I didn't want to choose the wrong one and mess up my PC.
P.S. Another question, does it need to be a Primary, Logical or Extended partition?

---

### Post by tkjacobsen on 2007-04-05
it can be any.. Only winblows has to be in a primary partition. But if you only got few partitions i would use primary. 

The reason extented partitions exists is that only 4 primary are allowed -- This is a legacy from when harddisks was very small and no one could imagine more than 4 partitions. The 4th can be made to an extended partition which can contain many partitions.

---

### Post by matty_b_1000 on 2007-04-05
Thanks again.

---

