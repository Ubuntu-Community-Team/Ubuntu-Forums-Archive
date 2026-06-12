---
title: "GRUB configured drives wrong"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by The Grum on 2007-04-23
Hi.

Just installed Feisty over Edgy (clean install). The system would not boot into either Linux or Windows as for some reason as GRUB labelled the drives the wrong way round - made Linux (hd1,0) instead of (hd0,1) and vice versa.

I have no idea why it did this. Any ideas?

---

### Post by zvacet on 2007-04-23
Try edit grub and make changes there

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by The Grum on 2007-04-24
Got Feisty to boot after using the live cd to edit that file. I just found it strange that the drives were wrongly identified. This didnt happen with Edgy, even after moving the Linux drive from IDE to SATA.

---

