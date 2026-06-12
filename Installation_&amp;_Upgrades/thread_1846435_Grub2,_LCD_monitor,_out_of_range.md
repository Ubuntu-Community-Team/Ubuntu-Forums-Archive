---
title: "Grub2, LCD monitor, out of range"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by youboontu on 2011-09-19
Hi,
I recently installed Ubuntu and wanted to get it dual booting with my Windows 7. I had some problems during installation and had to use the flag "nomodeset" with F6 to bypass the "out of range" error message. I also had to uninstall dmraid. However, it was a successful install and I'm typing from the new Ubuntu version. I have an LCD monitor and when I turn the computer on it displays "out of range" error message, no Grub screen, and after several seconds I get a login screen.

I'm guessing there is some problem with Grub because Xserver or whatever seems to be working fine. I've edited /etc/default/grub to include "nomodeset". I've also installed Start-up Manger and set the resolution, bit-depth to monitor factory settings. I also installed the unsupported nVidia drivers, but they did nothing so I uninstalled them.

Specs:
Microteck 710s 17" LCD display
Ubuntu 11.04 Natty Narwhale

(solution):
After spending nearly all day trying new options and then restarting my computer to see if it works I finally found a solution about an hour after posting. In /boot/grub/grub.cfg the line looked like "kernel ...ro quiet splash nomodeset"

After changing the line to:
"kernel ro nomodeset quiet splash"
The grub finally loaded.

Boy just putting that one word in front made a difference. Computers are as strict as nazis!!

---

