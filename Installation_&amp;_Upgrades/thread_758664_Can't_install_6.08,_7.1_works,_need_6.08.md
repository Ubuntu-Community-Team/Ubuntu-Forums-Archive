---
title: "Can't install 6.08, 7.1 works, need 6.08"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by questor on 2008-04-18
I had no trouble installing 7.1 (IBM NetVista Pentium 4), but the recommended install for machine control software I want to run (EMC2) is a live CD using 6.08.  Trying to install the latter gives me the dreaded "No video bios modes for chosen depth" error, and can't run X11.  I think I have identified the problem. Under 7.1, video settings show the monitor running 1280 x1024 @ 60 Hz. When I scroll through the failed installation log for 6.08, I see a setting for 1280 x 1024 @75 Hz, but not 60 Hz.  I'm new at this, and have no idea how to modify settings for the live CD installation.  Is it possible to move the X11 config file from 7.1 to 6.08? Can I modify the live CD installation to include additional monitor settings, or is there a simple way to modify it during installation?

Thanks for all replies.

---

### Post by dstew on 2008-04-18
> "No video bios modes for chosen depth"You don't need to install again. You can reconfigure the xserver from the command line (boot into recovery mode) using the command```
sudo dpkg-reconfigure xserver-xorg
```That takes you through the configuration steps you did during the installation, with some added options. It re-creates the /etc/X11/xorg.conf file for you. I think there is an option for the refresh rate, and you can put the upper limit at 60 Hz. See if that helps. If you booted in recovery mode, start the xserver with ```
startx
```If it doesn't work, you can try lower resolution.

To reconfigure the xserver without re-booting, press ctrl-alt-F1 to get a command line, and use the same command. After you are done reconfiguring, press ctrl-alt-backspace to restart the xserver.

---

### Post by questor on 2008-04-18
Thanks!  The error occurs while booting from the live CD, so nothing is actually written to the HD.  Does your fix apply in this situation?

---

### Post by dstew on 2008-04-18
No, in that case you have to use kernel parameters. Press F6 at the opening menu, and add the parameter **vesa=force** to the kernel line, then boot. Hopefully that will get you a Live CD desktop. Or, after F6, try booting in Save Graphics Mode.

---

