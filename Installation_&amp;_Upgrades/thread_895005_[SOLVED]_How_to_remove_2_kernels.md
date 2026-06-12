---
title: "[SOLVED] How to remove 2 kernels"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by L337_K3y5 on 2008-08-19
I need to know how to remove linux kernel 2.6.25.7 and linux kernel 2.6.26.2, because I want to uninstall both and put the newer one back in.  THe thing is though, I've ```
sudo apt-get purge
``` the headers, image, and linux symlink that was located in ```
usr/src
```.  How do I completely remove both, because when I do ls -l in the ```
usr/src
``` it shows up like what's in the attachment pic.

---

### Post by Pumalite on 2008-08-19
Use Synaptic>Complete Removal

---

### Post by trevelyan on 2008-08-19
in synaptic search for "linux-image" (no quotes) and then mark for complete removal the ones you dont want.

---

