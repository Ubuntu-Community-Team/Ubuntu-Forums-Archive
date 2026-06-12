---
title: "2GB RAM, how much swap needed?"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by lukoil on 2011-03-10
hi,

I have a netbook with Ubuntu 10.10 and currently i have 1 GB RAM installed and 2GB of swap space. The HDD is 250GB. If i want to upgrade to 2GB RAM, how much swap do I need? I read that its recommended 2x as the RAM. If i have to change it, how do I do that?

Thanks!

---

### Post by ~Plue on 2011-03-10
actually, a swap partition equal to the amount of RAM you've got is plentiful
the 2x rule of thumb applies  if the system is low on RAM

you can read more about it here >> [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by lukoil on 2011-03-10
So I should just upgrade to 2GB and leave the swap the way it is now (2GB)? I want 2GB mainly for windows 7 which is pretty slow and laggy. 

Cheers

---

### Post by ~Plue on 2011-03-10
yep
but if you ever feel the need to increase the size of the swap space;

boot in to a live cd, 
open gparted, 
shrink the partition next to the swap 
disable the swap
add the unallocated space to the swap partition by expanding it. 

(the options would be available from the right click context menu of each partition)

---

### Post by doas777 on 2011-03-10
just remember, to hibernate (if you want to) you need to have at least as much swap as ram, plus the amount of swap that was being used at the time of the hibernation. usually 1.5x is an alright guideline (but likely overkill). use your own judgement based on the amount of swap you notice being used when your system is under a good sized load. if you don;t need to hibernate, you might not need swap at all.

---

### Post by JohnnyC35 on 2011-03-10
My system only has 2Gb of memory, using 512 for onboard video, so 1.5Gb. Computer is only using 800Mb of RAM. I installed swapd to automatically make swapfiles if needed, so far it hasn't.

---

### Post by garvinrick4 on 2011-03-10
+1 on post 5

---

### Post by uRock on 2011-03-10
> **lukoil said:**
> So I should just upgrade to 2GB and leave the swap the way it is now (2GB)? I want 2GB mainly for windows 7 which is pretty slow and laggy. 

Cheers
That is what I have on my machine. The only time swap gets used is when I run a virtual machine or Wireshark while running a torrent. I never use hibernate, but I did it once accidentally and it worked fine.

---

### Post by SaintDanBert on 2011-03-10
Swap-space has at least two uses.  First, obviously, is to hold contents of RAM when copied from idle parts of running processes.  Second, and not obvious at all, swap-partition ( [highlight]partition[/highlight] not swap file) space gets used during suspend-to-ram and suspend-to-disk. Your swap partition must be large enough to hold 100% of system ram and some additional space for administrative details.

I've fought this issue for some time and do not find a formal formula:
```

swap-partition-size = ram-size + Q

```
where 'Q' is some amount for overhead either as a constant or as a function of ram size.

~~~ 0;-Dan

---

