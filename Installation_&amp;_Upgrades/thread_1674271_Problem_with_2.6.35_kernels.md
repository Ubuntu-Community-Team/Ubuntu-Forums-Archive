---
title: "Problem with 2.6.35 kernels"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by Superlinkx on 2011-01-23
I recently installed ubuntu on my HP pavilion elite e9240f desktop. Everything works fine in 10.10 as long as I use the older 2.6.32 kernel. Every time I update to 2.6.35 though, it runs for a few minutes, then randomly crashes, going to a black screen with a white cursor. The time varies from a few minutes to a couple hours, but I always end up with an unresponsive computer and have to hard shutdown. Then it won't load 2.6.35 and I have to boot into the older kernel, remove the newer one. I generally don't have any issues when using 2.6.32, other than when I use too many graphics intensive processes and my ubuntu stops talking to my graphics card.

Any help would be appreciated.

---

### Post by Pasta on 2011-01-23
> **Superlinkx said:**
> I recently installed ubuntu on my HP pavilion elite e9240f desktop. Everything works fine in 10.10 as long as I use the older 2.6.32 kernel. Every time I update to 2.6.35 though, it runs for a few minutes, then randomly crashes, going to a black screen with a white cursor. The time varies from a few minutes to a couple hours, but I always end up with an unresponsive computer and have to hard shutdown. Then it won't load 2.6.35 and I have to boot into the older kernel, remove the newer one. I generally don't have any issues when using 2.6.32, other than when I use too many graphics intensive processes and my ubuntu stops talking to my graphics card.

Any help would be appreciated.

Are you using proprietary drivers for your graphic card?
The 2.6.35 Kernel is a little slower but it works fine for me.
I've tried the 2.6.36 kernel and it's ok a little better.
The 2.6.37 rc1 is awesome, it's very fast and a great improvement but i couldn't install proprietary drivers in it for my ATI card.

---

### Post by Bucky Ball on 2011-01-23
> **Pasta said:**
> 
The 2.6.37 rc1 is awesome, it's very fast and a great improvement but i couldn't install proprietary drivers in it for my ATI card.

Apparently that kernel is not ready for those drivers I discovered after a bit of digging around. I have the same problem.

---

### Post by Superlinkx on 2011-01-23
I am not using proprietary drivers. The open source ones seem to work almost as good. I might try them to see if that helps, but not sure if that's what's causing the black screen issue. I'll look for the 2.6.36 kernel, I haven't seen it in synaptic yet, so I haven't tried it. I'll report back after trying drivers and the newer kernel.

---

