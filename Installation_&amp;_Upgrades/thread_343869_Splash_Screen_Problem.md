---
title: "Splash Screen Problem"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by hack2453 on 2007-01-22
After installing Ubuntu it found and installed 307 updates. After that little problem it only rand the previous install. When the the splash screen opened, it did so at 1600x1200 at 79 Hz. When Kubuntu was installed, I was able to change the display setting to 1152x864. Now when I boot up the splash screen is unreadable. My video card is the Asus EAX 1600 XT with 256 mgs of ram. Short of reinstalling, what can I do?

---

### Post by frodon on 2007-01-22
Could you paste your /boot/grub/menu.lst file here, type this to open it :
```
sudo gedit /boot/grub/menu.lst
```
In this file you can add a parameter to modify the resolution of the splash screen.

Just tell us what resolution you wish and we will tell you how to edit the file.

---

