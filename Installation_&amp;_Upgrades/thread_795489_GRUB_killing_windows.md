---
title: "GRUB killing windows"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by Azrael90 on 2008-05-15
2 drives
160 gig (Ubuntu)
200 gig (windows xp)
1 Raid for both of them

After installing Ubuntu I can only start Ubuntu. Windows is still on the drive but GRUB is not detecting it? Is this caused by the Raid controller ? How can I fix this ?

---

### Post by VMC on 2008-05-15
from within ubuntu. Open terminal and type 'sudo fdisk -l'. Write down the Windows /dev/sdx numbers

Then you can add to the last line to /boot/grub/menu.lst

Something looking like this:
title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1

---

