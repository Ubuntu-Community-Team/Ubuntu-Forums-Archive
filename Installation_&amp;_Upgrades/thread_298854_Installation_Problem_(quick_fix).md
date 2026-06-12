---
title: "Installation Problem (quick fix?)"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by Kinn on 2006-11-13
I am booting from an image of Kubuntu Edgy I burned onto a CD. When I go to start up Kubuntu it sucessfully boots into its live version. When I go to clikc install it seems that the installation window is too large for my screen. I've tried adjusting the monitor resolution and searched for a way to make the screen larger both in the OS itself and monitor but have come up with nothing. The window is stuck at the language chooser and I can'y even see the bottom of the scroll window and pushing "Enter" as recommended in the documentation is not working. Is there a way to bypass the live boot and just install? Or is there any other way to get past this problem? Thanks.

---

### Post by bulldog on 2006-11-13
You can try to push ALT and move the window with your left moude button pusht down.
Or right click the window and see if there's a resize option.

If this isn't working try in your terminal```
sudo dpkg-reconfigure -phigh  xserver-xorg
``` and see if this gives you an option to change this behavior.

If not,download the alternate cd which is a text based install and it uses less resources as the live cd so it should be a lot quicker.

---

