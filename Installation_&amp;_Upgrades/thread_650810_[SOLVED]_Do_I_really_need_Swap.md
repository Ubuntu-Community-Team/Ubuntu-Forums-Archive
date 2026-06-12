---
title: "[SOLVED] Do I really need Swap?"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by H4rm0ny on 2007-12-26
It's been a while since I've installed an Ubuntu system from scratch, so I can't remember if this is allowed by the install process, but anyway... I have a new system coming (I hope) with 4GB of memory. It's a silly amount of RAM, quite frankly. So my question is do I actually need to create a Swap partition and if not, will Ubuntu throw any errors without it?

I'm thinking that when my computer isn't reading data from files, or if only from my separate media hard disk, there's no reason for it to be spinning the drive up.

Can I do this? Is it advisable?

Thanks,

-Harmony.

---

### Post by taurus on 2007-12-26
It depends on what you plan to run with that machine.  Chances are you don't need to touch any swap at all so I assume you can skip the swap partition.  However, if it makes the system happy, give it about 512MB of swap.  

I assume you plan to install the x86_64 version if you want to use all 4GB of RAM.

---

### Post by Craigus on 2007-12-26
Some interesting discussion here :

[http://kerneltrap.org/node/3660]("http://kerneltrap.org/node/3660")

---

### Post by H4rm0ny on 2007-12-26
Yes - this will be my first venture into 64-bit territory. I've just had a look at the swap usage on my current machine which has 2GB of RAM (still a lot) using
```

free -mt

```

And even though I have a lot of RAM space free, it still tells me that I have about 34K in swap. Why, I don't know, but I'm thinking that if I don't have a swap partition then it will use memory all the time.

The linked article details setting up a RAM disk for swap. I can do this, but I'm unclear on whether I would have to. I presume that Swap isn't intended to be used until the RAM is full. I had understood that Linux made a lot of use of RAM as a disk cache.

So when my new kit arrives, I'm going to partition everything without swap at all, if the installer will let me. Nobody thinks this will lead to system Hell, then?

---

### Post by PmDematagoda on 2007-12-26
If you have 4Gb of RAM on the new PC then I really do not think you will have to have a Swap partition for it at all. But if you want to use all the RAM on the new PC then you will have to either use Ubuntu X64 or compile a kernel on Ubuntu 32bit which supports a maximum of 4Gb of RAM because Ubuntu 32bit  only supports a maximum of 3.2Gb of RAM out of the box.

---

### Post by H4rm0ny on 2007-12-26
Okay. That's reassuring. I was pretty confident that I wouldn't need Swap, but I wasn't certain if aspects of Linux were so conditioned to expect it that not having it configured would send everything into a panic.

I should have also added that I'll be doing some accounting work on this system and although I can configure processes not to store information in Swap, keeping everything in nicely volatile RAM altogether makes me worry less about having missed something.

I'm definitely going with the 64-bit version of Ubuntu, so no worries about addressing it all. My new motherboard supports 8GB and I only wish I could think of some way to justify maxing it out. It just appeals for some reason. :)

---

### Post by Steveway on 2007-12-26
Doesn't suspend-to-disk use swap?
I was under the impression it does.
So if you want to suspend-to-disk then you need swap in the size of at least your memory.

---

### Post by H4rm0ny on 2007-12-26
Oh bother. That's why I post to these forums before trying out any of my bright ideas. If it does need swap - and I can only assume that it would - then I'll have to think about whether or not I care about Suspend to Disk. I don't use it at the moment and my new system should boot up even more quickly.

But I should probably be using this feature, it being the modern way of doing things.

Hmmmmm. Thanks for pointing that out.

---

### Post by tgalati4 on 2007-12-26
Here's the dilemma:

4 GB is a large chunk to compress and write to disk during hibernate (aka suspend-to-disk).  It also takes a while to read from disk and uncompress.  In my timing, it takes the same amount of time to do a cold boot as it does to resume from a hibernation file.

Suspend-to-RAM is what you want.  It works on one of my machines going from 95 watts to 4 watts in ~5 seconds and waking up in ~6 seconds.  If you loose wall power then you lose your current session, unless you are on an UPS.  Unfortunately, Gutsy broke suspend-to-RAM for a lot of machines due to a newer kernel and a different memory allocation model.

I disabled hibernate because it takes too long.

You want a small amount of swap so that you can try out future Live distros.  They run faster when swap is available.

---

### Post by H4rm0ny on 2007-12-27
Suspend to RAM sounds interesting. I've never used it before, but I like the idea of it. I normally assign more Swap than I have memory, so perhaps there wouldn't be a need to compress it when hibernating and I'd get better performance. But I don't think I'll bother.

I'm not concerned about trying out future live distros. I can always try them on my old computer and I don't have much freetime to be swapping around between distros for the time being, anyway. If need be, I'll create a RAM disk and assign that as swap once I've started it up.

Thanks for all of the comments. This has turned out to be a really useful thread for me.

-Harmony.

---

### Post by H4rm0ny on 2007-12-31
Just in case this thread turns up for anyone else from Google or a forum search, I have now set my system up without a swap partition of any kind. The install process asked me if I were certain I wanted to do this, I said yes, and my system is now making very good use of its RAM, allowing the disks to have a nice rest and speeding my access times.

---

### Post by Gigamo on 2007-12-31
> **H4rm0ny said:**
> Just in case this thread turns up for anyone else from Google or a forum search, I have now set my system up without a swap partition of any kind. The install process asked me if I were certain I wanted to do this, I said yes, and my system is now making very good use of its RAM, allowing the disks to have a nice rest and speeding my access times.

Nice, good to know.

---

