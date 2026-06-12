---
title: "/boot full, cannot clean or update system"
date: 2013-06-03
forum: Installation &amp; Upgrades
---

### Post by aajyoung on 2013-06-03
I recently upgraded to 13.04 from 12.10.  I had no issues with automatic updates on 12.10, but now my /boot is full and I'm unable to install automatic updates.  I've used the janitor utility in ubuntu tweak to no avail, I've attempted to use synaptic, but the option to permanently remove kernels is grayed out/not available.  I've tried manually deleting old kernels in the terminal, but I'm very uncomfortable doing so since I don't understand the commands I'm using, nor the responses I'm receiving.  I had very little free space on my hard drive, but I threw what little I had left at the /boot partitions.  It allowed me to complete updates for a couple updates and is now full again.  I'm ignorant and lost...help!

---

### Post by Topsiho on 2013-06-04
I just removed older kernels en header files using synaptic, keeping the two latest.

In synaptic search for linux-image, and mark all installed for complete removal, except the latest, and preferably the two latest, just in case the latest proves to give troubles.

Then do the same for linux-header (twice as many files).

This gives you a vast amount of space in /boot. Every time you have to upgrade the kernel, you do this again to remove the oldest image and header files. Even on a netbook with only 6 GB of usable RAM I remain out of trouble this way.

Topsiho

---

