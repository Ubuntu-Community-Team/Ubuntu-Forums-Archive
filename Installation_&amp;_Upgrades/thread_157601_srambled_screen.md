---
title: "srambled screen"
date: 2006-04-09
forum: Installation &amp; Upgrades
---

### Post by colincam on 2006-04-09
Installed 5.10 everything ran through OK. until final screen start up. 
Scrambled graphics like wall paper patern and there is no response or escape from this screen. So hit reset button runs through startup to the same wallpaper rubish. I am running XP with nvidia card.
  Any ideas.   Thank you.

---

### Post by oscar on 2006-04-09
It sounds like a problem with your xorg.conf. Setting it up to use nvidia's proprietary drivers might help.
When you get to the scrambled screen press Ctrl+Alt+F1, this should take you to a screen where you can login to a terminal.
When you have logged in go:
```
sudo apt-get install nvidia-glx
```
Enter your password to let it run as administrator.
Now to configure your xorg.conf to use the nvidia drivers go:
```
sudo  nvidia-xconfig
```
Your xorg should now use the nvidia driver instead of the free nv driver that is used by default.
Restart your computer and hope that it works.

---

