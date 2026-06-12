---
title: "adding file from /usr/local/bin to unity launcher"
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by magnetpest2k7 on 2012-10-24
How can I add an executable file from /usr/local/bin path to unity launcher?. For instance, I am executing a software "orange-canvas" by typing its name in terminal. When I do this, the software gets executed and the unity launcher gets an icon. However, when I pin this icon to unity launcher and execute it from the launcher the program does not launch. The icon just blinks. It used to be easier in older versions of ubuntu to add custom launchers. Can some one tell me how to do in unity environment?

Thanks
Vineeth

---

### Post by kgriff on 2012-10-28
From terminal run:
gnome-desktop-item-edit --create-new ~/Desktop

This will open the Create Launcher dialog.  If I've done it correctly, there should be an image of this dialog below.
Create the launcher, which will be on your desktop.
Click and drag the launcher to the Unity Launcher.

I should note that this works with 12.04.  I can't say for certain about anything earlier.  I believe, however, that with 11.04 the launcher has to be moved from the desktop to .local/share/applications before it can be dragged to the Unity Launcher.

---

