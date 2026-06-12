---
title: "i386 and RAM"
date: 2005-08-16
forum: Installation &amp; Upgrades
---

### Post by ace2005 on 2005-08-16
I read this:

> Are you running an i386 kernel? To take advantage of 1G or more you need to install an i686 kernel or i686-smp kernel. Check your /var/log/kern.log. Does it look like this?:

klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
localhost kernel: Inspecting /boot/System.map-2.6.8.1-3-386
localhost kernel: Loaded 28166 symbols from /boot/System.map-2.6.8.1-3-386.
localhost kernel: Symbols match kernel version 2.6.8.
localhost kernel: Warning only 896MB will be used.
localhost kernel: Use a HIGHMEM enabled kernel.
localhost kernel: 896MB LOWMEM available.


This is what an -686 kernel looks like:

klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
localhost kernel: Inspecting /boot/System.map-2.6.8.1-4-686-smp
localhost kernel: Loaded 27787 symbols from /boot/System.map-2.6.8.1-4-686-smp.
localhost kernel: Symbols match kernel version 2.6.8.
localhost kernel: Linux version 2.6.8.1-4-686-smp (buildd@rockhopper) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 SMP Wed 
localhost kernel: 1150MB HIGHMEM available.
localhost kernel: 896MB LOWMEM available. 

So i want to know that if i install Ubuntu will all of my ram be usd? (1.25 GB)

or do i have the option to pick the i686 kernel when Ubuntu installs?

---

### Post by heimo on 2005-08-16
As I've understood, you need to install 686-kernel after you've installed Ubuntu. Fortunately, it's very easy to do using Synaptic package manager.

---

### Post by doclivingston on 2005-08-16
All you need to do is use synaptic or apt-get to install either "linux-686" (intel) or "linux-k7" (amd).

---

