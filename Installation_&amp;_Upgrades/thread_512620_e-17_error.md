---
title: "e-17 error?"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by godora102192 on 2007-07-29
ok i have e-17 in the SESSIONS when i am logging in but when i log in it gives me the following error.

Enlightenment error

you are executing enlightenment directly. this is bad. please do not execute the "enlightenment " binary. Use the "enlightenment_start" launcher. it will handle setting up environment variables, paths, and launching any other required services etc. Before enlightenment itself begins running.

what should i do?? 

i have this info also if it interests you

when i typed the """"gksudo gedit /usr/share/xsessions/e17.desktop""""" it gave the following output


/home/irakli/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:21: Unable to locate image file in pixmap_path: "Toolbar/toolbar-black.png"
/home/irakli/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:24: Background image options specified without filename
/home/irakli/.themes/aero-clone/gtk-2.0/gtkrc:187: Unable to locate image file in pixmap_path: "Arrows/arrow-up.png"
/home/irakli/.themes/aero-clone/gtk-2.0/gtkrc:191: Overlay image options specified without filename

and when i typed the """"""gksudo gedit /etc/environment"""""" it gave the following output!!

/home/irakli/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:21: Unable to locate image file in pixmap_path: "Toolbar/toolbar-black.png"
/home/irakli/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:24: Background image options specified without filename
/home/irakli/.themes/aero-clone/gtk-2.0/gtkrc:187: Unable to locate image file in pixmap_path: "Arrows/arrow-up.png"
/home/irakli/.themes/aero-clone/gtk-2.0/gtkrc:191: Overlay image options specified without filename
(gedit:5544): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

ohh and the PATH was the following-------- PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"-----



PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"

now i changed that path to the following because this dude from the e-17 installation page told me to do so.

now this path is  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/e17/bin"

i really want this guys. plz help me out

---

