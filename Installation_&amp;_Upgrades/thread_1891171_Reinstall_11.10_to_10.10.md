---
title: "Reinstall 11.10 to 10.10"
date: 2011-12-05
forum: Installation &amp; Upgrades
---

### Post by iRydel on 2011-12-05
Hi. I have a little problem. I have installed Windows 7 on my laptop and Ubuntu 11.10. I want to uninstall 11.10 and install 10.10, so i formated partisions of 11.10 and install there 10.10, but the grub menu doesn't show any list of operating systems when i start my computer. The grub show me "no such partitions" and grub's command line. I can't run any system. Please help!

---

### Post by ManualSparrow on 2011-12-05
Grab your live-cd, boot from it, open a terminal, and do ```
sudo grub-install /dev/sda
sudo update-grub
```

Assuming your hard drive is listed as sda and not hda, sdb, etc.

EDIT: Actually, take a look here: [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by iRydel on 2011-12-05
when i do your commands or when i do commands of this site, after
sudo grub-install /dev/sda
i have response
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
but i had all partissions mounted. ;/

---

### Post by iRydel on 2011-12-05
and all my partitons are mouting in /home/media not in /dev.

---

### Post by cbowman57 on 2011-12-05
Make it easy on yourself and keep a copy of [Rescatux]("http://www.supergrubdisk.org/rescatux/") around.

Unless of course your livelihood depends on knowing how to install grub from liveCD by memory. :)

---

