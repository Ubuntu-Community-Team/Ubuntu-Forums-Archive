---
title: "How to switch from Ubuntu-generic to Ubuntu-virtual kernel"
date: 2011-07-13
forum: Installation &amp; Upgrades
---

### Post by cmdematos on 2011-07-13
I have a VM image that I recently migrated form VirtualBox to KVM. It uses the generic kernel and I would like to use the virtual kernel instead.

What is the procedure to switch kernels?

Also, what are the relative merits of the generic, virtual and server kernels?

---

### Post by TheR on 2011-07-15
AFAIK no way.

I asked the same question one year ago.

One of the differences is that virtual kernel is very light. 30MB compared to 128 MB when upgrading. 


by
TheR

---

### Post by cmdematos on 2011-07-28
I found the information above to be incorrect. You can switch to a Virtual Kernel at any time, simply issue a sudo apt-get install linux-virtual and it will all be done for you.

---

