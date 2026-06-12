---
title: "[lucid] [upgrade] KDM logs me out after 2 seconds"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by GDR! on 2010-05-05
After an upgrade from Kubuntu 9.10 to 10.04 I'm not able to log in to my computer.

KDE seems to book OK, but when KDM displays login screen, I enter my login and password, and after 2-3 seconds the screen goes blank for a short moment and I'm back at login screen.

KDM log:
[http://gdr.pastebin.pl/23049](http://gdr.pastebin.pl/23049)

/var/log/messages doesn't print anything interesting.

I tried: reinstalling nvidia drivers, various combinations of dpkg-reconfigure suggested in the forums, installing kdebase and kubuntu-desktop. Nothing helped.

---

### Post by FrankTank on 2010-05-11
Have a look at your ~/.xsession-errors file

Mine pointed to problems with the /usr/lib/LibGL.so.0 symbolic link. After removing it I am able to use startx to start a KDE session, but I still cannot login via KDM..

---

### Post by GDR! on 2010-05-12
I have just solved it and here is the solution:

[LIST][*]Rebooted in safe mode
[*]apt-get purge nvidia-*
[*]Downloaded NVIDIA-Linux-x86_64-195.36.24-pkg2.run
[*]Executed: sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run
[*]Changed runlevel to 3 according to the command suggested by nVidia installer
[*]Logged in and executed sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run
[*]Answer OK to a series of errors, starting with the one saying about symlink
[*]Reboot (in normal mode)
[/LIST]

The downside of this is that all my settings (twinview, font sizes etc) are now gone.

---

