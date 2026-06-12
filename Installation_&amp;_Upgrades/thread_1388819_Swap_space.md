---
title: "Swap space"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by AmrH on 2010-01-23
I've asked here about swap space for a 64bit system with 6GB of Ram, and people have answered me that I wouldn't need that much of a swap space; however, when I was following duanedesign's "Partitioning 101" on the IRC, I noticed that he mentioned that the swap space should be 1.5 times the RAM. He also mentioned that it should be at least the size of the RAM. Does this apply to the 64bit version too?

---

### Post by lloyd_b on 2010-01-23
> **AmrH said:**
> I've asked here about swap space for a 64bit system with 6GB of Ram, and people have answered me that I wouldn't need that much of a swap space; however, when I was following duanedesign's "Partitioning 101" on the IRC, I noticed that he mentioned that the swap space should be 1.5 times the RAM. He also mentioned that it should be at least the size of the RAM. Does this apply to the 64bit version too?

A lot depends on exactly what you're using the machine for.  32/64 bit isn't really significant in this case - it's a matter of how much physical RAM you have, and how much virtual memory you'll need.

For a basic desktop system, not running any "memory hog" applications, you could easily run that machine with 6GB and *no* swap space and never encounter a problem (I'm currently on a machine with 1GB, and rarely use swap space at all).

If you're running applications that really need lots of memory (like video editing or such), then you probably *need* swap space, and I'd recommend allowing at least the same amount as you have RAM.  Note that if you need more swap than that, then you probably don't have enough physical RAM...

Unless you're short of disk space (something that's pretty rare on modern systems), I'd go ahead and create a 6GB swap, just so it's there if you *do* need it.  But don't be surprised if it's rarely/never used.

Lloyd B.

---

### Post by AmrH on 2010-01-24
Seems I'll go on with a 9GB swap space. Thanks for your help!

---

### Post by cascade9 on 2010-01-24
9GB is overkill.

The only reason to have much more swap space than your RAM is if you think you are going to need it. With 6GB I doubt you will need another 9GB swap space. No matter what your doing. A friend of mine does a lot of 3d rendering, and even he doesnt use more than 8GB RAM + Swap. 

You would do better to make your swap size just a little bigger than your RAM (cause you need a tiny bit more swap space than your RAM size to use suspend).

---

### Post by Sef on 2010-01-24
>          9GB is overkill.+1.   If you want to use hibernation, you should make a 6 gb swap.   Otherwise, I would probably make it about 1 - 2 gb.   If you are going to need more swap than that (other than what was mentioned previously), you should consider adding more ram.

The 1.5 times ram was when it was much less, e.g., under 1 gb.

---

### Post by cascade9 on 2010-01-24
> **Sef said:**
> +1.   If you want to use hibernation, you should make a 6 gb swap.

Opps, is it hibernation? Shows how much I use it. Also...I think you need to have a bit more swap than your RAM size for this to work (IRC its only 20-30MB though), but 6.5GB should be fine.

---

### Post by AmrH on 2010-01-24
I'm not gonna do any 3d rendering. I just wanna hibernate from time to time, so 6GB would be enough?

---

### Post by lloyd_b on 2010-01-24
> **AmrH said:**
> I'm not gonna do any 3d rendering. I just wanna hibernate from time to time, so 6GB would be enough?

I believe you need to go a bit over 6GB, so that it has enough space to save ALL of RAM to disk, and a bit to spare.  Not really sure how far over, though (6.5GB?)

Lloyd B.

---

### Post by cascade9 on 2010-01-25
I think 6.5GB should be enough. 

The probably is that you need RAM + X for swap, where 'X' is unknown till your have tried it....

---

