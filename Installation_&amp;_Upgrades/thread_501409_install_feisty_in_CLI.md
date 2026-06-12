---
title: "install feisty in CLI"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by summer of 69 on 2007-07-15
Hay,
I had to install feisty on a friend's pc but the installerr stops at the "install software"
After 3 attempts I ended the installation, started up in recovery mode and tried to install the essentials manually

"apt-get update && upgrade"
"apt-get install x-window-system-core gdm ubuntu-desktop"
Can someone give me other essential software I can install in the terminal, because I seem to miss a few (of course) I mean the commands in the terminal . :)

---

### Post by aysiu on 2007-07-15
You shouldn't need to install in recovery mode.

Boot into regular mode and try ```
sudo apt-get update
sudo apt-get install xorg ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

---

