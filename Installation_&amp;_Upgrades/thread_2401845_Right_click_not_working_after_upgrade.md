---
title: "Right click not working after upgrade"
date: 2018-09-23
forum: Installation &amp; Upgrades
---

### Post by Dy1anW on 2018-09-23
I just upgraded a desktop from 16.04 to 18.04.1, but for some reason the right mouse button does nothing. Just to be clear, this is a desktop with a physical mouse, and not a touchpad. I've tried the gnome-tweak method, and switching to virtual consoles (which seems to work for some), but right click still won't work. Any way to resolve this? Thanks.

---

### Post by Dy1anW on 2018-09-25
Just an update:

left click is misbehaving as well. When clicking inside a window I can't actually click on any of the buttons, sliders, etc. I can't even close/minimise the window using the buttons in the top corner of the window. For example in VLC I can't change the volume, press play/pause, etc. Sometimes I can't left click any of the icons in the dock bar. Another odd behaviour within a window is when, for example in gnome-tweaks, if I go to any selection on the left, I can't scroll up/down on the relevant page, but if I click anywhere in that window it'll select the section on the left that is at the same Y-coordinateas the mouse cursor. Additionally when I have a terminal window open, the mouse cursor remains in an 'I' shape even when the cursor is outside of the window. Lastly if I right click anywhere on the desktop, the right click menu might come up, but only after a long delay.

A lot of these problems appear to be sporadic as well.

These problems persist even after a fresh reinstall.

Edit:
Actually the problem sounds similar to this:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1730174](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1730174)
but I'm not using Wayland (definitely in X11), and uncommenting the recommended line from custom.conf did nothing.

---

