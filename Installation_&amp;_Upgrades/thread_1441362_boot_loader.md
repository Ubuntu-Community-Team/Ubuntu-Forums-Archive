---
title: "boot loader"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by mfaraday on 2010-03-28
Hello everyone,

I need help reloading grub onto my mbr.  I dual installed ubuntu with Windows Vista, but I accidentally deleted the partition holding ubuntu when I expanded the partition holding windows.  When I restarted my computer I got the error:

GRUB Loading
Unknown filesystem
grub rescue>

I intended to reinstall ubuntu, but I could shrink the windows partition even though I had the free space.  Any help here would be wonderful.

Thanks!

---

### Post by munchen800 on 2010-03-28
If you plan on reinstalling Ubuntu on the now empty partition then just do it and it will reinstall Grub. When you deleted your Ubuntu partition you deleted the grub files also. if you just want to go with your Windows os and you want to remove grub boot to the cd and do a fixmbr.

---

### Post by oldfred on 2010-03-28
If you are going to shrink the Vista partition you should use the windows tools.


How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

