---
title: "repair after removing compiz and metacity"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by farchumbre on 2010-04-01
hi
I removed compiz from synaptic and also metacity.
now ubuntu boots but only in terminal mode.
i tried to re install both synaptic and metacity from the terminal but i have no internet connection via the terminal, how should i connect?
i am also trying to use the ubuntu 9.10 cd to repair my ubuntu but i don't know how.
any suggestions?

---

### Post by tom4everitt on 2010-04-01
1. Boot from the live cd
2. Open a terminal
3. Mount the ubuntu partition: sudo mount /dev/sda1 /mnt
4. Change root to you ubuntu file system: sudo chroot /mnt
5. Install ubuntu-desktop (which should install everything you need): sudo apt-get install ubuntu-desktop

In step 3 you might have to adjust sda1 to the correct partition. 

Its important that you use a 32-bit live cd if your system is 32-bit and vice versa, otherwise the chroot command in step 4 won't work.

---

### Post by 4nd12345 on 2011-12-21
....

---

