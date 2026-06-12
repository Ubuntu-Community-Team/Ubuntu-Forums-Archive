---
title: "How do I unistall nvidia CUDA drivers?"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by N3tMast3r on 2009-11-16
Hi every one. I found that the nvidia CUDA drivers for my vdeo card (nvidia geforce 9400M) are kind of buggy so I decided to remove them.
I cannot get to uninstall them though. Can anyone help me?

Thank you,

A.

---

### Post by lemming465 on 2009-11-17
Which version of Ubuntu are you running, and were the nvidia drivers installed from an Ubuntu repository, or by direct download from nvidia.com?

If the former, try System -> Administration -> Hardware Drivers, click on the one with the green (enabled) icon, and then use the "remove" button on the bottom right, then reboot.

---

### Post by WillWhart on 2011-05-04
One more way - in Ubuntu you generally got an install package, or you can download it again from the CUDA site.
The same install NVIDIA_*run may be called with the switch --uninstall

---

