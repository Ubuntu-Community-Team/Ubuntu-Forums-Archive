---
title: "[SOLVED] Live CD partitioning of Vista"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by nowhere@cox.net on 2008-01-23
Heya everyone,

I just did a quick Live CD install of Gutsy on my Thinkpad T61 and let it do the guided resize partitioning and everything boots up fine. When I fdisk -l it says for 4 out of 5 of my partitions that the partition does not end on a cylinder boundary. The only one that does not say this is the swap which also happens to be the last partition. 

What does this mean? Is it troublesome? Should I fix it? Is this the "gparted resizing doesn't play nice with Vista" I read about?

btw:
I have the ability of booting from the recovery partition (which I confirmed still works fine) and recovering the factory install of Vista if needed.

Cheers!
Eric

---

### Post by wolfen69 on 2008-01-23
if everything is working correctly, dont worry about it.

---

### Post by nowhere@cox.net on 2008-01-23
Thanks for the confidence! 

However, to advance my never ending quest for knowledge, I would love to know what that message means and how it happens. It would appear to be obvious that the auto partitioner picked spots to end each partition that were not at a cylinders end but what impact does this have? Performance, reliability? 

Anyway, for now it seems to be working fine so I won't mess to much with it unless there are differing opinions provided.

Thanks!
Eric

---

### Post by Philio on 2008-01-23
You could always start over and configure the partitions manually if you don't like it as it is. Also you can resize your Vista partition within Vista from Computer Management (in Administration Tools folder if unhidden from start menu or somewhere in Control Panel). I used the Vista tool on my laptop, then created a single partition for Ubuntu, didn't see any point adding a swap as it has 4Gb ram.

---

### Post by nowhere@cox.net on 2008-01-23
This is probably what I will do since I don't like having those messages even tho I don't really understand the implications.

For you linux gurus, I also have 4GB of RAM (registering as 3.8 I guess due to the nvidia quadro 140NVM eating some up? I thought it was discrete RAM as well tho). Is the swap needed? I plan to be running VMware Workstation with an XP and when I run it I will give it 1gig to play with...

Thanks,
Eric

---

### Post by Philio on 2008-01-23
You should be fine, I'm using less than 1Gb ram at the moment with quite a few apps running.

---

### Post by nowhere@cox.net on 2008-01-29
Thanks all for the input everyone. I decided to go ahead and add 5GB of swap space to accommodate the ability to hibernate. From what I understand, you need at least as much swap as RAM to hibernate to disk, and a little extra in case you were using some swap before hibernating.

Thanks all!

Eric

---

