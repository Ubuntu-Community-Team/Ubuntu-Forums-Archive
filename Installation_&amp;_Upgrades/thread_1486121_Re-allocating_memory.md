---
title: "Re-allocating memory"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by ardvark on 2010-05-17
I've recently fresh installed Ubuntu 10.4, coming up from the last LTS version. I have a question about RAM memory allocation. Yesterday the system became really bogged down (with a lot of disk access). Looking at the System Monitor shows that of my 2G ram, 500M was allocated to memory and 1.5G allocated to swap. Memory usage was up to 80+ % sometimes hitting 100%. Today there's only 50% being used. I'm not sure at this point what was hogging almost 400M.. Also swap never got above 30%.

What I'd like to know is if there is a procedure to re-allocate this memory
to at least give a bit more ram memory?

---

### Post by JustinR on 2010-05-17
If you have enough ram, at least 2GB you can turn Swap off if you don't use Ubuntu for heavy usage.

But if you have less RAM you can tell Ubuntu to use as much RAM and not Swap as possible - making the constant hard drive reading/writing go down.

The Ubuntu Kernel uses whats called Swappiness to determine what and what should not be put into SWAP. Swappiness is based on a scale from 0-100, the default being 60. You can lower that value to something, like 10 to keep memory swapping to a minimum
```

sudo sysctl vm.swappiness=10

```

To make this permanent adjust, run "gksudo gedit /etc/sysctl.conf"

This FAQ with help: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by ardvark on 2010-05-17
Thanks for your quick reply.

I may be a bit lost here. If I do this:
cat /proc/sys/vm/swappiness 
I do get 60 as a reply..
But when I try to edit sysctl.conf the line  vm.swappiness does not exist.
Was it moved somewhere else? All of the entries in the sysctl.conf seem to be dealing with network stuff.

---

### Post by ardvark on 2010-05-18
Also, swappiness seems to only effect how much is sent to swap, not its physical size. I want to decrease the physical size of RAM swap and use it for main RAM memory.

---

### Post by oldos2er on 2010-05-18
How much actual RAM do you have?

---

### Post by ardvark on 2010-05-18
I have 2G Ram, system monitor is showing 497M assigned to memory and 1.5+G assigned to swap. Personally I think it should the other way around. From just what's normally loaded, it's using up over 50%, start up a browser and your right up to 80%.

---

### Post by oldos2er on 2010-05-18
Swap is a hard disk partition, not RAM. Can you post the output of **free -m** run in a terminal?

---

### Post by robert shearer on 2010-05-18
can you open a terminal and type..

```
cat /proc/meminfo
```

and paste the output here.

Correct me if I am mistaken,  what I think you are experiencing is your actual physical ram being somehow cached as swap ?.

I assume you have an actual swap partition that is not being used ?? can you post details of its size and use if any..  
In a terminal type...

```
top
```

and paste the output of lines 4 and 5 (mem/swap) here.

For what it is worth I have had this happen twice recently, once on a live cd and once on installed system. Both on the same machine.
May be a bug.

It is not normal behaviour, Ram is usually _cached_ so will be shown as utilised but hardly ever as swap.
Strange.


Edit,  I would be interested in the result of..

```
sudo hdparm -tT /dev/sda
```

This tests the timing of caching and buffering of your hard drive.

When I run this my hard drive fails the buffer read but spends an age and 100% cpu trying.
At the same time memory use is almost maxed out.

Could explain why the swap partition seems not to be used and why it tries to swap to ram.??

---

### Post by ardvark on 2010-05-19
I'm sending what I got out of top & meminfo. As you can see, out of my on board 2G RAM about 500K is set for memory and the rest is swap. I had several things going on the desktop and there wasn't much memory left. Pretty much all being wasted in the swap area.

Swap:  1490936k total,    80232k used,  1410704k free,   125224k cached
Mem:    509168k total,   488480k used,    20688k free,    22296k buffers

MemTotal:         509168 kB
MemFree:           12276 kB
Buffers:           28304 kB
Cached:           131056 kB
SwapCached:        19864 kB

---

### Post by robert shearer on 2010-05-19
O.K  you need to run memtest from the live cd.

From your last posting it would appear that you only have 512MB of RAM recognised.

Then,
Can you run from the terminal...

```
sudo lshw
```

and paste here the output that pertains to "memory". :)

---

### Post by ardvark on 2010-05-19
Well, this is embarrassing, I only actually have 512K. I completely forgot about a few months ago I was trouble-shooting what I thought was a memory problem in another PC and I moved the 2G to that one. :oops:

I was blindingly led down a false assumption when my RAM and HD swap just happened to add up to 2G...   Thanks again to all who replied.

---

### Post by robert shearer on 2010-05-19
> **ardvark said:**
> Well, this is embarrassing, I only actually have 512K. I completely forgot about a few months ago I was trouble-shooting what I thought was a memory problem in another PC and I moved the 2G to that one. :oops:

Classic.! :)

I laughed so hard I nearly fell off the chair. :)

Thanks for the update, things should fly when you put the ram back !.

---

