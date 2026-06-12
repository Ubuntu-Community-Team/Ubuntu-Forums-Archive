---
title: "Couple of Quick Partition Questions"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by Max Roswell on 2006-07-10
Hey, all...

I've set up dual-boot machines before, but I just got a new Acer laptop (100 GB hard drive) that has a hidden "XP recovery" partition, and I wanted to check a couple of things before I start the partitioning process.

My plan is to manually shrink the XP partition to about 20 GB or so and leave the hidden partition as is.  I'd like to make maybe another 30 GB partition that both OS's can read.  The rest will be for Ubuntu.

My questions are:

1.  After I manually shrink the existing XP partition to 20 GB and create the 30 GB shared partition, will the Ubuntu partitioner automatically take care of the rest?  I'm always a little foggy on swap space and so forth, but I'm worried that the hidden recovery partition might get wiped out.

2.  The shared partition should be Fat32 in order for XP and Ubuntu to both use it, right?

Thanks in advance!

---

### Post by Jagot on 2006-07-10
1.

If you do it with the Alternate Install CD, once you have shrunk the Windows partition, go back to th menu and select Guided Partitioning - that will set up your / and swap and everything without you having to do anything.

Not sure about the Desktop (live) CD, but it shoudld be fairly obvious - I think there's an option to resize the main partition and use the rest of the free space.  If you need to set up the partitions yourself just remember that the swap should be twice the size of your RAM and then / can be the rest.

You can see the graphical partition on the Desktop cd in action here:

[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

And the Alternate Install partitioner here:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)


2.

Yes

---

### Post by Max Roswell on 2006-07-10
You rule.

I'm writing this post from my properly-working, dual-booed, shockingly-correctly-partitioned-on-the-first-try, sweet, sweet new laptop.  I got a little turned around when I found out I had to deal with extended and logical partitions to get everything I wanted on here, but a quick search of these here forums got me squared away.

Thanks!

---

