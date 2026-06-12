---
title: "Corrupted login splash after update 9.04-&gt;9.10"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by g003y on 2010-04-04
I just ran an update of ubuntu 9.04 to 9.10 and now the "startup" splash and the login splash is gone. Instead I see the terminal during bootup and the login prompt is some strange sparse login screen looking like it was taken from some old CDE GUI. What has happened and how do I fix it?

I can also add that while upgrading I chose to let the menu.lst remain untouched which turned out to be a bad mistake. So I added the following lines manually to compensate for my mistake.

title        Ubuntu 9.10, kernel 2.6.31.20-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=<same as old>  ro quiet splash
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

But that didn't resolve my problems. I also tried the following without success:

[COLOR=blue]$ export display=:0.0
[/COLOR][COLOR=blue]$ sudo -u gdm gnome-control-center[/COLOR]

after loging myself out and pressning ALT+F1/ALT+F7...

---

### Post by quadproc on 2010-04-04
> **g003y said:**
> I just ran an update of ubuntu 9.04 to 9.10 and now the "startup" splash and the login splash is gone. Instead I see the terminal during bootup and the login prompt is some strange sparse login screen looking like it was taken from some old CDE GUI. What has happened and how do I fix it?
It sounds like your X server is not running.  You might try looking in /var/log/Xorg.0.log for anything related to errors.  From the command line you could try startx or sudo startx, as appropriate to see if you can get X to run.

Whn I did the 9.04 -> 9.10 upgrade, I ended up with an unhappy X windows; it was running, but only in low graphics mode.  After a while I suspected driver problems so I uninstalled fglrx and then reinstalled it.  This fixed the problems for me.  In retrospect, I should have uninstalled the driver before doing the system upgrade, and then reinstalled it after the upgrade was done.

quadproc

---

### Post by g003y on 2010-04-04
But the desktop is the same as before except that the "wallpaper" is gone. I have full "3D effects" on the windows and everything. I checked the log you suggested but I see no indication that the xserver failed to start. The only error message I see is "Failed to load module "freetype" (module does not exist, 0)".

I also checked the menu item System -> Administration -> Login screen, but when I choose it, it shows a simplistic window that only allows me to choose user at login. It is not as fancy as the following URL:

[http://www.simplehelp.net/2009/05/21/how-to-change-the-ubuntu-login-screen/](http://www.simplehelp.net/2009/05/21/how-to-change-the-ubuntu-login-screen/)

Here's what I have done, I downgraded gdm 2.28 to 2.20. I followed these instructions:

[http://ubuntuforums.org/showthread.php?t=1323087](http://ubuntuforums.org/showthread.php?t=1323087)

and when I did that, the login screen came back. There is no doubt that somethings corrupt about the new gdm installation. I lost my wallpaper and login. I'm not sure yet if this has fixed the startup splash.

---

