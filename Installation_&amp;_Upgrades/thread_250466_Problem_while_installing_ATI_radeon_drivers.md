---
title: "Problem while installing ATI radeon drivers"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by vzkid111 on 2006-09-04
I just installed the latest ATI radeon drivers to work with my radeon x1300, after i finished and restarted my system, my monitor displays that resolution is too high, i dont know how to fix besides just reinstalling ubuntu but then i dont have the drivers which i need for XGL which is part of the reason i got linux.

---

### Post by Princey on 2006-09-04
> **vzkid111 said:**
> I just installed the latest ATI radeon drivers to work with my radeon x1300, after i finished and restarted my system, my monitor displays that resolution is too high, i dont know how to fix besides just reinstalling ubuntu but then i dont have the drivers which i need for XGL which is part of the reason i got linux.

Try this from the terminal ```
sudo dpkg-reconfigure xserver-xorg
``` and follow the wizard. Pay particular attention to the part where it deals with the monitor resolutions. Delete uncheck those you don't want.

---

