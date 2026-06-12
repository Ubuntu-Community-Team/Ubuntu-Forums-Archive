---
title: "Boot Drive not Recognized"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by cdwalsh on 2008-02-18
I bought a new hard drive for my UBUNTU OS.
 I have a seperate drive for Vista and XP.
Install went fine. Once I restarted my system. UBUNTU shows all OSes
When I choose UBUNTU it wants to boot from the first drive
(hd1,0) with Vista and XP.
How do I redirect UBUNTU to the Second drive.

---

### Post by Existentialist on 2008-02-21
Counting begins at 0 in grub.  So your first hd is hd0, second hd1, and so on.  From grub, you can press e to edit the boot entries and you can try pointing it to the correct hd.  Do the windows boot fine?

---

