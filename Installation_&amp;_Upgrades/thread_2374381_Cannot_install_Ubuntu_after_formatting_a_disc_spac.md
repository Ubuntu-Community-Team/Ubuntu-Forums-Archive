---
title: "Cannot install Ubuntu after formatting a disc space where the previous ubuntu was"
date: 2017-10-15
forum: Installation &amp; Upgrades
---

### Post by Marek_Kosinski on 2017-10-15
[COLOR=#111111][FONT=Ubuntu]I've stumbled across a problem which I cannot find an answer to, so I'm forced to ask for your wisdom and help. So untill yesterday I had Windows 7 and Ubuntu installed on my PC. Windows 7 was installed on my SSD disc and the Ubuntu was installed on HDD disc. I've bought a new SSD just for ubuntu, and after installing it into the PC. I thought that the best way to erase Ubuntu and reinstall it is to do it through disc managment on Windows 7. After formatting it and rebooting the system did not want to start, nor Windows or Ubuntu. I tried to launch a Ubuntu without installation from USB Pendrive, unfortunetely it did not work. Same goes with installing it. The errors which are printed are following:


[/FONT][/COLOR]```
[COLOR=#111111][FONT=Ubuntu]ACPI Error: [\SR.PC10.XHC.RHUB.HS11] Namespace lookup failure,
AU_NOT_FOUND (20160930/dswload-210) ACPI Exception : AE_NOT_FOUND, During name lookup/catalog (20160930/psobject-227)
[/FONT][/COLOR]
```[COLOR=#111111][FONT=Ubuntu]

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]After a few seconds the screen gets glitched and it looks like this: [IMG]https://i.stack.imgur.com/4Vf9j.jpg[/IMG][/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've recovered the windows by installing it once again from usb boot, but even after doing that, I cannot install the ubuntu. The same errors appear all the time.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Does anyone know how to solve this? Thanks in an advance.[/FONT][/COLOR]

---

### Post by ubfan1 on 2017-10-15
Looks like a video problem, from the nouveau references in the hard-to-read bottom of the screen. Try the "nomodeset" parameter on the linux boot line in grub, edit the grub commands by typing "e" (instructions at bottom of screen), then add nomodeset at the "quiet splash" location, and ctrl X to boot.  You can then add the proprietary Nvidia drivers to avoid this in the future.

---

