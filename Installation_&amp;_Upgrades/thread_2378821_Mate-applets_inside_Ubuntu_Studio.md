---
title: "Mate-applets inside Ubuntu Studio"
date: 2017-11-27
forum: Installation &amp; Upgrades
---

### Post by 01gk10 on 2017-11-27
Hi, folks! :popcorn:

I hope you all are fine.

Ok, I know that Ubuntu Studio already comes with Xfce-applets and they are very useful, but does anyone know how to install all applets from mate-applets into Ubuntu Studio without installing mate-desktop?

Thanks in advance!

---

### Post by ajgreeny on 2017-11-28
It looks as if you will have to install mate-panel plus its dependencies, and there are quite a few of those, though not the whole mate-desktop as far as I can see.

I run Xubuntu 16.04 and if I ask to install mate-applets it would add 30 packages with a download of about 30MB which when installed would use over 90MB; your choice, but you will need to add a mate panel to your desktop to use the applets as they can not be added to the xfce4-panel.

The list of packages I would have to add is
```
gir1.2-gtk-2.0	
mate-polkit-common 
mate-system-monitor		
libmate-desktop-2-17		
libgtksourceview2.0-0		
mate-system-monitor-common		
gir1.2-mate-panel		
mate-panel		
mate-desktop-common		
mate-polkit		
mate-media-common		
menu-xdg		
libcanberra-gtk-module		
mate-applets-common		
mate-media		
libgtksourceview2.0-common		
mate-desktop		
libmatemixer0		
libmate-menu2		
libmateweather-common		
libmateweather1		
cpufrequtils		
mate-menus		
libmate-panel-applet-4-1		
mate-user-guide		
libmatemixer-common		
mate-panel-common		
libcanberra-gtk0		
libcpufreq0		
mate-applets		

```
You would probably need a similar addition of packages as Ubuntu-Studio also uses the xfce4 desktop.

---

### Post by 01gk10 on 2017-11-29
Hi [COLOR=#000000]ajgreeny

Sorry for the late response.

Well, I made some searches and found a plugin called as [/COLOR][Xfce4-]("https://launchpad.net/xfce4-xfapplet-plugin")[xfapplet]("https://launchpad.net/xfce4-xfapplet-plugin")[-plugin]("https://launchpad.net/xfce4-xfapplet-plugin"), which enables to insert gnome-applets inside Xfce-panels. So, I'm wondering if, once I install this plugin, all mate-panel packages will not be required anymore for me to use its applets on Xfce. What do you think about it?

Please, let me know what you think about it or even whether it's gonna work or not.


Again, thanks in advance.

---

### Post by ajgreeny on 2017-11-30
I haven't the faintest idea if that will work or not, but I note that it is a source package only, and for Debian, not Ubuntu, so there is definitely a risk that it might not work.

All I can suggest is that you try it; you will need to download the source and then build it from that.

Good luck; tell us how it goes if you decide to try.

---

