---
title: "not enough space on disk to upgrade (but my disk is empty)"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by abelito8 on 2010-01-12
Good evening, 
 
I have installed ubuntu on an AA1 (160 GB, 1 RAM, 11.6 screen) and I have tried to upgrade the version I have. The system says there is not enough space...but I have installed linux today and I should have more than 120 GB free...

the only thing that might have gone wrong is the partition. When installing I was not asked how much space I wanted for a swap and how much for mount point (I selected the option "biggest empty space")...

shall I just reinstall and do the partition manually or there is anything else that might have gone wrong?

thank you
Abel

---

### Post by drs305 on 2010-01-12
If you run this we can see what you have for partitions and how the space is allocated:
```
sudo df -h
```

---

### Post by abelito8 on 2010-01-25
I found your reply only now for I have no more alerts arriving into my mailbox for some reason

I eventually found out, I simply made a mistake when doing the partitioning but thank you anyway

---

### Post by drs305 on 2010-01-25
> **abelito8 said:**
> I found your reply only now for I have no more alerts arriving into my mailbox for some reason

I eventually found out, I simply made a mistake when doing the partitioning but thank you anyway

If you installed Jaunty side-by-side with Windows there is a bug in the installation script. You must resize the Linux partition since the default (2.3-2.5 GB) is too small. You may have already figured this out. It was poorly designed and if you fell 'victim' to the bug you weren't alone.  

If you need any help with this problem for reinstalling, here is a link to help: [http://ubuntuforums.org/showthread.php?p=7658271]("http://ubuntuforums.org/showthread.php?p=7658271")

---

### Post by abelito8 on 2010-01-25
ah was a bug, I thought it was my fault...anyway it prompted me to learn how to partition manually now :)

---

