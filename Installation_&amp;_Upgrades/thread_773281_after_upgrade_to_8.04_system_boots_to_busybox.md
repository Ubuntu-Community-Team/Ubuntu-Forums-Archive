---
title: "after upgrade to 8.04 system boots to busybox"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by peter_t on 2008-04-28
I am new to linux so please excuse my ignorance.  After running the upgrade to 8.04 from the Update Manager in 7.10, my laptop (dell m1330n) boots to busybox.  If I select the 2.6.26-16-generic kernel it loads fine but I don't even know if this is the kernel that I should be running.  Any suggestions would be appreciated.

---

### Post by radpup on 2008-04-28
I had the same issue....I found a fix if you are using supergrub and have SATA drives. Simple change in the supergrub startup script.

     D

> **peter_t said:**
> I am new to linux so please excuse my ignorance.  After running the upgrade to 8.04 from the Update Manager in 7.10, my laptop (dell m1330n) boots to busybox.  If I select the 2.6.26-16-generic kernel it loads fine but I don't even know if this is the kernel that I should be running.  Any suggestions would be appreciated.

---

### Post by peter_t on 2008-04-28
> **radpup said:**
> I had the same issue....I found a fix if you are using supergrub and have SATA drives. Simple change in the supergrub startup script.

     D

Ahhh, thank you that seems to have corrected it.  What is the difference between the virtual and generic kernels?

---

### Post by radpup on 2008-04-29
Not sure on that one....I'm somewhat of a newb, on my first install. When I got the busybox error, I spent a couple days trying to work the issue until I found a way to fix the boot script. 

  d

> **peter_t said:**
> Ahhh, thank you that seems to have corrected it.  What is the difference between the virtual and generic kernels?

---

