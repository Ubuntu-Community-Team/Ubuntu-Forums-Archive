---
title: "Can I go without swap?"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by JohnFante on 2011-02-07
I am considering buying a fast SSD to use for my system files on a triple boot (Win7, OSX and my primary OS Ubuntu10.10) setup. All data (including /home) wil be placed on four HD's in RAID0 configurations. The reason for this configuration is that tripleboot does not like RAID0. Win7 and Ubuntu works fine but OSX gives me problems.

My question is, can I go with out a swap partition?

My PC has 6GB ram and it does not go into hibernation so I am bit unsure if I need to make a swap partiton. I know that I can make one on the RAID0 dics, so it is not a space question, but I was just wondering.

Thank you in advance.

---

### Post by vanadium on 2011-02-07
With six gigabytes, there is, with "typical" desktop use, almost never use of swap. Howeverm if disk space is not an issue, you should provide some swap just for these exceptional cases where it might be needed. By adjusting system swappiness to a minimum, you will tell the system to wait before using swap unless absolutely necessary.

---

### Post by snowpine on 2011-02-07
Swap is not mandatory. :) Typing this from 1gb ram and no swap.

---

### Post by vanadium on 2011-02-07
Swap just provides spare ram memory. Someone without a swap will quicker get into an out of memory situation that someone with the same ram, but with swap. I agree that, even with only 1 GM ram, you must already load quite a number of applications and documents before swap space is being used. And even then, you must load even more applications before effectively running out of memory. that is the practice, and in practice, you can get away without a swap. But it is not the optimal approach.

If disk space is not an issue (and usually it is not anymore an issue), there there is no drawback in having a swap. If you set swappiness to a very low value, your system will still behave as if you did not have swap. However, if the swap space would ever be needed, it will be there. The user with swap will see a very slow system that he still can shut down cleanly without data loss. The user without swap will see processes that are shut down by the system, causing data loss and leaving behind an unstable system.

---

### Post by JohnnyC35 on 2011-02-07
no issue here either. 1.5Gb of RAM, no swap. worked fine when I had the SSD installed. still good now that I am running off a regular drive drive

---

### Post by Old_Grey_Wolf on 2011-02-07
With 6GB RAM, I doubt you need swap. You can try without a swap partition. If you have problems you can add a swap partition or swap file later. Example of a tutorial to add a swap file: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by markthekdeguy on 2011-02-07
You dont need swap. i dont use it.
- especially disable swap when using a solid state hard disk.
try Googling  trim SSD swap and linux and maybe even win7. 
(Win 7 is the only windows os only to support trim)
if you need to know what trim is and how it is important to SSD .. 
and you feel like  a good read ..

[http://www.bit-tech.net/hardware/storage/2010/02/04/windows-7-ssd-performance-and-trim/1](http://www.bit-tech.net/hardware/storage/2010/02/04/windows-7-ssd-performance-and-trim/1)

have fun .. !
Mark 



-- post pointless computer specs here as a sig --

---

