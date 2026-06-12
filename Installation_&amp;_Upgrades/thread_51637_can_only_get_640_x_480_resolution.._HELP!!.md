---
title: "can only get 640 x 480 resolution.. HELP!!"
date: 2005-07-24
forum: Installation &amp; Upgrades
---

### Post by klutzini on 2005-07-24
Hi all,

I am using a HP laptop with a broken screen so I am using a HP pavillion MX70 monitor.

I installed Hoary which replaced Fedora Core 3.

when I installed it asked me which settings to use and I ticked: 1024x768 & 800x600, but I can only get 640x480 which is virtually un-useable!!

My chipset is Intel 82830 CGC shared graphics.

Can anyone help?

---

### Post by chazm on 2005-07-25
[QUOTE=klutzini]Hi all,

I am using a HP laptop with a broken screen so I am using a HP pavillion MX70 monitor.

I installed Hoary which replaced Fedora Core 3.

when I installed it asked me which settings to use and I ticked: 1024x768 & 800x600, but I can only get 640x480 which is virtually un-useable!!

My chipset is Intel 82830 CGC shared graphics.

Can anyone help?[/QUOTE]
 I had experience with that. Using Dimension 2350 w/ Intel 845G.

To fix, open a terminal and type: sudo gedit /etc/X11/xorg.conf

Scroll down to where it says "Monitor" and add these lines:

HorizSync        31.5-48.5
VertRefresh     59.0-75.0

Those are the settings that work on mine :)

---

### Post by daigorobr on 2005-07-25
[QUOTE=klutzini]Hi all,

I am using a HP laptop with a broken screen so I am using a HP pavillion MX70 monitor.

I installed Hoary which replaced Fedora Core 3.

when I installed it asked me which settings to use and I ticked: 1024x768 & 800x600, but I can only get 640x480 which is virtually un-useable!!

My chipset is Intel 82830 CGC shared graphics.

Can anyone help?[/QUOTE]
 I suggest going to console mode (Ctrl+Alt+F1) and "sudo dpkg-reconfigure xserver-xorg".
After that, go back to your WM (Ctrl+Alt+F7) and reinitialize it (Ctrl+Alt+BackSpace).

---

### Post by chazm on 2005-07-25
[QUOTE=daigorobr]I suggest going to console mode (Ctrl+Alt+F1) and "sudo dpkg-reconfigure xserver-xorg".
After that, go back to your WM (Ctrl+Alt+F7) and reinitialize it (Ctrl+Alt+BackSpace).[/QUOTE]

I'll write that down and try it sometime :)

---

### Post by klutzini on 2005-07-25
You guys are genius's!!!!

It worked..

Thankyou

---

### Post by jones_jj on 2005-07-25
[QUOTE=daigorobr]I suggest going to console mode (Ctrl+Alt+F1) and "sudo dpkg-reconfigure xserver-xorg".
After that, go back to your WM (Ctrl+Alt+F7) and reinitialize it (Ctrl+Alt+BackSpace).[/QUOTE]


I have tried the above suggestion and I can not seem to get Ubuntu to go to anything but a 640x480 resolution.  I have even tried to do a simple detect a medium detect and even a advance detect.  And when I go to screen resolution preferences it only gives me 640x480.

My chipset is Intel 82845G/GL

Thanks

---

### Post by chazm on 2005-07-25
[QUOTE=jones_jj]I have tried the above suggestion and I can not seem to get Ubuntu to go to anything but a 640x480 resolution.  I have even tried to do a simple detect a medium detect and even a advance detect.  And when I go to screen resolution preferences it only gives me 640x480.

My chipset is Intel 82845G/GL

Thanks[/QUOTE]

Try my steps in the second post. Works for me and I'm on 845G chip also :)

---

