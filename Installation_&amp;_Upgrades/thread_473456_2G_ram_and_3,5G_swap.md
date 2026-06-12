---
title: "2G ram and 3,5G swap"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by eentonig on 2007-06-14
I started with 512M Ram and recently upgrade to 2G

Now I just read somewhere that the generic kernel only supports up to 4G of memory. Including RAM+Swap.

But when I look at htop, I see my 2G of ram AND the 3.5G of swap.

Is there a drawback  somewhere in keeping this setup? I don't need the space, zo I rather not touch my partitions for the moment. Unless it could improve my performance by reducing the swap.

---

### Post by kerry_s on 2007-06-14
with 2gig you don't even need a swap, but no it won't do nothing.

---

### Post by omschaub on 2007-06-14
> **kerry_s said:**
> with 2gig you don't even need a swap, but no it won't do nothing.

I do not agree with this.  I often dip into my swap on my 2GB system.  With Eclipse running a memory hogging program, with Firefox's memory leaks, etc. ,etc. I do notice some usage. 

But.. I do agree that having a swap and not using it will indeed do nothing.  If you have the space, then leave it be.  

If you end up running a memory hog and then shut it down and notice that your swap is still holding something, then all you have to do is:

sudo swapoff -a
sudo swapon -a

This will force everything out of swap (if memory is available) and then you just can turn it back on.  It will be empty at that point

---

### Post by eentonig on 2007-06-14
Thanks for the clarification everybody.

One last stupid questions for completeness. What would happen if I did disable swap and I run into a memory hog that exhausts RAM?

---

### Post by kerry_s on 2007-06-14
> **eentonig said:**
> Thanks for the clarification everybody.

One last stupid questions for completeness. What would happen if I did disable swap and I run into a memory hog that exhausts RAM?

the old cache will be discarded.

---

### Post by cseljatib on 2007-11-20
is it possible to relocate swap memory to ram?

i have not idea why, but i have 2.9 GB of swap memory, but i would rather to have it as ram (see picture). Can i change that?

---

### Post by forestpixie on 2007-11-20
not completely sure what you're asking here - you can't change swap to ram

If you're saying that you want the ram used before swap - linuc generally does that afaik - you change swappiness if you like

have a look in terminal at the memory usage there - it's probably different than the sys mon

```
free -m
```

---

### Post by rsambuca on 2007-11-20
> **cseljatib said:**
> is it possible to relocate swap memory to ram?

i have not idea why, but i have 2.9 GB of swap memory, but i would rather to have it as ram (see picture). Can i change that?

The answer to your first question is no.  Your RAM is a an actual card that is inserted into your motherboard, so the size of it doesn't change unless you physically open your computer and add more.

Your system is working fine.  You do not want to have your swap used if possible.  The swap is partition on your hard drive that is used if your RAM is insufficient for the programs you are running.  The swap is much slower than RAM, it is better to use RAM wherever possible.  Just leave everything as is!

---

