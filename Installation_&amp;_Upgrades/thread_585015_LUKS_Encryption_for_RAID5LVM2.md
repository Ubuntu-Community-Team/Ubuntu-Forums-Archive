---
title: "LUKS Encryption for RAID5/LVM2"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by trmentry on 2007-10-21
I have a Gentoo server that is running with 8x400 drives in a Raid5 set.  /dev/md0 is then 'carved' up using LVM2.

I noticed while playing with Gutsy in a vm that it has the encrypt option at install for / and /swap.   And since I've been thinking of moving my server to Ubuntu this comes at a great time. 

How can I go about using the encryption that is there after the install of the base server to encrypt md0 or the lvm2 'partitions'?   Currently I have 10 lvm2 'partitions' on my server and would really like to not have to enter the luks passwd in all 10 times.  

My thoughts are to encrypt /dev/md0 and then after it is unencrypted and running, carve it up via lvm2.  That way if I want to resize, add space, etc to the lvm2 logical volumes I can and not be affected by each 'partition' being encrypted.  

I found this [**post**](http://ubuntuforums.org/showthread.php?t=578667&highlight=gutsy+luks) and it looks like what I need to do to /dev/md0.  But I'm not sure.

Can someone please point me in the right direction or offer comments/advice?

Thanks

---

### Post by kidders on 2007-10-22
Hi there,

Just a few comments, really ...

Both Gentoo & Ubuntu have been capable of this sort of thing for quite a while, so don't feel like you have to switch distro, just to encrypt your server's on-disk data. The explicit addition of the feature to Gutsy's installer is certainly nice, but tbh I wouldn't feel completely confident in its ability to do it right, just yet. So, even if you *do* switch to Ubuntu, I would still recommend configuring the encryption manually (especially on a production server), at least until the installer is a few months old. In any case, if your server *is* a production machine, you should _not_ consider installing Gutsy on it. It's just too new.

The other suggestion I would make is to give some thought to failure scenarios on your box. Combining RAID & encryption drastically increases the probability of disastrous failures (as distinct from minor ones), because the on-disk data is not laid out in the traditional way. So, for instance, if your encryption is sitting *underneath* your LVM, the probability of single bit errors causing the loss of the entire structure goes up. Essentially, the use of on-disk encryption has the potential to make what would otherwise be an inconsequential glitch much more significant, so it's worth taking a moment to think about risk management.

---

