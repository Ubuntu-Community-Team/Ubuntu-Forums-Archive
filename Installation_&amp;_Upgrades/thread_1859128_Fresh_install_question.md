---
title: "Fresh install question"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by GammaPoint on 2011-10-13
If I do a fresh install from a CD rather than an update through the package manager, and I didn't (I think) create a separate /boot partition when I first set up my partitions, will I have to save all my data and recopy it back over? Or will a "fresh install" also recognize that it shouldn't through away my data in the home directory?

---

### Post by dave2001 on 2011-10-13
I think a fresh install for a new version is always a good idea.. just look at all the "update failed" threads open right now!

To answer your question, we must determine (for sure) how your partitions are set up right now. If your not sure how to do this, open up System Monitor and go the tab which says "File Systems". Your partitions should be listed here, along with the mount point for each one. Tell us what you see.

---

### Post by zvacet on 2011-10-13
If you have separate home partition your data should be safe,but backup is always recommended.So in case you have separate home **do not format it**.Just sign it as home and you will format just root partition.If I didn´t answer in the way you want it,please tell me so.

---

### Post by GammaPoint on 2011-10-13
Yeah, I don't have a /home partition unfortunately. The only file system I see in systems monitor is:

```
/
```

---

### Post by dave2001 on 2011-10-13
> **GammaPoint said:**
> Yeah, I don't have a /home partition unfortunately. The only file system I see in systems monitor is:

```
/
```

Yep, you've just one partition for everything. Looks like you'll need to be really sure you have a functional backup of all your personal files before doing a fresh install, because it will all be erased during an installation. 

When you're running the installation, it's not too hard to set-up a separate partition for your OS. When the installer asks "where to install ubuntu" or something along those lines, choose the "manual" or "other" option. That should allow you to set up the partitions yourself. First, Make one for the OS (I make my ubuntu partion at least 10GB, more if you plan on installing alot of extra software). Mount point for the first partition would be /. Second, create another partition for your personal data. Mount point for the second partition would be /home. Third, a final partition for the swap file. 1-2 GB is usually fine for this, but some people recommend it be twice the size of your RAM. For the third partion, make sure you check "use as swap". Forgive me if i'm over explaining things, I like to be thorough for other readers who have similar questions. On the other hand, if you've got questions, just lemme know!

---

### Post by GammaPoint on 2011-10-13
Thanks for the detailed explanation. I will do that next time I do a fresh install.

Best,
GP

---

### Post by zvacet on 2011-10-14
If you want to do fresh install and have your files saved make separate home partition first (not during installation).You can look [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) for instructions.

---

