---
title: "booting ubuntu hangs"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by nguyen_t_anh on 2006-06-16
Hi,

I installed the ubuntu 6.06 as normal (I have longtime experience with installing and running redhat and debian). When rebooting the system, ubuntu hangs at:

Uncompressing the kernel, OK. Booting the kernel.

Please help. Thanks in advance.
tuan

---

### Post by d.j.schroeder on 2006-06-16
I had that exact problem.  It was a new system build and it turned out that one of my memory sticks was bad.  It may be unlikely that it is the case for you but I thought I'd mention it in case you hadn't already run memtest.

---

### Post by nguyen_t_anh on 2006-06-17
I had tried to run memtest, it was fine. I have installed fedora and debian on the same laptop (dell latitude d400). Stupid Ubuntu :-(

---

### Post by rcarring on 2006-06-17
When grub loads, hit Esc and select safe recovery mode.

If it still hangs then 

a) your kernel won't boot as it is corrupt and you may have to reinstall
b) memory issue

---

