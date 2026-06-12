---
title: "Black screen"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by cha0s_unity on 2008-10-22
I have an older computer (pent4 2.0ghz 256 ram) hooked up to my tv (CRT) via svideo. I'm trying to install xubuntu on the computer to use it to play movies and music.  When I power on the machine with the disc in the drive I can see the initial screen with the "try without changing" and "install" screen. After I select one, and I have tried both, I see the xubuntu loading screen. After that screen everything goes black. I see nothing.  If I run xubuntu off the cd and let it finish loading I can ctrl+alt+f1 to get to a shell and I can see that. From the shell I install vnc and connected to the computer from my laptop. On my laptop I could see the desktop. I don't understand that problem. I've tried installing puppy linux and if I use the xorg display I have the same problem but if I use xvesa the desktop loads as normal. Does xubuntu have a way to bring up the display or is there a way to install vesa?

thanks

---

### Post by didac on 2008-10-23
Look at /var/log/Xorg.0.log It will give you some messages.

To load vesa edit your /etc/X11/xorg.conf and add:

    Driver      "vesa"

 after the line:

Identifier	"Configured Video Device"

---

### Post by cha0s_unity on 2008-10-25
I tried switching over to vesa and I still get a black screen. I've also adjusted the resolution and there is still nothing. Does anyone have any ideas why?

---

### Post by didac on 2008-10-27
What does your /var/log/Xorg.0.log say? any hint about the problem?

---

### Post by cha0s_unity on 2008-10-27
I have fixed the problem of the black screen. Apparently I had forgotten to check the drivers and set them right. I had to take the same steps to switch to nvidia drivers that is normally required to run compiz. Now I'm just trying to get tightvnc server to display something besides a gray screen.

---

