---
title: "Upgrade killed my comp HELP!"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by slugkilla on 2007-05-04
I just upgraded from edgy to fiesty and my comp won't take me to the log in screen. Normally I could just run envy to get X started, but I can't log in to do so. If I wait awhile this "BusyBox" thing comes up. I don't know how to get into the system from there. Please help me figure this out. Thanks

---

### Post by Naegling23 on 2007-05-04
this might be of some help

[http://ubuntuforums.org/showthread.php?t=415479](http://ubuntuforums.org/showthread.php?t=415479)

---

### Post by slugkilla on 2007-05-04
Thanks, I'm downloding the new cd now. The edgy cd started to load the live thing but it hung. Hopefullly the new one will work. I'll let you know how it goes

---

### Post by slugkilla on 2007-05-04
Ok so far I've chrooted into my system through the live cd and done a "sudo apt-get -f install". It listed a bunch of programs and then said that there are too many errors to do anything else. What a usefull command! Thanks for all the help. I'm close now. What should I do?

---

### Post by slugkilla on 2007-05-04
:confused: :confused: My system is still not functional. Is there another command that will fix these dependencies and configuration problems? Please help. Thanks

---

### Post by jerrylamos on 2007-05-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There could be a number of situations.  What are the last few lines on the screen?  Do you get a "can't access tty"?

Cheers, Jerry

---

### Post by slugkilla on 2007-05-04
Well last time i restarted i go a just an underscore and a black screen. No login prompt. I should be able to fix things from being chrooted in side of the system. I just don't know how to fix the errors. 

When runing "sudo apt-get -f install
> dpkg: too many errors, stopping
Errors were encountered while processing:
 dbus
 libgnomevfs2-0
 libgnome2-0
 libbonoboui2-0
 libgnomeui-0
 libgnome-desktop-2
 libgnomekbdui1
 libgucharmap6
 libpanel-applet2-0
 libgnome-menu2
 python-gmenu
 gnome-menus
 libcamel1.2-10
 libebook1.2-9
 libecal1.2-7
 libedataserverui1.2-8
 liblpint-bonobo0
 libnautilus-extension1
 libslab0
 libgnome-window-settings1
 gnome-control-center
 gnome-about
 gnome-panel
 gnome-applets
 yelp
 gnome-user-guide
 ubuntu-docs
 avahi-daemon
 compiz-gnome
 compiz
 python-gnome2
 libtotem-plparser1
 python-gnome2-desktop
 python-gnome2-extras
 deskbar-applet
 desktop-effects
 dhcdbd
 libedata-book1.2-2
 libedata-cal1.2-6
 evolution-data-server
 ekiga
 libexchange-storage1.2-3
 libgtkhtml3.14-19
 gtkhtml3.14
 evolution
 evolution-exchange
 libgnome2.0-cil
 f-spot
 firefox-gnome-support
 gnome-games
 gnome-keyring-manager
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# 



---

### Post by slugkilla on 2007-05-05
Any Idea yet? My comp is so messed up. Isn't there some way to get rid of these apps and put them back on after everything is all right?

---

### Post by slugkilla on 2007-05-05
Since I don't know how to save my system, I'm trying to burn everything on my hard drive to a cd. When I click "write to disc" a warning pops up saying that all my files are unreadable. Thats not cool. I think I have to run that program under sudo. How can I do this. Or is there an easyer way or even a new idea on how to save my system? thanks for help

---

