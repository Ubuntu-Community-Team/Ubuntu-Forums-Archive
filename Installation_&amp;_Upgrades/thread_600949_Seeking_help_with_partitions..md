---
title: "Seeking help with partitions."
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by JimmyK377 on 2007-11-02
Right, after much researching, I've come to the conclusion about what I should do.
I have an Acer Aspire 5920g, which came with vista pre-installed, taking up 4 partitions. The 4th partition is small and contains a bizarre miniature version of win xp to run Acer InstantOn Arcade (although that doesn't work for me, the 'e' button does nothing more than make vista's screen dim aside from the arcade panel, apparantly it can bypass booting vista, but I have no idea how, anyone?).
Is it feasible to backup the files on this partition, delete the partition, and then replace it with an extended one? Before adding the files back into a logical partition, with 2 further logical ones for Ubuntu?

---

### Post by JimmyK377 on 2007-11-03
anybody?

---

### Post by cuby on 2007-11-03
You last sentence is a bit confuse. 
You cannot backup files in the partition you are going to delete. Backup the files in another drive or in DVD.
Try to play with
```

 GParted  
```

under Ubuntu to delete that partition, resize and create new partitions.

---

### Post by JimmyK377 on 2007-11-03
ah, apologies. To clarify, I meant backup the files from that partition elsewhere, before creating a logical partition to replace it, then putting the files back on

---

### Post by Pumalite on 2007-11-03
You may want to try these:

[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

