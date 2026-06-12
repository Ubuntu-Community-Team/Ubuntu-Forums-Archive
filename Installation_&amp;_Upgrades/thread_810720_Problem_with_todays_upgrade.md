---
title: "Problem with todays upgrade"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by ancientrustic on 2008-05-28
Todays upgrade froze at 49%. I eventually had to kill Adept and had to go to the Konsol to kill the process. This completed the update but left me with the *-16 kernel rather than *-17. The latter shows up as installed in Adept but is not in menu.lst. How can I connect to the latest kernel? I am using KDE4.

---

### Post by dstew on 2008-05-28
You can try ```
sudo update-grub
```to update the menu.lst file.

---

### Post by ancientrustic on 2008-05-29
Thanks for that dstew. Grub appears to update but when I check menu.lst the *-17 kernel is not there. Is it possible uninstall the *-17 kernel and then reinstall?

---

### Post by zvacet on 2008-05-29
How many kernels do you have installed?Look in Adept for linux-image package and you can delete them all exept 2.6.24-16.I don´t work with Adept but I believe that you can there mark package for reinstall.Do that with 2.6.24.-17 kernel.

---

### Post by ancientrustic on 2008-05-29
Thanks again. I managed to uninstall and then updated again. this worked and I now have the *24-17 kernel but my wi-fi now fails to connect. There seems to be other people with this problem but following the advice doesn't work for me. I've fallen back to the 24-16 kernel which works fine.

---

