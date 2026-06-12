---
title: "Newb question..."
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by budhaboy on 2006-07-07
I've been using SuSE for years... I'm getting ready to install ubuntu on a box that has both a windows and a SuSE partition. Will the install script update or overwrite my current grub settings?

Thandks in advance for any comments, suggestions.

---

### Post by aysiu on 2006-07-07
If you're using the Desktop CD, it will overwrite SuSE's Grub.

---

### Post by budhaboy on 2006-07-07
> **aysiu said:**
> If you're using the Desktop CD, it will overwrite SuSE's Grub.

I downloaded/burned both desktop and server. I presume from this comment that the server version will not?

---

### Post by aysiu on 2006-07-07
I believe the server version will ask you where you want Grub installed.

If you install it to the MBR it may or may not automatically detect and add SuSE to the Grub menu. If you install it to the partition itself, you'll have to add Ubuntu to SuSE's Grub manually.

---

