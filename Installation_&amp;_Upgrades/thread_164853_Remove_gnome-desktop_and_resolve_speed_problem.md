---
title: "Remove gnome-desktop and resolve speed problem"
date: 2006-04-23
forum: Installation &amp; Upgrades
---

### Post by jan-banan on 2006-04-23
I upgraded to dapper some weeks ago, and from now on i can only start x as root, and when i do it's really really slow. What's to do about that?

And i also want to remove _everything_ connected to gnome-desktop and install xubuntu-desktop, is that possible without removing everything by hand or formating the drive? Because i want to keep my files. 

PS. The speed problem is not connected to gnome, it ran just fine before i upgraded, so it isn't gnomes fault. ds.

---

### Post by Ensnared on 2006-04-23
[This post](http://ubuntuforums.org/showpost.php?p=662949&postcount=25) from [this thread](http://ubuntuforums.org/showthread.php?t=96048) might help. I used this to remove ubuntu-desktop while keeping kubuntu-desktop before, and it worked like a charm. All it does is compare the list of packages from the selected desktop and remove the ones belonging to the one you wish to remove except if they are required for the one you wish to keep.

---

### Post by jan-banan on 2006-04-23
Yeah! It seems grate, i'll try it out asap.
Thank you.

---

### Post by scooper on 2006-04-23
I'm not expert here, but some things to look at...

Did it upgrade udev?  If so, it may have changed permissions or even the presence of some /dev devices.  Use "ls -l /dev/input*" and "ls -s /dev/nv*" (assuming your video is nvidia).  Check the perms and the group.  Are you able to read and write those devices?  I.e. does the group have "w" permission and are you in the group?  Fixing the permissions is likely covered in other threads.  Look for udev and or pam.

The way I personally go about wiping something major is to pick a low level library to remove and watch what the dependencies take out.  E.g., I tried this.

$ sudo apt-get remove libgnomeui-common

Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  alacarte bug-buddy contact-lookup-applet dasher deskbar-applet ekiga eog evince evolution evolution-exchange
  evolution-plugins evolution-webcal file-roller firefox-gnome-support gcalctool gconf-editor gdesklets gdesklets-data
  gedit gnome-about gnome-app-install gnome-applets gnome-btdownload gnome-control-center gnome-cups-manager
  gnome-games gnome-keyring-manager gnome-media gnome-netstatus-applet gnome-panel gnome-pilot gnome-pilot-conduits
  gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-utils gnome-volume-manager gok gthumb gtkhtml3.8 gucharmap hal-device-manager hwdb-client
  libeel2-2 libgail-gnome-module libgdl-1-0 libgdl-1-common libgnome-desktop-2 libgnome2-perl libgnomecupsui1.0-1c2a
  libgnomeui-0 libgnomeui-common libgtkhtml3.8-15 libgucharmap4 libpanel-applet2-0 nautilus nautilus-cd-burner
  nautilus-sendto python-gnome2 python-gnome2-desktop python-gnome2-extras python2.4-gnome2 python2.4-gnome2-desktop
  python2.4-gnome2-extras rhythmbox serpentine sound-juicer totem totem-gstreamer tsclient update-notifier vino yelp
0 upgraded, 0 newly installed, 77 to remove and 108 not upgraded.
Need to get 0B of archives.
After unpacking 217MB disk space will be freed.
Do you want to continue [Y/n]?

The list looks pretty good for removing gnome-desktop, but I don't know that I picked the best core library, to get everything in Gnome and nothing more.  Please do it carefully, if you try, and scan the list thoroughly before saying "y".

Xubuntu may be more complicated, since it's a blend of stuff.  If you really want to be aggressive you can start with GTK, e.g. "sudo apt-get remove libgtk2.0-common".  Again, look at the list extremely carefully before proceeding.  It should eliminate all or most of xubuntu-desktop, hopefully not too much.

Good luck,
Steve

---

### Post by jan-banan on 2006-04-24
i'm in linux now, i discovered that i can use firefox though in a fail safe terminal. I have updated my udev to the latest version, and i tried the code scooper gave me and although i dont know what it said, it only said root in every column, wich inevitably must mean that i can only use my devs as root, right? So how do i change that? And will it solve my speedproblem to begin with?

---

### Post by jan-banan on 2006-04-25
*bump* 
Anyone?

---

