---
title: "Installing Intrepid on Fujitsu-Siemens Amilo Li1705"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by Maverickprowls on 2008-11-09
I am looking for assistance in getting a successful clean install on my Amilo Li 1705.  I  understand that there is a bug in the bios, but that this need not be an impediment to obtaining a working system.  Does anyone have any experience in getting as far as a log-in screen?

Having tried to install Intrepid on my Amilo Li1705 from the LiveCD with no success (screen locks up as soon as X starts), I will now try and document the process as I (hopefully) manage to get a working install on the machine, at which point I could hopefully turn this into a howto to help others.

First attempt:
Using Alternate install CD.  
When starting the install, the screen is split vertically into three, with the left and right sides transposed, and a patch of the right side duplicated and dumped twice on the screen.  Thus cannot read screen to install

Second attempt:
Using the additional options on the menu screen, added VGA=0x3b8 to the boot options.  All menus now display beautifully, and the install proceeds without a hitch until trying to start X, whereupon I get the same problem I saw with the Live CD. (See attachment) The system is entirely locked up and nothing on the screen is moving.  There does appear to be a hint of a text box just below the spinning cursor, but there's no mouse available.



If I discover how to get any further, I will naturally post the results here.  Many thanks in advance to anyone offering help.

---

### Post by Maverickprowls on 2008-11-09
Some small progress.

I have managed to get a working install of OpenSuSE 11 onto the machine alongside my Ubuntu install.  I had a look at the xorg.conf in SuSE to see if it can help me configure Ubuntu's X.  Being largely unexperienced with the nut and bolts of x, I simply copied across all the sections of the working xorg.conf.

Result:
Ubuntu tells me it is running in low graphics mode, and asks to restart the X server, but then cycles repeatedly through a lot of garbled graphics before returning me to the low-graphics warning.  Clearly some sort of window is at least being displayed, so I'll look more closely at the xorg.conf and see if I can cherry-pick the pieces I need.

Should anyone know more about configuring directly in the xorg.conf file, I would greatly appreciate the advice.

My xorg.conf (from SuSE) is included below (the one in Ubuntu appears to be entirely unconfigured, but this isn't surprising as I haven't yet made it to the login screen)

---

### Post by Maverickprowls on 2008-11-10
A little more progress.

First, as my system was locking up entirely when X started, I had to make sure that I could start my Ubuntu install without X.

To do this, I started my working SuSE install, mounted the Ubuntu partition, then found the file "default-display-manager" at > /etc/X11/default-display-manager using a text editor I then opened the file and changed the line > /usr/sbin/gdm to # > /usr/sbin/gdm

I was then able to boot my Ubuntu install and arrive at a command prompt.

Searches elsewhere on these forums had told me that the graphics card in the Fu-Si Amilo Li1705 is a Via Chrome 9, and that I should install the OpenChrome drivers using the line ```
sudo apt-get install xserver-xorg-video-openchrome
```this told me that the drivers were already installed.  It was then that I noticed a file called xorg.conf.new dumped in my / directory.  I had a look at it, and saw what appeared to be an xorg.conf set up to use the openchrome (called via in the file) drivers.  I copied this file to my /etc/X11 directory and overwrote the original xorg.conf.

I then started X with ```
startx
``` and after a few seconds I saw my gnome desktop!  Hoorah!  The display resolution is wrong, and the gnome display manager seems to think that my refresh rate is 0Hz, but at least I can see what I'm doing!

Notes:  When I log out of the gnome desktop, the display instantly becomes scrambled and I am not returned to the command prompt as I would expect.  I am beginning to suspect that the problem may lie with the GDM interface using an inappropriate resolution, and as such I'm going to try and reconfigure the gdm to use the standard 1280x800 or less of the screen on this machine.

I'm going to post the partially working xorg.config below.  If anyone can tell me how to get the correct resolution out of my monitor (1280x800), I should be very grateful, I've already tried adding line > Mode "1280x800"to the appropriate Subsection in my xorg.conf file, but the system just seems to ignore it.

---

