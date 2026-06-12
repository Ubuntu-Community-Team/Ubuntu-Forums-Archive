---
title: "Upgrading to 12.04 deleted windows 7"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by joshwd36 on 2012-05-05
When I upgraded from Ubuntu 11.10 to Ubuntu 12.04, it worked, but my windows partition comes up as unknown on disk utility and I can't boot it. How do I fix it without losing all of my data?

---

### Post by darkod on 2012-05-05
If it doesn't open in the file manager, it doesn't look good. Open the terminal and post the result of:
sudo fdisk -l (small L)

for a start.

---

### Post by Tanker Bob on 2012-05-05
Try running update-grub in a terminal or from Ctrl-Alt-F2, then reboot. That may fix the boot issue if your Win7 setup isn't corrupt.

---

