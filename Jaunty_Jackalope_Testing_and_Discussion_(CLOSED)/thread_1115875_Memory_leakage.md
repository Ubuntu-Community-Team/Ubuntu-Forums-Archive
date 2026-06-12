---
title: "Memory leakage"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by BhumibolTheGreat on 2009-04-04
Hi guys, 

How do I know if system has memory leakage? 
On my daily usage system reaches up to 1.5 GB RAM usage (I've got 2 GB RAM installed on my system). 
When trying to list all running applications I could see that none of them was taking so much resources and combining them all together would give me a smaller result.

I must admit that it happened once and after several updates that were made my system now reaches about 900 MB usage. 
I'm not sure if this bug was fixed or I just couldn't reproduce this scenario.

Any comments from your side? 
What's your average system RAM usage?


Thanks,

---

### Post by phenest on 2009-04-04
One thing you need to be careful of is thinking it's a memory leak. It may be, but consider this first:

Different programs report memory usage differently. Which one are you using? Some programs include the memory cache, and some don't. The memory usage you are seeing may be perfectly normal if it includes the cache.

I would only show cause for concern when your computer starts to slow down as usage reaches memory limits.

---

### Post by damis648 on 2009-04-04
> **phenest said:**
> One thing you need to be careful of is thinking it's a memory leak. It may be, but consider this first:

Different programs report memory usage differently. Which one are you using? Some programs include the memory cache, and some don't. The memory usage you are seeing may be perfectly normal if it includes the cache.

I would only show cause for concern when your computer starts to slow down as usage reaches memory limits.

Yes, what does
```
free -m
```
show? It will show something like
```
                total       used       free     shared    buffers     cached
Mem:          3528       3435         92          0        152       2730
**-/+ buffers/cache:        552       2976**
Swap:         5239          1       5238
```
The 'free' in the first line *includes* the cache while the 'free' in the second line doesn't. Have a look at the usage in the second line, that is your actual usage of RAM.

---

### Post by phenest on 2009-04-04
Another thought:

Some users think it's terrible when their memory gets used up. But that IS what it's there for. If you have 2GB RAM, expect it to be used. If you have 8GB, expect it to be used.

The cache is there to speed things up removing the need to keep accessing the hard drive.

If you haven't noticed this before in previous releases of Ubuntu, that is no cause for concern either. It just means that Jaunty is making use of your RAM as a good OS should do.

---

