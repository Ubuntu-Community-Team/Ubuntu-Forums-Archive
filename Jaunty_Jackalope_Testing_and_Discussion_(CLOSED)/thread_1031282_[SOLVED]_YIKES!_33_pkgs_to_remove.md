---
title: "[SOLVED] YIKES! 33 pkgs to remove?"
date: 2009-01-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-01-05
This morning updates there were 23 updates, but it also wants to remove 33 pkgs. I think I shall wait this out unless I here different
```
dougie@DougiesLeanMachine:~$ sudo aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages will be REMOVED:
  arj{u} cheese{u} desktop-base{u} gdm-themes{u} gnome-core{u} gnome-games-extra-data{u} 
  gnome-network-admin{u} gnome-office{u} gnome-themes-extras{u} gnome-vfs-obexftp{u} gnome-volume-manager{u} 
  gnumeric{u} gnumeric-common{u} gparted{u} gthumb{u} gthumb-data{u} hardinfo{u} inkscape{u} 
  libmagick++10{u} libsoup2.2-8{u} libwmf-bin{u} liferea{u} menu-xdg{u} p7zip{u} perlmagick{u} planner{u} 
  python-4suite-doc{u} python-4suite-xml{u} python-lxml{u} python-reportlab{u} python-uniconvertor{u} 
  serpentine{u} sound-juicer{u} 
The following packages will be upgraded:
  acpi-support apport apport-gtk deskbar-applet gedit gedit-common ghostscript ghostscript-x libgs8 
  libgtksourceview-common libgtksourceview1.0-0 libgtksourceview2.0-0 libgtksourceview2.0-common 
  libgtksourceview2.0-dev python-apport python-problem-report python2.5 python2.5-dev python2.5-minimal 
  unattended-upgrades xterm xulrunner-1.9.1 xulrunner-1.9.1-gnome-support 
23 packages upgraded, 0 newly installed, 33 to remove and 0 not upgraded.
Need to get 21.7MB of archives. After unpacking 185MB will be freed.
Do you want to continue? [Y/n/?] n
```

---

### Post by autocrosser on 2009-01-05
I just checked & got the same out of sudo aptitude upgrade & sudo aptitude safe-upgrade. I've been using Update Manager & Synaptic--not getting that problem with them.....pulled all the updates without problem.

Aptitude will always "try" to remove things it "thinks" are not needed any more--I really like to be the last answer there......

---

### Post by ronacc on 2009-01-05
I updated this AM with update-manager and got the same updates installed with none of the removals .

---

### Post by chrisccoulson on 2009-01-05
This is completely expected whilst all the new upstream versions of Gnome packages are being pulled in. It will work itself out as more stuff gets updated.

---

### Post by ShirishAg75 on 2009-01-05
The only thing I found which is not being updated is the gecko-mediaplayer although I do remember to use aptitude autoclean after every few updates or so.

```
$ sudo aptitude autoclean
```

---

### Post by DougieFresh4U on 2009-01-05
I went and used update manager and it updated with out removing things.
I just like to use terminal as some times update manager can be 'funny' about doing partial upgrades and what not, but this goes to show that I can't always trust terminal. 
I kinda figured that things will sort out in a few days, just gotta be patient, but I love getting those updates!!:D
Thanks to all who replied.

---

### Post by ronacc on 2009-01-05
if you want to use the terminal use apt-get rather than aptitude .

---

### Post by Gina on 2009-01-05
I've just done an update using Update Manager.  I tried Synaptic at frist but got an error so clicked on the panel icon for UM and it all worked fine :)

---

### Post by DougieFresh4U on 2009-01-05
> **ronacc said:**
> if you want to use the terminal use apt-get rather than aptitude .

I see your point. I have always been under the impression that 'aptitude' was better, but I guess I shall go back to using 'apt-get'

---

