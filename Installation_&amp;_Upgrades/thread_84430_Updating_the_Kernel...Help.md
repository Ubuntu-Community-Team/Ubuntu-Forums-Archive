---
title: "Updating the Kernel...Help"
date: 2005-10-31
forum: Installation &amp; Upgrades
---

### Post by Plank117 on 2005-10-31
How do I update the kernel? I'm running 2.6.8 or some other vintage release, but apparently there's a new and exciting release out there. Also, when I boot into Ubuntu I get a message prophesying that no kernel older than 2.6.10 is supported. On a related note, I've updated before (but forgotten how to do it) and the old kernel is still listed in the GRUB menu. How do I get rid of it?

---

### Post by 23meg on 2005-10-31
Did you manually install that kernel? Which Ubuntu version are you using? Also, type ```
uname -r
``` to learn the exact kernel version you're using.

---

### Post by linbetwin on 2005-10-31
I've got a similar problem. Changed my kernel from 386 to k7
> sudo apt-get install linux-k7
but the 386 kernel is still listed in Grub. How do I remove it safely?

---

### Post by 23meg on 2005-10-31
Find your 386 kernel by doing a search for "linux-image" in Synaptic, and choose to remove it.

---

### Post by Plank117 on 2005-10-31
I updated the kernel manually in Hoary and now I've updated to Breezy.

---

