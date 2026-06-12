---
title: "after dd from full 15GB part to 1.3TB part, shows same free space"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by teddmeister2 on 2010-12-08
I just used dd to clone a linux partition to a new hard drive, it had 800mb left on the old hard drive, after dd, new hard drive lists 1.29/1.3 terabytes full.  Is this what happens by default in dd?  How can I fix this?

---

### Post by anglican on 2010-12-09
> **teddmeister2 said:**
> I just used dd to clone a linux partition to a new hard drive, it had 800mb left on the old hard drive, after dd, new hard drive lists 1.29/1.3 terabytes full.  Is this what happens by default in dd?  How can I fix this?Indeed, this is exactly what dd does when you use it to copy a disk partition, the copied partition **should** look just like the original i.e. not use the additional space on the new drive (I presume the new disk is larger than the original). You can use gparted (or various other utilities) to resize the partition on the new disk... but not if it is mounted, so unmount it before trying to resize it. If it is the file system on which your OS resides and you've booted from it, you will need to go back to the original disk to do this (or use a live CD).

H

---

