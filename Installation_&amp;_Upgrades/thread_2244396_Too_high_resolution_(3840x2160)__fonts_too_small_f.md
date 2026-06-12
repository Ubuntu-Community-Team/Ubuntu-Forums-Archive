---
title: "Too high resolution (3840x2160) / fonts too small for terminal"
date: 2014-09-16
forum: Installation &amp; Upgrades
---

### Post by wonghang on 2014-09-16
Hi there,

I got a new laptop computer and running a Intel HD graphics card that could support the screen up to 3840x2160, but it is just too high and make the font too small for the terminal (for terminal I mean tty1,tty2, not gnome-terminal in xserver).
How can I change it to a lower resolution? I just want to stuck to 1920x1080.

I know I can change the screen by using:
1. Config -> Display or "xrandr" command in xserver
2. /etc/default/grub -> Edit "GRUB_GFXMODE=1024x768" / "GRUB_GFXPAYLOAD_LINUX=keep"
3. /etc/lightdm.conf -> Edit "display-setup-script=xrandr ...."

By following (2) I can make it to keep the screen at 1024x768 during boot, but _**at some point**_, the kernel try to load "font" and then the screen switch back to 3840x2160.
Lightdm just force to change it back to 1920x1080 using my configuration (3). If I press "Alt+Ctrl+1" to switch back to the terminal, the screen keep in 3840x2160 which too high and the font is too small for me.

How can I solve it?

I am running Ubuntu Desktop 14.04 LTS, kernel version 3.13-0-35-generic x86_64
display card is Intel Integrated Graphics and have a nvidia card support Nvidia Optimus.

P.S. I have already tried "nomodeset" and "xvga=1024x768" in kernel command line. The first one will make xserver fail, the second one was just the same.
It would be best if I can keep the screen in 1920x1080 starting from grub so that the machine does not need to change resolution every time.

---

### Post by wonghang on 2014-09-19
I solved it by adding the following in kernel command line:  

> video=eDP-1:1920x1080

---

