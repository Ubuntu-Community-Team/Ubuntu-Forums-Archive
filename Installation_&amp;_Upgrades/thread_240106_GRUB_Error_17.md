---
title: "GRUB Error 17"
date: 2006-08-20
forum: Installation &amp; Upgrades
---

### Post by igrachev on 2006-08-20
Hello i just deleted my swap and / partitions in order to make a instalation from minimal instalation linux CD and build new OS but when i deleted the partitions and reboot the PC it refused to boot my windows OS with system msg 
GRUB loading ...
Error 17
now i can use my computer only true my CD-rom
How can i fix this error ?

---

### Post by noof on 2006-08-20
Did you have both windows and linux on the same disk, but different partitions? If that's the case, you've screwed your MBR. If you want to get back to windows you need to boot into rescue mode (using the windows install cd) and use the fixmbr command ([http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true))

---

### Post by Jonie on 2006-08-20
GRUB reads it's config file from / or /boot partition. It means it can't find its config, so it will not continue. If you deleted / it's no surprise ;) 

Reinstall linux - then you will have GRUB working again. Your windows installation is not affected.

---

