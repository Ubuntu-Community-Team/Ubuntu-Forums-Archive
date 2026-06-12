---
title: "Fiesty Fawn install question"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by inviz on 2007-10-01
Ok, I've got a retarded install question.

I currently use Windows Vista and I can't live without it, but I really want to start using Ubuntu Fiesty Fawn. So what I want to do is set up a small partition of like 30-40 gigs and use Ubuntu on that while Vista still has around 120gigs. But when I went to install Ubuntu I got scared at the partitioner when it said:

"Reformat your old partition, blah blah blah." And then it said "New partition size" but I was wondering, is it talking about the brand new partition that you're creating, or the new updated size of my old Vista partition?

---

### Post by rsambuca on 2007-10-01
You must first use the Vista Disk Manager to 'shrink' the existing vista partition.  Then use the ubuntu disc to install to the free unallocated space.

---

### Post by astromech on 2007-10-01
When you install Windows it likes to take over the whole hard drive so you have 1 partition. just use guided resize partiton number one and use free space you resize using the little slider bar. Always back up first!

---

### Post by logos34 on 2007-10-01
If [this]("http://img379.imageshack.us/my.php?image=feistydual06rw5.png") is what you are seeing, it means the size of the vista partition after you shrink it.  Then you create a linux '/' (root) and /swap in the new free space.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by rsambuca on 2007-10-01
> **astromech said:**
> When you install Windows it likes to take over the whole hard drive so you have 1 partition. just use guided resize partiton number one and use free space you resize using the little slider bar. Always back up first!

That doesn't work very well with Vista.  I highly recommend using Vista's Disk manager to shrink the vista partition first.

---

### Post by inviz on 2007-10-01
Ok, thanks a bunch guys. This helped out a lot.

---

### Post by Hatfield on 2007-10-09
Deleted.

---

