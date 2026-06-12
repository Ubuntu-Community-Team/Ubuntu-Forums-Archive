---
title: "[SOLVED] Just installed Ubuntu, but no bootloader?"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by BattleGnome on 2008-05-08
I Just installed ubuntu, after the installation I was prompted to restart my pc. The pc just boots into windows, theres no bootloader installed. When doing the install I just followed pages 1-7 in graphical mode and did not go int othe advanced settings. Howcome the installer no longer installs a bootloader? Using windows vista 32-bit & ubuntu 8.04.

---

### Post by dstew on 2008-05-08
Did you install "Inside Windows" or from a fresh boot of the Live CD? If you installed from a booted Live CD, grub by default goes into the MBR of the first hard disk, as reported by your BIOS. If you think grub was mis-installed, we can install it again properly.

---

