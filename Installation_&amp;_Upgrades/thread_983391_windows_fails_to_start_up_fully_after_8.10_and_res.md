---
title: "windows fails to start up fully after 8.10 and resize"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by tgpqaz on 2008-11-15
I upgraded to 8.10 but it overwrote the grub menu.I then used gparted live cd to add 15gbs to the windows partition. I put this back into the menu under the first entry in grub:
title		MS Windows
root		(hd0,1)
makeactive
chainloader	+1

When it booted the first time it checked the drive and continued. all it showed then was windows and logo. plz help

---

