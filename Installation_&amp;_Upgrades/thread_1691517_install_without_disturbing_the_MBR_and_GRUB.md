---
title: "install without disturbing the MBR and GRUB"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by th1bill on 2011-02-20
I have 10.04 installed on my 320 gig. SATA hdd and i have an 80 gig IDE that I want to install Mepis on but i do not want to upset my boot order.  Can I install the Mepis and later update grub so as to have Ubuntu as my default?

---

### Post by sikander3786 on 2011-02-20
You need to refer to Mepis documentation or forums. If the installer gives you a choice to Install or Not Install the bootloader, select not to install it and later run *sudo update-grub* from your Ubuntu install.

---

