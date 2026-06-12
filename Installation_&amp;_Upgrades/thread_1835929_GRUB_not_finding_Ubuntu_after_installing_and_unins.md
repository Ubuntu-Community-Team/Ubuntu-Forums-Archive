---
title: "GRUB not finding Ubuntu after installing and uninstalling Fedora"
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by LFA2711 on 2011-08-30
I recently installed Fedora 15 in some empty space alongside my Ubuntu partition. I then tried to boot up, and the only entry in the GRUB menu was Fedora 15. I then booted GParted and deleted Fedora in an attempt to remedy this. However now when I boot up GRUB doesn't show any boot options; it just shows a terminal. I know that my Ubuntu partition is still there (checked with Ubuntu Live CD, GParted), however GRUB doesn't seem to recognize it. Are there any solutions to this? Should I just copy my files to another location and do a fresh install?

Thanks for the help.

---

### Post by nothingspecial on 2011-08-30
You can try booting a live cd and repairing ubuntu's grub

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by LFA2711 on 2011-08-30
Thanks for the help; it worked perfectly.

---

### Post by nothingspecial on 2011-08-30
No problem :)

ps You might want to mark this thread solved.

---

