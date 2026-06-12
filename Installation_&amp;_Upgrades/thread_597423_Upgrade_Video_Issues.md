---
title: "Upgrade Video Issues"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by Brian2 on 2007-10-30
I just upgraded from Feisty to Gusty using the auto upgrade found in the the Ubuntu upgrade window. Now when I boot I see the Ubuntu logo and the loading bar and it loads like normal, but after that I see text. The text is basically the starting of various daemons and then my screen blinks about three times and then I have a text login. I can login in fine using the prompt but I want X11 back. I looked through xorg.conf for anything obvious but I didn't spot anything. I also tried replacing xorg.conf with the failsafe but I got the same result. I am attaching my original config file. Any help would be great, thanks.

---

### Post by perlluver on 2007-10-30
Did you try sudo dpkg-reconfigure xserver-xorg.  And set Nvidia to NV.

---

### Post by Brian2 on 2007-10-30
I ran sudo dpkg-reconfigure xserver-xorg and I went through the configuration. On the next boot I was asked about low graphics mode and I entered Ubuntu. Unfortunately I cannot move on from here. The restricted drivers unit says I am using Nvidia but under screens and graphics I am using the vesa driver. The screens and graphics unit cannot detect my monitor or my graphics card, instead it uses generic defaults. When I try to switch from these defaults(monitor or driver) I get a screen with a bunch of black and white dots, but the dialog window asking if this setting is OK is still visible and normal. Now I am really confused.

---

