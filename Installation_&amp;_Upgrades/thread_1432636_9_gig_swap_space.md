---
title: "9 gig swap space?"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by linux_believer on 2010-03-18
Recently did a fresh install on a terrabyte hard drive and did the automatic partitioning and setup. Just noticed it gave me a 9gig swap. Seems like it determines the swap space by a percentage of the total drive.  Should I file a bug report?

---

### Post by zvacet on 2010-03-18
For terabyte HDD (and smaller sizes too ) I think it is better idea t ohave separate home partition.If you want you can make one following [this]("http://www.psychocats.net/ubuntu/separatehome") guide.If you don't want to do thatstill in that guide you will see how to use Gparted and shrink your swap to 2-2,5GB.You can extend existing partition to that free space.

---

### Post by cascade9 on 2010-03-18
> **linux_believer said:**
> Recently did a fresh install on a terrabyte hard drive and did the automatic partitioning and setup. Just noticed it gave me a 9gig swap. Seems like it determines the swap space by a percentage of the total drive.  Should I file a bug report?

Yes, as far as I know that is how automatic partitioning does things- by % of the drive. No, dont put in a bug report, thats how its meant to work. 

Better to do manual partitoning IMO. Its not that hard to do. :)

---

### Post by srs5694 on 2010-03-18
It may sound excessive, but 9GB of swap space might not be if you've got a lot of RAM. When you suspend to disk, Linux stores the contents of RAM in swap space, so you need as much swap space as you've got RAM, and more doesn't hurt. Thus, on a system with 8GB of RAM, 9GB of swap would certainly not be excessive. Also, as a general rule it's better to have too much swap than too little. The swap space is there to keep your system running in case of a big demand for memory (lots of programs running or demanding more memory for some reason). If you run out of memory (RAM + swap), programs may misbehave or crash. On a 1TB hard drive, chances are you won't miss, say, 5GB of space that's tied up in swap rather than being used in a filesystem.

---

### Post by rahulshah on 2010-03-18
Its better to do the manual partitioning. Its not that tough and might turn out to be more stable. Always give the size of the swap to be double the size of your RAM. Do not keep too big a swap memory.
To much can be too bad :)

---

### Post by linux_believer on 2010-03-18
Thanks for all your input!

I have 4gigs of Ram. When I'm running a virtual machine I'm only utilizing 46% of my ram. Even when suspending to disk the amount looks to be excessive but I guess that's something I need to think about if I want to use my machine that way.

---

