---
title: "Can't load ubuntu 10.10 desktop after installing"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by dino_mordelon on 2010-10-20
I'm having a hard time installing Ubuntu 10.10 (32bits). I load the CD and everything's ok throughout the installing procedure, but when the installation is over and it says it's gonna reboot it doesn't do it! 

The screen resembles a terminal with a message like "the computer is going to reboot NOW!" but it could stay like that for hours. The keyboard is locked so I can't reboot by commands, and if I press CTRL+ALT+DEL it just reprints the same message. Therefore I'm forced to turn off my computer manually. 

After that, the Ubuntu desktop doesn't load. The screen shows a terminal asking for my username and password to access the computer. No graphics at all.

So, if anyone has or had the same problem I would appreciate your help.

---

### Post by lemming465 on 2010-10-21
If it boots to terminal mode, try logging in, and running```

sudo aptitude update
sudo aptitude full-upgrade
```
This will work best with a wired ethernet network connection. That will hopefully patch some bugs, possibly including the one causing X not to start.  If the GUI still doesn't come up after patching and rebooting, attach a copy of your /var/log/Xorg.0.log file.

---

