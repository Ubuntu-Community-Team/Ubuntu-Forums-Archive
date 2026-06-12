---
title: "What do you advise Ubuntu 32 bits or Ubuntu 64-bit?"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by ismaelito on 2010-02-28
I am using ubuntu 32bit on a laptop and it's going  luxury.

However, we have a desktop 64-bit Intel core 2 Quard  and 4 GB of Memory Ram and a 500GB HHD, and now  the question, what  is the version that would fit better with this computer, the 32 bits  or 64 bits?

Another  thing, on a computer with 500 GB HDD and 4 GB of Memory RAM:
How mach do we give to the root (/) and the swap? Of  course we want to put the largest size to (/ home)
Thanks in advance.

---

### Post by underworld288 on 2010-02-28
I'm running on a laptop right now that has the 64-bit version of Ubuntu on it and I'm having no problems. As for the / (root) and swap partitions of your hard drive, I would recommend 128MB for the swap partition. The / (root) partition depends on the directories that are not going to have their own partition (e.g. the var, usr, home, boot, tmp, and opt directories).





















(

---

### Post by spcwingo on 2010-02-28
You can also install 32-bit and then install a PAE enabled kernel (server kernel) to address the rest of your RAM.  The only reason for doing this is 64-bit support is indeed getting better, but 32-bit is still the defacto standard, hence better support, more software choices, less buggy, etc.  As always, YMMV.  Just my $0.02.  ;)

---

### Post by dE_logics on 2010-02-28
Post the output of ```
free -m
```

If you see the total memory less than 3.5 GB (or equivalent in MB), you NEED a 64 bit distribution.

Since you have 4 GB installed, it's really a good idea to switch to 64 bit. You're on the verge you know.

---

### Post by MattBD on 2010-02-28
I've found 64-bit to be significantly faster on my sadly now-departed Philips laptop, and there wasn't any software I needed that wasn't supported in 64-bit, so I'd urge going 64-bit.

---

### Post by oldfred on 2010-02-28
I had 32 bit up until Karmic and I converted to 64 bit and have not had any problems at all. I also installed 64 bit on my portable but I use it as a desktop so I may not have tested all the features, but have not had any issues.

If you ever want to hibernate you should make swap the same size as RAM or 4GB otherwise 2GB would be fine as you have 500GB. Root can be 10-20GB and since you have 500 I would go with 20GB. I have all my data in a separate data partition and even my /home partition has only used about 1GB for the hidden stuff. If you are ever thinking about other systems or when upgradeing keeping another version I would make another 20GB for that. I am alternating root partitions so I keep the last version available incase I want old settings or have boot problems.

---

### Post by 2hot6ft2 on 2010-02-28
> **ismaelito said:**
> 
Another  thing, on a computer with 500 GB HDD and 4 GB of Memory RAM:

To make full use of the 4GB of RAM you will have to go with 64 bit.
To be able to suspend your swap should be at least the size of your RAM so 4GB.

---

### Post by sgosnell on 2010-02-28
If you have the hardware, 64-bit is the way to go.  You have half a terabyte of storage, so don't be stingy with it.  You want 4GB swap, and at least 20GB for /, maybe more.  Right now, you can get by with a lot less than that, but if you want to use the drive as is for the long term, you may want to put more, because software never gets smaller, only larger, and you may need more room for future versions.  If a few GB in / is going to make you run short on /home, you need to get a bigger drive in the first place.

---

