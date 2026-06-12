---
title: "No Desktop After Upgrade"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by dadamia on 2013-04-28
After upgrading my lubuntu installation to 13.04 I no longer get a desktop.  LXDM comes up and lets me enter my user name and password.  The screen then goes blank, except for the LXDM background image.  The desktop never comes up.  I can still switch over to a virtual terminal (Ctrl-Alt-F1).  I don't see any error messages in ~/.xsession-errors or in /var/log/Xorg.  Any ideas?

---

### Post by cellphonebarbie on 2013-04-29
> **dadamia said:**
> After upgrading my lubuntu installation to 13.04 I no longer get a desktop.  LXDM comes up and lets me enter my user name and password.  The screen then goes blank, except for the LXDM background image.  The desktop never comes up.  I can still switch over to a virtual terminal (Ctrl-Alt-F1).  I don't see any error messages in ~/.xsession-errors or in /var/log/Xorg.  Any ideas?

I have a similar problem. Not to hijack your thread, but I upgraded to 12.10 and lost my desktop. I'm able to use a mouse and right click to create a new folder which I then used to access settings. I was hoping it was a display issue as my desktop and font appear stretched. I was able to get to firefox by using the open with feature on the new "folder" on my desktop, but so far that hasn't been a terrific workaround. Please let me know if you find out the issue or what I can do! I'll be happy to continue researching and update you if I find anything. I'm a simple user with little to no computer literacy. I strictly run Ubuntu because I was angry at Windows and stumbled upon the Ubuntu os by accident.

Thank you!

---

### Post by dadamia on 2013-05-02
I don't know why, but the problem went away after I changed display managers from lxdm to lightdm.  To change your display manager, edit /etc/X11/default-display-manager.  It's just a one line file.  Mine looks like this:

dadamia@jannaa-M520:/etc/X11$ cat default-display-manager
/usr/sbin/lightdm

Each display manager has its own configuration file.  (See the man page.)  The one for lightdm is /etc/lightdm/lightdm.conf.  Mine looks like this:

dadamia@jannaa-M520:/etc/lightdm$ cat lightdm.conf

[SeatDefaults]
user-session=Lubuntu
greeter-session=lightdm-gtk-greeter

---

### Post by echo6 on 2013-05-06
Is this issue related to this thread [http://ubuntuforums.org/showthread.php?t=2141007](http://ubuntuforums.org/showthread.php?t=2141007)

---

### Post by dadamia on 2013-05-06
The "Solved" message that I posted a few days ago did work on one of my computers, but not on another.  Both computers run Lubuntu.  But, lightdm does not work on the second computer.  However, gdm does work.  I cannot explain the difference.  If you are having a problem like this I suggest you try a different display manager.  Maybe one will work for you.

I should note that neither of these computers had Lubuntu as an origianl installation.  One was originally Ubuntu and the other Xubuntu.  The lubuntu-desktop package was added later to make them Lubuntu machines.  Maybe that that had something to do with the problems that I had.

---

### Post by emaxwell14 on 2014-02-19
I found this on an LXDE forum and it solved my problem:

> [COLOR=#333333][FONT=Lucida Grande]I remove "lxpanel" , "lxsession" and "openbox" folder from "./config" folder. and log out. Then log in with default session and everythings works. [/FONT][/COLOR][IMG]http://forum.lxde.org/images/smilies/icon_e_smile.gif[/IMG][COLOR=#333333][FONT=Lucida Grande] [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Thanks to lubuntu users mailing lis[/FONT][/COLOR]

I am now using LightDM and selecting Lubuntu from the login screen. Previously this option would not work.

---

