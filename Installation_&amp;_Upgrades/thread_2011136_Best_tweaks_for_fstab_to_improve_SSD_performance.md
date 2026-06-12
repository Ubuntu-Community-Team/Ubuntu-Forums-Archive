---
title: "Best tweaks for fstab to improve SSD performance"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by 23senick on 2012-06-26
I’ve been running xubuntu with some years on Aspire Aspire One with 8GB SSD - now on 12.04. I’ve tweaked fstab to reduce writes to SSD, because SSD writing is slower than HDD and creates frustrating pauses. 

I didn’t pick up on the need to format to EXT4 without journaling so my first fstab tweak is data=ordered in this line:

<disc name>/               ext4    noatime,discard,data=ordered,errors=remount-ro 0       1

And I’ll leave it this way unless/until I have a good reason to go for a fresh install, at which point I'd re-format the drive.  I also ensured Firefox caches to the tmp file.

**However I recently noticed there are two differing sets of advice for additional lines in fstab. ** I’ve been using  

[I]tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
none /var/tmp aufs noatime,br:/tmp=rw:/var/tmp=ro 0 0
none /var/log aufs noatime,br:/tmp=rw:/var/log=ro 0 0
none /var/cache aufs noatime,br:/tmp=rw:/var/cache=ro 0 0[/I]

I still seem to get some pauses while there is writing to the hard disk.  The following are the alternative lines I’ve recently noticed in some posts.
[I]
&#65279;tmpfs   /tmp       tmpfs   defaults,noatime,mode=1777   0  0
tmpfs   /var/spool tmpfs   defaults,noatime,mode=1777   0  0
tmpfs   /var/tmp   tmpfs   defaults,noatime,mode=1777   0  0 
tmpfs   /var/log   tmpfs   defaults,noatime,mode=0755   0  0[/I]


How do these two options differ? Both appear to claim to have the same effect (stopping writing logs to SSD). Which is best?

Thoughts anyone?

---

