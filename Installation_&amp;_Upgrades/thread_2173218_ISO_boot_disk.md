---
title: "ISO boot disk"
date: 2013-09-08
forum: Installation &amp; Upgrades
---

### Post by mike_2 on 2013-09-08
I have Fadora 19 gnome 3. I wanted to make a ISO disk so I could check out Ubuntu the problem is when I change my boot options to disk instead of HDD it does not boot from disk and goes into Fadora then I try and open the disk in boxes and it says it can't communicate with Ubuntu and fails can I get help with this ? Thank you

---

### Post by ian-weisser on 2013-09-08
> **mike_2 said:**
> when I change my boot options to disk instead of HDD it does not boot from disk and goes into Fadora

The most likely problem is that your disk is unreadable or burning the disk somehow failed. When booting from the disk fails, the machine will move to the next option (HDD).
Try the disk in a different machine.
Try a different disk in this machine.
Try burning a new disk.

> **mike_2 said:**
>  I try and open  the disk in boxes and it says it can't communicate with Ubuntu and fails

That seems correct to me. Ubuntu is not an application that can be run on top of another OS. Ubuntu is meant to be booted.

---

### Post by VMC on 2013-09-08
I'm unclear as to what your trying to accomplish. Use a VM or loop-back. Are you wanting to crate an ISO of Fedora or Ubuntu. What does "open the disk in boxes" mean exactly.

I'm miss reading this somehow.

---

