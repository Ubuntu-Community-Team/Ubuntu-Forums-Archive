---
title: "[SOLVED] Install won't recognize my SATA partitions"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by Victormd on 2008-03-10
I'm trying to install ubuntu on a new machine with a SATA HD. The live CD runs, no problem, and mounts my Windows partition. However, when I try to run the install, the partitioner doesn't recognize my partitions and wants to install on the entire drive! If I set it to Manual, the partitioner only shows one large partition! Any thoughts?

---

### Post by taurus on 2008-03-10
Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by logos34 on 2008-03-10
> **Victormd said:**
>  If I set it to Manual, the partitioner only shows one large partition! Any thoughts?

Right, your windows parittion, which takes up the entire disk,  You have to drag the slider bar to shrink it down to make room for ubuntu / and /swap

---

### Post by Victormd on 2008-03-10
> **logos34 said:**
> Right, your windows parittion, which takes up the entire disk,  You have to drag the slider bar to shrink it down to make room for ubuntu / and /swap

My HD was already partitioned. That's what was bothering me, because the partitioner would not recognize my partitions.

Problem solved. Even though I could see and use my partitions under windows (and even under the live CD), there was something wrong with the partition table (I'm not sure). I installed Partition Magic and it fixed my HD. The first time I partitioned, I used Windows XP partition manager (bad idea - of course). After PQ Magic, everything worked like a charm!

Thanks

---

