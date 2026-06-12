---
title: "Minimum font size after update"
date: 2020-09-02
forum: Installation &amp; Upgrades
---

### Post by iki3 on 2020-09-02
Hi all.
After the last system update, every time I start it, it appears with the font size so small that it can hardly be read. I have tried to change it with gnome-tweaks but when restarting the minimum letter returns. The only quick way I have found to fix it every time and go back to the default system font is to enable Universal Access large font size and then disable it again and so it returns to normal font size, but I can't get Ubuntu to boot with the font size listed in the system settings.
Thanks for your help.

Edit:
It appears to be a bug in Mutter, which is the default window manager for Gnome Shell:
[https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1892440](https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1892440)

We will therefore wait for a solution from the developers

---

### Post by Randy_Bass on 2020-09-10
I have a similar problem using XFCE as my desktop environment, on my initial boot after updating. This is on update to Linux kernel 5.4.0-47. File Manager font is exceedingly small, and I have no way to change it. I've gone into Appearance and changed font size and monospace font size, but it doesn't affect File Manager. Window Title Font was also changed to smaller, but I was able to change that in Window Tweaks. It also changed the font size in Orage calendar widget, but I was able to modify that to something useful. I haven't rebooted yet to test if these changes are permanent.

---

