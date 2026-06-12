---
title: "Partition Question"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by Dr Small on 2006-11-22
Ok. We tried installing Ubuntu the other day, something went wrong with the setup, and lost the computer. So we finally did a recovery, and got Windows back. But the partition is still on the hard drive.

I was wondering, is it possible to try to install Ubuntu on that certain partition again? Or will it create another partition upon installation.

That is the part that has me baffled.
I want to be able to install Ubuntu on the same partition that it created upon installation, the previous time.

We have already cleared that partition, so any thing that was on it, is no longer there, so is there anyway to install ubuntu on that partition without creating another partition?

Thanks.

Dr Small

---

### Post by adwait on 2006-11-22
You said you have cleared that partition, what does that mean? Did you format that partition? Or did you delete that partition? Either way, you should be able to ask Ubuntu to install itself in the same place.

---

### Post by bulldog on 2006-11-22
Yes,when you come to the disk partitioner when you install Ubuntu again,choose manual partitioning and mount your swap as swap and your /  as root partition and if you had a separate /home partition you have to mount it as /home.
Format your swap and / partition,not your /home and your windows,and install  should be smooth.

---

