---
title: "No video from LiveCD on A6 APU"
date: 2012-04-14
forum: Installation &amp; Upgrades
---

### Post by Auax on 2012-04-14
Hi all, 

I'm attempting to install Ubuntu 11.10 on a Toshiba Satellite L775D with the A6-3420M APU. 

Whenever I attempt to boot the liveCD environment, I get a completely black screen. I still get the startup music and all, so I can only assume the default drivers don't play nice with the A6's integrated Radeon graphics.

Does anyone know if there is a working video driver for the A6 and what it is/how to use it to boot up the liveCD?

Thanks, Auax.

---

### Post by paulpsicle on 2012-04-15
well, the proprietary fglrx driver works...
To install:
[LIST]
[*]On the boot menu, press F6 and select "nomodeset"
[*]Boot to the installer. Do not exit to the full desktop
[*]Go through the installation process
[*]reboot
[*]press Ctrl-Alt-F1
[*]log in
[*]type "sudo apt-get install fglrx"
[*]Done!
[/LIST]

---

### Post by drremulak on 2012-04-29
Had a similar problem using a Toshiba Satellite. I changed a setting for the display selection in the BIOS from "auto-select" to "LCD only and it works..

---

