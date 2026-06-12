---
title: "Iconia Tab W500"
date: 2013-06-02
forum: Installation &amp; Upgrades
---

### Post by Vl4dim1r on 2013-06-02
Hi Ubuntu Community, this is my first post with this username. Had to make a new one; its been years since my last login and I have no idea what my old username is. Anyways, I am attempting to install Ubuntu 13.04 on my Acer Iconia Tab W500. I've seen some threads about getting Ubuntu to work on the W500, but they were all from a couple years ago and don't seem to be valid on 13.04. I decided to go with Ubuntu over the Win7 install because of my familiarity with Ubuntu, all of my servers run Ubuntu server, and I just got tired of using Win7. 

Anyways, I have 13.04 already installed, but there are a few issues as I expected. 

Touchscreen - It works, kinda. I can select things, but I can't click anything? All the windows/buttons/etc react like my "mouse pointer" aka finger is over it, but I just can't tap. Also there is no right click.

Auto-Rotate - I havn't read anything about anyone actually getting this to work.

Honestly everything else seems to be cooperating, but I'm sure I'll encounter more issues once I can really use this thing. I'm glad I got the keyboard dock with it. Thank you for your help and suggestions.

---

### Post by thejoecarroll on 2013-06-12
Have you had any luck getting the touchscreen to work better? I was considering installing Ubuntu on my Tab, but maybe now I shouldn't bother...

---

### Post by Vl4dim1r on 2013-07-14
Sorry to get back to you so late. No I havn't been able to get everything working. I'm considering going back to Win7 with it. It made a nice head unit in my car with the dash mount, and I havn't been able to get the same level of functionality yet.

---

### Post by efflandt on 2013-07-16
I have a W500P (Win7 Pro instead of Home). I have been running 64-bit Lubuntu and Ubuntu 12.04 from 32 GB SD on it (3 partitions total w/common /home). And I was able to use it without the keyboard once I enabled some **Universal Access** things like icon for on screen keyboard, etc. I was using an older Verizon mobile data dongle on it (which worked in Linux), but now have smart phone WiFi hotspot.

Tapping the screen has always worked for left mouse button. I usually use it with a keyboard and often with wireless mouse, so I have not used the panel alone much and have not looked into auto-rotate.

I still need Win7 on it for company software to program electronic valve controls in the field.

PS: If you enable it in Universal Access, if you hold right click (or hold a finger on touch screen), that should bring up a right click menu if there is one for whatever you are pointing at

---

### Post by biochemistrygmcs on 2013-10-27
I have good experiance of acer iconia with debian wheezy with xfce

1)
for touch function install drivers from home.**eeti**.com.tw/**driver**download.html&#8206;; it wil start logh-press=right-click
do tell me if you fail to install driver

2)
for easy to grab window title bar and window borders modify pixmap of your theme from /usr/share/themes folder using GIMP

3)
for login screen install xvkbd
write following in a file "light", and chmod +x
==========================
/usr/bin/xvkbd -display $DISPLAY&
=============================

edit /etc/lightdm/lightdm.conf   to add following line to given section

[SeatDefaults]
greeter-setup-script=/root/light


reboot


4)
to widen scrollbar make **.gtkrc-2.0 in home folder**

style "scrollbar"
{
    GtkScrollbar::slider-width = 30
}
class "Gtk*Scrollbar" style "scrollbar"

style "resize-grip"
{
    GtkWindow::resize-grip-height = 35
    GtkWindow::resize-grip-width = 35
}
class "GtkWindow*" style "resize-grip"

5)
install xtile; to tile and see keyboard while typing.
set "xtile -v" command as panel launcher, to quickly tile horizontal (and other ways you want)

---

