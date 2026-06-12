---
title: "black screen on initial boot"
date: 2021-09-03
forum: Installation &amp; Upgrades
---

### Post by bigbirdwpg on 2021-09-03
I been struggling with this bug for years.  My system consists of an Asus MB - Z370 a ii, with a RX580 GPU that connects to a Samsung QLED 55" tv using HDMI via a Marantz SR7005 AVR.  Booting using a USB install or DVD install always results a black screen.  The only recourse is to connect directly to the TV (HDMI).  After installation is complete, if I switch back to the AVR route, black screen.  If I reboot while connected via the AVR - black screen,  The only way to make it work is to install VNC server and then initiate a remote session from another PC.  Once a connection is made, the screen on my linux install turns on and all is well from that point on.  This happen with every version of Linux that I have tried, Redhat, Ubuntu, Mint, etc.  Any post Windows 95 install just works - screen wise.

I wish this could be fixed.  I'm sure I'm not the only person to run into this.

---

### Post by MAFoElffen on 2021-09-06
Are you using XServer or Wayland?

My best guess, is that when Your GPU is coming up, since it is not seeing the Samsung through the AVR (because the AVR is between), it is not seeing the EDID modes of the Display, so it is setting an invalid graphics mode. If you are using XServer, and while you are looking at the system through your VNC  connected session, and looked at your xorg.0.log file, I believe that is  what you are going to find and see.

Several ways to get around this...You could set the Resolution in Grub, in the Grub default file. That would boot the Kernel and set KMS at that Graphics mode and when the desktop comes up, it would take that mode as a helper...

Unfortunately, since the AVR is functionally a video switch, if the power settings of the system goes to a screen lock, when it wakes up from Sleep, it queries on it's own again, see's just the AVR, resulting in an invalid mode again...

The way to get around that in XServer is to setup a user configured Xorg.conf file to set the mode as the default and to have that mode, even without a connected device seen.

Does that make sense?

---

