---
title: "Screen Flickering When Booting Ubuntu"
date: 2024-10-07
forum: Installation &amp; Upgrades
---

### Post by victoranthony on 2024-10-07
Hi everyone,


I recently installed Ubuntu 19.10 in a dual boot setup with Windows 10. Every time I select Ubuntu from the GRUB menu, I see a list of processes running, and the Ubuntu logo flickers continuously. This same issue occurs when I try to boot from a live USB for installation. I have looked for solutions but not been able to resolve it.
Has anyone else experienced this problem? [SIZE=1][[COLOR=#ffffff]white screen[/COLOR]]("https://whitescreen.vip/")[/SIZE]

---

### Post by yancek on 2024-10-07
Why are you using 19.10 as it has had no support or updates for over 4 years?  The link below to the Ubuntu site shows that and also shows what Ubuntu releases are currently supported.  If you install a more current and supported version and have similar problems, post back with information on your graphics card.  You can get that information using any Linux installed or on a usb from a terminal with the command:   lspci | grep VGA

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by grahammechanical on 2024-10-07
How old or new is your machine? If we install a version of Ubuntu that is older than our hardware it may be that the hardware drivers in that version of Ubuntu may not work well or at all on that machine.

Regards

---

