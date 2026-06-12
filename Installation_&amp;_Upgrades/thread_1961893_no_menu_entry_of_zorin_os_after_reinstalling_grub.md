---
title: "no menu entry of zorin os after reinstalling grub"
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by aneez004 on 2012-04-20
From a live cd of zorin os 5.2 64 bit,I chose live session.I installed boot-repair and recovered grub.After rebooting system,there was only entry of windows 7 in grub and no menu entry of zorin os.Please suggest solution to recover zorin or to add menu entry manually

---

### Post by aneez004 on 2012-04-20
problem solved


One of my Windows software writes DRM where it should not be allowed
to. (in the disk boot sector).Run Boot-Repair, click "Advanced options", go to the "GRUB
options" tab, tick the "FlexNet" option, then apply.

---

