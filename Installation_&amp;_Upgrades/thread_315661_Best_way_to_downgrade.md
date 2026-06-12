---
title: "Best way to downgrade?"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by wgscott on 2006-12-09
Since "upgrading" to Edgy, I have had an intractable problem in which one or more drives or partitions spontaneously become read-only, rendering my computer pretty much useless.  I've spent a lot of time trying to track down the source of this problem, and I am giving up.

My last attempt was to upgrade to feisty, but that delivered me squarely into apt-get hell.  So I think it is time to throw this in the fire and start over.

I have a master drive that has a root and /home partition.  I would like to reformat the root partition and reinstall 6.06, but I want to keep the /home partition.

Will the install disk permit me to do this?  If I save /etc/password will it preserve my original user setup, or should I start from scratch.  Any other advice would be greatly appreciated.

](*,)

---

### Post by meng on 2006-12-09
Yes the install disk will allow you to preserve your separate /home partition. You choose to manually partition, then ensure that the separate partition is mounted to /home AND that you keep existing data rather than reformat the partition.

---

### Post by wgscott on 2006-12-09
Thanks.  I just hate going backward.  I've tried ubuntu/kubuntu/xubuntu.  Maybe this time mubuntu is the way to go. :D

---

