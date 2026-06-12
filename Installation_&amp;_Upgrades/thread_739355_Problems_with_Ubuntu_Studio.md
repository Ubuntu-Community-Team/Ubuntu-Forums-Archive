---
title: "Problems with Ubuntu Studio"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by dropscience on 2008-03-29
Hello a while ago i decided to give Ubuntu Studio a try, so i installed the audio, desktop and the audio-plugins packages using apt. Now every time when i try to log in i get a message that says: Failed to start the X server (your graphical interface). It is likely that it is not set up correctly, would you like to view the X server output to diagnose the problem. I am thinking of installing Ubuntu Studio from a CD, but would i have to part my hard drive again, or can that be avoided, because i don't want to remove anything. Can someone please help me?

---

### Post by logos34 on 2008-03-29
It must have changed your graphics config--can't imagine why it would do that if all you did is add the desktop and audio pkgs. Unless you also installed the linux-rt kernel and that is what you're booting (if so simply select the regular kernel on the grub menu screen).

Try restoring the xorg file (it should have saved it with '~' ending).  

At the console prompt:

sudo mv /etc/X11/xorg.conf~ /etc/X11/xorg.conf

reboot.

More info/options here:
[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy)
[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

---

