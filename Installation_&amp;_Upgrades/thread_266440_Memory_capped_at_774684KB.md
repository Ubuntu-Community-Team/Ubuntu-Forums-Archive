---
title: "Memory capped at 774684KB"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by haydenstainsby on 2006-09-27
I'm  running Dapper Drake server, and am having a problem with the amount of memory the kernel is seeing.

I have the same set up on 6 seperate machines (Acer F5 - 3GHz P4, 4 with 1GB RAM and 2 with 2GB RAM). On all the machines 'free' gives me something like this (Obviously it's not code, but it's the only way I could get the columns to show properly):


```
		total		used		free		shared	buffers	cached
Mem:	774684	731404	43280	0		132		587116
-/+ buffers/cache:	144156	630528
Swap:	1951856	0		1951856
```


I have not had any success recompiling the kernel, although I did install a new one using apt-get - uname -r gives me this:

[FONT="Courier New"]Linux <name> 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux[/FONT]

I checked the current kernel's configuration (Loaded the file /boot/config-2.6.15-27-686 into 'make menuconfig') and High Memory Support is set to 4GB, which I'm assuming means that that's how the current kernel is configured.

Any help would be greatly appriciated.

Thanks in advance.

--
Hayden

---

### Post by k_rock923 on 2006-09-27
Hi.  To see if Highmem actually is being loaded with the kernel, do a dmesg | grep -i HIGHMEM

If it's not, the kernel ( at least new kernels) will say something to the effect of 'use hihgmem) if there's more memory than it can handle.

---

### Post by haydenstainsby on 2006-09-27
Thanks.

dmesg | grep -i HIGHMEM gives me this.

[FONT="Courier New"][17179569.184000] 0MB HIGHMEM available.
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179572.588000] Memory: 767460k/786240k available (2115k kernel code, 18288k reserved, 595k data, 332k init, 0k highmem)[/FONT]

Which is looking fairly grim, any ideas why?

Thanks again.

---

### Post by k_rock923 on 2006-09-27
Hmm, now that I think about it, you're not hitting the highmem limit here.  In dmesg, you should see a line right under the HIGHMEM one about how much LOWMEM is available.  See if that corresponds to how much you have installed (really, see if it's 896MB as that is the high mem limit)  I'll assume that hihgmem was compiled into the kernel and not as a module.

---

### Post by haydenstainsby on 2006-09-27
Here's the whole section.

[FONT="Courier New"][42949372.960000] 0MB HIGHMEM available.
[42949372.960000] 767MB LOWMEM available.
[42949372.960000] NX (Execute Disable) protection: active
[42949372.960000] On node 0 totalpages: 196560
[42949372.960000]   DMA zone: 4096 pages, LIFO batch:0
[42949372.960000]   DMA32 zone: 0 pages, LIFO batch:0
[42949372.960000]   Normal zone: 192464 pages, LIFO batch:31
[42949372.960000]   HighMem zone: 0 pages, LIFO batch:0[/FONT]

As you can see I can only see the 767MB of LowMEM, but I know that I've got at least 1GB installed, and I'm getting the same on the machines with 2GB installed.

I'm thinking perhaps it's another factor, but I can't see what. The machines are brand new and shouldn't have a problem with the memory from what I can see.

There's no limit set in Lilo as a boot parameter either (I checked that first).

Thanks again.

---

### Post by haydenstainsby on 2006-09-28
Turns out it is the physical hardware causing the problem, not the linux kernel.

Thanks for the help.

---

