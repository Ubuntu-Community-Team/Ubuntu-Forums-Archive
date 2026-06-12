---
title: "Shrink Partition and Move /home"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by VideoRoy on 2010-02-23
After running Ubuntu for a while now I think I made a rookie mistake and have used my entire 640gb drive for Ubuntu filesystem and /home (plus small swap).

Looks like best practice is to have the filesystem and /home on separate partitions to make upgrades and backups easier.

It took me a while get the system setup the way I want although I do not have much data loaded yet I would like to shrink the filesystem to maybe 200gb or less and use the rest for /home.

I think I know the steps to achieve this but my question is, is it better to shrink and move /home or just start over?  If shrink will I just cause myself more headaches later?

The steps I am going to do is shrink partition, update UUID in fstab and then follow the guide to move my /home to a new partition.

Any advice from someone that has done this before would be appreciated.

Thanks!

---

### Post by VideoRoy on 2010-02-23
I found this really good guide so I am going to go for it.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by bruno9779 on 2010-02-23
> **VideoRoy said:**
> I found this really good guide so I am going to go for it.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

That's exactly what I was going to advice. Really good & useful tutorials at psychocats

---

