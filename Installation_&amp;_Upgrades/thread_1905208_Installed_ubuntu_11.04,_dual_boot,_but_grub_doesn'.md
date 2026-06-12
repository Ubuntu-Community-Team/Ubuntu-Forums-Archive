---
title: "Installed ubuntu 11.04, dual boot, but grub doesn't show up."
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by Fishtank on 2012-01-06
Hello, i'm a newbie and followed an installation tutorial and I think it ended up installing ubuntu completely instead of dual boot. Unfortunately my tutorial is in windows and I can't get to it. Is there some way I can see if windows is still actually on my hard drive and if it is, how can I get to it? Jody.

---

### Post by Megaptera on 2012-01-06
Removed my reply.
See post below from darkod.

---

### Post by darkod on 2012-01-06
First of all, stop booting the hdd. Use the ubuntu cd or usb stick and boot into live mode with it.

Post the result of:
sudo fdisk -l (small L)

If you really overwrote your windows partitions and you want to restore some data from it, booting the hdd will make this more difficult. New information will be written over the old one making the recovery impossible.

---

