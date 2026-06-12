---
title: "Can't login graphically to 18.04 LTS after upgrade"
date: 2019-03-03
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2019-03-03
I upgraded a server  from 16.04 LTS to 18.04 LTS> I had a number of problems with the upgrade but the server now seem to be working except:

I can't login in using the graphic logins. I have the list of users, but the screen is in very low resolution and none of the logins I've tried work. It simply returns me to that screen.

I can go to a tty session and login in normally I can also stty in and login.

dpkg --configure -a is clean

apt install -f is clean

apt upgrade reports no packages to upgrade.

I tried to reconfigure gdm3 no change.
I tried to remove .Xauthority from some users.
I tried to recongigure lightdm with no resolut.
I noticed there is no xorg.conf file in /etc/X11

All users seem to have 5 display options:

[LIST]
[*]Gnome on Xorg
[*]Gnome Classic
[*]Gnome Flashback (Compis)
[*]Gnome Flashback (Metacity)
[*]Ubuntu. 
[/LIST]
I've tried them all on some users but none of them work

---

### Post by rsteinmetz70112 on 2019-03-03
Progress:

Switching to lightdm I can now login but I've still got a problem with very low resolution both on login and on the desktop.

The Setting tool display doens't recognize the display and won't let me change the resolution.

A number of posts on similar problems mentio a file in the users .config file names monitor.xml

I don't have any in any users .config file

Many of these problems seem to be connected to NVIDIA chips. I am not using the nvidia driver I am using the open source Nouveau.

However running # Ubuntu-droivers devices returns not information.

---

### Post by rsteinmetz70112 on 2019-03-03
Solved.
Purging all Nvidia software from the system did it. I only hope nouveau is now good enough.

---

