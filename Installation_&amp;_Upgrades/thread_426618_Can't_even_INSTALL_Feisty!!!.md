---
title: "Can't even INSTALL Feisty!!!"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by Mike Dolan on 2007-04-28
I just tried installing Ubuntu Feisty (the 386i desktop on AMD 64), and the install screen is locked at 800x600 (the only other size is smaller!). In this size on my Advueu 17 LCD, the Next buttons weren't even visible! And I couldn't scroll down to them! I've spent half an hour trying to get around this, but it's impossible. And clicking ENTER on the time zone screen only repeats the selection menu! How is anybody supposed to even TRY Feisty if installing it is impossible??

On the next distro, PLEASE allow the user to SCROLL up and down in the install screens!!!

---

### Post by taurus on 2007-04-28
What video card do you have on your AMD64?  Perhaps you need to add a higher resolution to /etc/X11/xorg.conf.  Boot into recovery mode from GRUB menu and type

```
nano -Bw /etc/X11/xorg.conf
```
Scroll down until you get near the end and add "1024x768" at the beginning for all the modes.  Save it and exit with <Ctrl>0 and <Ctrl>x.  Reboot and see if you get a higher resolution on your monitor.

```
shutdown -r now
```

---

### Post by Mike Dolan on 2007-04-29
You're assuming I've managed to install Feisty and can reboot to the GRUB recovery utility. I can't do any of that as long as it remains impossible for me to install Feisty under any conditions!

---

### Post by taurus on 2007-04-29
Then try to use the alternate CD to install it on your machine instead of the desktop CD/LiveCD.

---

