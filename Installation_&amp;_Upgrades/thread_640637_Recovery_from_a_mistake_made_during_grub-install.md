---
title: "Recovery from a mistake made during grub-install"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by unbuntu on 2007-12-14
Hi,

Here's my situation:

I installed Ubuntu on my machine first.  The grub is set up.
Then I installed Windows XP, which overwrites the MBR
I want to get grub back, so I boot the system up with a systemRescueCD, then under command line:
```
grub
```
```
root (hd0,4)
```  ; this is the partition where my Ubuntu installation is
```
setup (hd0,0)
```  ; here's the mistake...I should've typed setup (hd0)

Now I can't boot into Windows.
Is there a way to recover from this mistake?

Thanks!

---

### Post by mikewhatever on 2007-12-14
There are lots of options:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by psusi on 2007-12-14
(hd0) is not a valid target for root, it needs a partition number.  You say you can't boot windows?  What about Ubuntu?  If so then just go correct the entry.

---

### Post by unbuntu on 2007-12-14
I'm not looking for a "GRUB Howto"...As I said, I've already overwritten the XP Boot sector by mistake...and now even under Ubuntu I cannot mount the XP partition...it says:
```

Unexpected cluster per mft record (-1)
```

Also, I tried using a boot disk to do
```
fdisk /mbr
```
but that doesn't help either...

---

### Post by unbuntu on 2007-12-14
> **psusi said:**
> (hd0) is not a valid target for root, it needs a partition number.  You say you can't boot windows?  What about Ubuntu?  If so then just go correct the entry.

I can boot Ubuntu.  Please read my previous post.  Looks like my Windows partition is corrupted.  But the usual ways (like fdisk /mbr) doesn't correct the problem.  Is there any other ways?

---

### Post by psusi on 2007-12-14
Wow, you still have an old msdos boot disk around with fdisk on it?  

Boot the windows cd into the recovery console and try the FIXBOOT command.

---

### Post by unbuntu on 2007-12-14
> **psusi said:**
> Wow, you still have an old msdos boot disk around with fdisk on it?  

Boot the windows cd into the recovery console and try the FIXBOOT command.

Yay FIXBOOT works!  You just saved me 5-6 hours of work!  Thanks a bunch.

---

