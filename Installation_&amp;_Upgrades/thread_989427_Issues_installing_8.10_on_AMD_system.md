---
title: "Issues installing 8.10 on AMD system"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by Dozam on 2008-11-21
Ok, I've tried twice to get Ubuntu installed on my AMD system that is just over 4 years old. I'm able to get through the installation process, as far as I can tell, but when the system is restarted the GUI does not come up(I've tried having it sign me in automatically), all I get is some sort of command prompt that will not let me do much of anything. 
     Any suggestions that can be given would be great...I'm new to Linux and Ubuntu so please bear with me.

---

### Post by taurus on 2008-11-21
Try these from the prompt.

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

