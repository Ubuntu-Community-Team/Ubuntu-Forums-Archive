---
title: "How to Reinstall (cannot currently login)"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by CaptainPants on 2008-09-06
Hi,

I have a computer dual booted with XP and Ubuntu (Windows installed first).  When I upgraded to Hardy Heron, it seems like Ubuntu just kinda broke itself, lol.  It boots up to the login screen, but when I login it just freezes.

Last time I upgraded Ubuntu HAL stopped working.  So I would just like to start over by clearing off the Ubuntu partition and then do a clean install of the new Hardy Heron version (is it still considered clean if there's still a Window's partition on the hard drive?).

I have two questions:

1. In order to backup my files I tried Damn Small but it could only find the Windows partition.  I also tried several Windows applications for ext1/2 file systems, but none of them worked either. So how can I get to the Ubuntu files?

2. How should I go about clearing off the Ubuntu partition so I can start fresh (except still with Windows XP on it)?

Thanks in advance for any help!

---

### Post by aysiu on 2008-09-06
With the Ubuntu live CD, you should be able to mount both the Windows and Ubuntu partitions. (Technically, you should be able to do this with DSL also, but DSL may not make it immediately obvious how to do so.)

Reinstalling is a lot easier than you think it is, also, since you already had it set up in separate partitions.

1. Boot the Ubuntu CD

2. Mount the Ubuntu and Windows partitions. Back up your files.

3. Unmount both partitions.

4. Install Ubuntu and make sure you select the old Ubuntu partition as the partition to install Ubuntu to.

---

### Post by Pumalite on 2008-09-06
You have to choose 'Manual' to do it.

---

### Post by CaptainPants on 2008-09-06
Thank you for the quick replies.  I'll do that.

---

