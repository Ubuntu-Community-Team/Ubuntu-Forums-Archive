---
title: "Upgrade / re-install from FC6 and keep RAID data..."
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by Steve Hammers on 2008-05-14
Ok.. so I've had it with the Fedora Core 6 installation on my server.  I've been trying for several days to update it, and I've come to the conclusion that the package dependency tree is so FUBAR'd that its impossible without a complete re-install.

So I'd like to leave Fedora behind and Install Ubuntu to my server.  I have installed Ubuntu on several other systems now, and every one has had no problems at all.  

I'm not expecting to keep my FC6 config.  Most of this I can backup and reinstall (apache, svn, trac, munin, etc..)  But what I would really like to keep is my software RAID data.  

I have 2x 4disk RAID 5 arrays with an active spare, created with mdadm, that are then joined using LVM.  Basically I want to know if its possible to do a fresh install of Ububtu, and recreate the arrays WITHOUT losing my data!  A tall order?  I hope not, as I don't have 2TB of storage to back this up to... 

Please help.. 

-Steve

---

### Post by Steve Hammers on 2008-05-17
** Bump **

No ideas?  I thought the main benefit of using software RAID was its portability?  i.e. if you MB / Controller dies you can just move the raid to another Linux system and re-activate it.  Or have I completely mis-understood?

-Steve

---

