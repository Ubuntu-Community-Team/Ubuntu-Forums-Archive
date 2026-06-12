---
title: "Is it better to install to one fast drive or a raid0?"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by bartos on 2008-12-02
I am looking to install a new hard drive, Either a 1-tb or a 10,000 rpm Raptor.I have 2 320-gb drives to make the raid. What i would like to have is the root partition on a fast drive to access and load source files fast while having my home partition safe on a regular drive.
If anyone has experience with either setup , I would appriciate some input.So either I buy a Raptor for root or I buy a 1-tb drive to transfer everything off my 320s and make the 320s a raid0.

Thanks

---

### Post by Kadin2048 on 2008-12-02
Define "better."  As you seem to understand, a RAID0 setup is twice as dangerous as having a single drive.

If you're just using a regular hard drive, and it fails, you lose your stuff.

But if you have RAID0, and either one of the two (or more) drives fail, you lose your stuff.

Frankly I would not use RAID0 as a system partition; I've had lots of hard drives fail, and I can't imagine having to reinstall my whole system every time one crapped out.  (My home server has a RAID5 across 4 drives with a hotspare.)  You need to think of not only what data is totally irreplaceable, but also what data would take a lot of your time to rebuild, and what your time is worth.

So anyway, if your question is whether I'd go with the one large drive or two smaller drives as stripes, I would go for the single larger drive.  I would only use the two smaller drives in stripes for /tmp space, or if you're doing something like digital video where you need a lot of very short-term, high-speed storage.

---

### Post by bartos on 2008-12-02
> Define "better.

Better = Faster

> If you're just using a regular hard drive, and it fails, you lose your stuff.

But if you have RAID0, and either one of the two (or more) drives fail, you lose your stuff.



That is why I would put my Home Partition on a drive that is safe so if a raid or fast drive fails, I only lose the operating system not my personal settings and files.

I am looking for info about performance gains by configuring my partitions in this manner.

---

