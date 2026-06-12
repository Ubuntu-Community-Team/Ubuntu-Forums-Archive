---
title: "partition help"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by maxgt1 on 2008-11-12
I have a sata 160gb HD partitioned 60 60 40gb with xp on the first storage (programs pics e.t.c.)on the second.
How do i get Ubuntu 8.10 to install ( dual boot ) on the 40gb partition whilst leaving the other two intact?
Iam new to this so any advice will help, even if it means formatting the whole disk i would rather not but heyho

---

### Post by Pumalite on 2008-11-12
You can install; go 'Manual' and pick the 40 GB partition. Give it  a mount point '/' Format ext3 and continue with the installation.

---

### Post by maxgt1 on 2008-11-12
I will try that thanks:)

---

### Post by Coreigh on 2008-11-12
If you install Ubuntu on the first partition (40gb) this will overwrite Windows. Is that what you want? I thought you said dual boot?

You would want to either split the 40 in to two 20s or install Ubuntu on the 3rd partition.

---

### Post by Pumalite on 2008-11-12
'How do i get Ubuntu 8.10 to install ( dual boot ) on the 40gb partition whilst leaving the other two intact?'

---

### Post by Coreigh on 2008-11-12
So you want to _keep_ Windows but have Ubuntu also, and both are to be on the 40gb partition?

The easiest is to use Wubi.[http://wubi-installer.org/](http://wubi-installer.org/)

A more advanced [more complicated] method would involve resizing the 40gb partition in to two 20gb partitions having Windows on the 1st, Ubuntu on the 2nd and your 60gb partitions would then be #3 and #4. But That would be a lot more work and could confuse Windows if you have thinkgs installed and configured in Windows to use one or both of the 60gb partitions.

Wubi it is.

---

### Post by Dazed_75 on 2008-11-12
Not the way I read his original post. I read it that he has the following partitions

1) 60 GB with a bootable XP
2) 60 GB with data and programs (originally for use from xp)
3) 40 GB not currently used, format unknown but where he wants ubuntu

If he does a normal (not wubi type) install he has two options as I see it:

1) Delete the 3rd partition, use the live CD to install and when it gets to partitioning, select guided to the largest unused space (the 40 GB area), or
2) Do not delete the 3rd partition and when the install gets to partitioning, select manual, resize that partition, format it to ext3, and add a swap partition.  Clearly this option is harder for someone less technical.

---

### Post by Coreigh on 2008-11-12
My Bad.

I did in fact read the post wrong. I apologize. :rolleyes:

Just run the installer  from the regular Ubuntu CD you have and when you get to the partitioning part choose _guided_ and install to the 40gb partition.

---

### Post by Pumalite on 2008-11-12
You are better off with 'Manual'. You have more control. If you install in the 40 GB partition; the installer itself will create a /swap partition. You can also make the 40 GB partition an extended partition and within it; make 2 'New' logical partitions: one with mount point '/' and one /swap.

---

