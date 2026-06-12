---
title: "losing hd space with each ubuntu install"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by Ryan_macy on 2008-08-03
I am running a dell 1330n and I lose hd space every time I do a fresh install.

I originally had 160gb now I have 141gb.

Whats going on here, and further more, how can I fix it?

---

### Post by Pumalite on 2008-08-03
Get Gparted Live CD and delete everything you are not using; then install.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn iso to disk and boot from it.
(after you delete format the free space)

---

### Post by Ryan_macy on 2008-08-03
> **Pumalite said:**
> Get Gparted Live CD and delete everything you are not using; then install.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn iso to disk and boot from it.
(after you delete format the free space)

is there any way to fix it without reinstalling?

---

### Post by kihjin on 2008-08-03
I would first do sudo fdisk -l

At the top it will have a line for each disk like:

Disk /dev/sda: 250.0 GB, 250059350016 bytes

Then do df -h

This will show you which partitions are eating away your disk space.

There might be partitions which aren't mounted, do a comparison between

mount

and

sudo fdisk -l

Hope you can get this figured out.

---

### Post by Pumalite on 2008-08-03
> **Ryan_macy said:**
> is there any way to fix it without reinstalling?
I'd advise you to get your drive cleaned up and reinstall.

---

### Post by Ryan_macy on 2008-08-03
ok im going to reinstall :(

I'll update this thread and give you a heads up on the results.

---

### Post by Ryan_macy on 2008-08-04
well no luck, I have 149.5gb in my hdd, the other 10.5 just vanished.

anyone have a fix for this, its driving me nuts

---

### Post by cariboo on 2008-08-04
You have to remember in a stock installation Linux reserves 5% of the hard drive space for root to use if the hard gets filled up and becomes unusable. I'm not sure if gparted will let you use the reserved space, but parted will, if you do a manual partition. The other thing you should look at is the size of your swap partition, it should be set at twice the amount of ram you have. 

Jim

---

### Post by Liakath on 2008-08-04
Dear Ryan,

> **Ryan_macy said:**
> well no luck, I have 149.5gb in my hdd, the other 10.5 just vanished.

anyone have a fix for this, its driving me nuts

I think you need not worry about the space reported.

Your 160 GB Disk has only 160,000,000 Bytes which when translated in to actual GB is only 160,000/1024=156.25 GB in reality.

While formatting with any file system like NTFS / EXT3 there are some overheads maintained which is roughly about 5% and only the balance is available for storage.

So the 149.5 GB reported by any partition manager is to be seen in light of above.

Liakath

---

