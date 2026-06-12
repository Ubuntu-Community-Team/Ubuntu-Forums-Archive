---
title: "installation proble -figures!!"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by kacmaz on 2005-09-08
as usual, my attempt at installing linux failed again  ](*,) 

I didn't have much luck with official debian 3.0r2 so tried ubuntu....

I suspect the hardware I have is just too new!

I've got:
Asus P5AD2 deluxe motherboard
Asus PCI-E N6600 video card
Logitech wireless keyboard/mouse
DSL-302GL using PPoe connecting to internet
1xSATA Seagate HDD 160gb
1xIDE WD HDD: 80gb / 8mb buffer

Since I have WinXP on the SATA hdd, I wanted to install Ubuntu on the IDE drive.

I booted with the Ubuntu cd (v5.04) without any arguments on boot prompt, however installation didn't go further then the DHCP Connectoin Detection. For about 30mins, I wasn't sure whether it froze or still trying to detect!!!

Next installation attempt,  I used the "netcfg/disable_dhcp=true" argument at boot prompt. This time it seemed to install everything and asked me to remove the cd and reboot the computer. But during the reboot, I had a kernel panic and it frooze again...

Any help?

cheers

---

### Post by duminas on 2005-09-08
[QUOTE=kacmaz]as usual, my attempt at installing linux failed again  ](*,) 

I didn't have much luck with official debian 3.0r2 so tried ubuntu....

I suspect the hardware I have is just too new!

I've got:
Asus P5AD2 deluxe motherboard
Asus PCI-E N6600 video card
Logitech wireless keyboard/mouse
DSL-302GL using PPoe connecting to internet
1xSATA Seagate HDD 160gb
1xIDE WD HDD: 80gb / 8mb buffer

Since I have WinXP on the SATA hdd, I wanted to install Ubuntu on the IDE drive.

I booted with the Ubuntu cd (v5.04) without any arguments on boot prompt, however installation didn't go further then the DHCP Connectoin Detection. For about 30mins, I wasn't sure whether it froze or still trying to detect!!!

Next installation attempt,  I used the "netcfg/disable_dhcp=true" argument at boot prompt. This time it seemed to install everything and asked me to remove the cd and reboot the computer. But during the reboot, I had a kernel panic and it frooze again...

Any help?

cheers[/QUOTE]
 What is your CPU and what architecture CD are you using?

---

### Post by kacmaz on 2005-09-08
Ubuntu cd (v5.04)
and Celeron 2600

cheers

---

