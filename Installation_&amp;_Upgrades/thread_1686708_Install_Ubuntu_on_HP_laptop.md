---
title: "Install Ubuntu on HP laptop"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by Ubntu on 2011-02-12
So I just found out how to install Ubuntu, and found something wrong. I made a partition for the install and when I went to install it, it already had 4 partitions. The recovery and other stuff, so that means the partition I made can not be used. D: How do I fix this?

---

### Post by jerrrys on 2011-02-12
is this vista ?

---

### Post by Ubntu on 2011-02-12
> **jerrrys said:**
> is this vista ?

No, I have Windows 7.

---

### Post by jerrrys on 2011-02-12
vista had partitioning problems all its own, but we don't have to worry about that.

if you are running 10.10 then installing (partitioning) is different from mine  and maybe a 10.10er will come along and assist

---

### Post by Ubntu on 2011-02-12
> **jerrrys said:**
> vista had partitioning problems all its own, but we don't have to worry about that.

if you are running 10.10 then installing (partitioning) is different from mine  and maybe a 10.10er will come along and assist

Okay, hopefully because I would really like to use Ubuntu.

---

### Post by Hedgehog1 on 2011-02-12
> **Ubntu said:**
> So I just found out how to install Ubuntu, and found something wrong. I made a partition for the install and when I went to install it, it already had 4 partitions. The recovery and other stuff, so that means the partition I made can not be used. D: How do I fix this?

You created a forth partition yourself?

May I suggest you do the following so the Ubuntu Installer can do the hard work for you:

Using the disk management tool in Windows 7, you can delete the new partition you just created and then expand the windows 7 partition to fill that space.

Then boot up on the Ubuntu live CD and do a side-by-side install, letting the install take the disk space back (based on how much you want it to have).  It will make an extended partition and then break that up into 2 partitions - the big one for your Ubuntu OS and data, and a little one for swap space.

[SIZE="3"]SOME WORDS OF CAUTION:[/SIZE]

[SIZE="2"]  * Always back up your personal data before you futz with partitions.
  * Please run Defrag on your Windows disk several times before you install Ubuntu in a side-by-side.[/SIZE]

I am running Windows 7 with Ubuntu 10.10 just like you are wanting to, and it works very well.

I used the method I described to install it - including the defrag & backup.

:KS

---

### Post by Ubntu on 2011-02-12
> **Hedgehog1 said:**
> You created a forth partition yourself?

May I suggest you do the following so the Ubuntu Installer can do the hard work for you:

Using the disk management tool in Windows 7, you can delete the new partition you just created and then expand the windows 7 partition to fill that space.

Then boot up on the Ubuntu live CD and do a side-by-side install, letting the install take the disk space back (based on how much you want it to have).  It will make an extended partition and then break that up into 2 partitions - the big one for your Ubuntu OS and data, and a little one for swap space.

[SIZE=3]SOME WORDS OF CAUTION:[/SIZE]

[SIZE=2]  * Always back up your personal data before you futz with partitions.
  * Please run Defrag on your Windows disk several times before you install Ubuntu in a side-by-side.[/SIZE]

I am running Windows 7 with Ubuntu 10.10 just like you are wanting to, and it works very well.

I used the method I described to install it - including the defrag & backup.

:KS

No I did not create a forth partition. HP has other partitions on here and I don't know what to do. :confused:

---

