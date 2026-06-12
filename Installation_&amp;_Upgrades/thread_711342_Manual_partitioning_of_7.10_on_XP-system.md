---
title: "Manual partitioning of 7.10 on XP-system"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by Bion_b on 2008-02-29
I'm trying to install Ubuntu on a second harddrive using the alternate-CD. The only option that shows that drive is the manual partitioning. But what flags shall I set to make it right? I have something like 13GB storage on that drive.

---

### Post by housam on 2008-02-29
- You need two partitions : one EXT3 ( 12 GB is a good space ) for installing ubuntu as a root partition ( / ). and the other one as a swap ( only 1 GB ).
- During the installation process when it comes to the partitioning , assign the EXT3 as a root ( / ) .

---

### Post by Pumalite on 2008-02-29
You dont need to create any flags. Just create at least 10 GB for '/', 1 GB for /swap in the space you have (13 GB?)

---

### Post by Bion_b on 2008-03-01
Thanks,
working fine now.

/Bjoern Bergvall

---

### Post by Pumalite on 2008-03-01
You are welcome. Good luck.

---

