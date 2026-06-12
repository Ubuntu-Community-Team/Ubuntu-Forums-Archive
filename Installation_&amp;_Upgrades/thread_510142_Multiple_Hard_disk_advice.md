---
title: "Multiple Hard disk advice"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by awalsh on 2007-07-26
Hello,

Ive just ordered a new 250gb SATA drive for my computer (all ready got a 250gb in there), I want to be able to have partitions across both the drives. I know this can be done with LVM or RAID, I was wondering if anyone had any advice on which I should go for, my motherboard supports onboard RAID 0, 5 etc (a few others that I cannot remember). However I don't think that I will benefit too greatly from a RAID setup unless I bought more disks which will not likely happen for a while.

So my main questions are, does anyone have any advice on how I can go about this?

Also does the Ubuntu Feisty (64 bit) installer support LVM so I can do it on the reinstall (sadly I think i will have to format my pc and set it up again :( )? Or do I have to do the LVM stuff from the alternate CD as many people seem to do....

Any suggestions would be greatly appreciated 

Thanks

Andrew

---

### Post by dabl on 2007-07-26
Doesn't matter what your motherboard RAID controller can do, 'cause Linux has no drivers for it. :(

However, folks are doing software RAID 0 setups successfully, according to what you can read if you search for "software raid" or "mdadm" or terms like that. I think there are posts on this forum, as well as elsewhere that Google can find.

Bear in mind that when you set up your system on a RAID 0, if either drive fails your entire system is hosed ... just a caution. :)

---

### Post by awalsh on 2007-07-26
Thanks for the advice, I see now that RAID is probably not my best choice. I'm not too bothered about redundancy as I have a fairly good backup procedure in place that runs nightly (rsync to external machine, burn to DVD weekly). Any more thoughts on LVM or RAID?

---

