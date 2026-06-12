---
title: "Ubuntu installer doesn't find existing Windows XP"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by hydrobates on 2010-01-08
Hi All

I'm trying to set up a dual boot of Ubuntu & Windows XP.

I have two hard disks installed - sda is 80GB and has an existing Windows setup on it, sdb is my 160GB data storage disk.

When I have installed Ubuntu on other machines, it has detected any exisiting OS's and offered to install Ubuntu alongside them.

However, this time Windows doesn't seem to be detected - it says 'no other operating systems found' and wants to install to my second (i.e. sdb) disk. I was intending for Ubuntu & Windows to sit side-by-side on the first hard disk.

Although I've installed Ubuntu before, I'm a bit of a novice and I'm not sure how to achieve this - where am I going wrong?

---

### Post by audiomick on 2010-01-08
Hi.
Is the installer seeing the first disk at all? There have been problems with this, i.e. the live cd installer not seeing all of the HDs in the machine. I've had it too.

You might have better luck with the alternative CD. It has a different partitioning tool, and seems to deal with multiple HD.s better.

---

### Post by hydrobates on 2010-01-08
Thanks. I think I might give the alternative installer a go.

It sort of does see the first disk, in that under the 'use entire disk' bit, my first hard disk is listed. But is doesn't recognise that Windows is on it & offer to install along side it.

---

### Post by tachuela on 2010-01-08
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by hydrobates on 2010-01-09
Thanks for your help folks.

I got round the problem by unplugging the second hard drive. The installer then recognised the first hard drive, and that Windows is installed on it, and let me install Ubuntu next to it.

---

