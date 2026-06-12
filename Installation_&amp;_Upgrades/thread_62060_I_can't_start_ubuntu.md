---
title: "I can't start ubuntu"
date: 2005-09-03
forum: Installation &amp; Upgrades
---

### Post by hugoc on 2005-09-03
When I start Ubuntu I receive this message:

Starting Ubuntu...
chroot:relocation error:/lib/tls/i686/cmov/libc.so.6: symbol_dl_starting_up,
version GLIBC_PRIVATE not defined in file ld-linux.so.2 with link time reference
Kernel panic-not syncing: Attempted to kill init!


WHAT I CAN DO????

---

### Post by twowheeler on 2005-09-03
What packages have you installed before this happened?  Was it some of the glibc stuff?  

If you search for the error text in google, it finds lots of posts on this.    [This](http://lists.debian.org/debian-glibc/2005/03/msg00146.html) one for example talks about a version conflict.  I don't know if this has been fixed in hoary.  You might need to back out your recent installs until the problem goes away, that will at least let you identify which one is at fault.

---

### Post by hugoc on 2005-09-03
Before I wanted to create a new partition with Partition Magic and it failed then I aborted the action, later I can't open ubuntu normally.

---

### Post by twowheeler on 2005-09-04
I have seen some posts by people whose disks have been screwed over by Partition Magic.  Can't say, as I don't have it.  If you don't have anything important in the ubuntu partition, I would just reinstall.  If you do, I suggest you boot from a live cd, mount the partition, and see if it is readable.  If it is, there should be a way to salvage  the data at least by backing it up on to some other medium.  Let us know how it goes.  Good luck!

---

