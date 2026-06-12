---
title: "dependency problem"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by tollboy on 2008-08-05
when i am trying to run ```
sudo apt-get upgrade
```
then there is a error in the last line saying like this ```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

this is the screen which lead to the above error.

```
panky@TiGER:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  virtualbox-ose-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
26 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up gnome-applets-data (2.22.2-0ubuntu2) ...
dpkg: error processing gnome-applets-data (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-panel-data (1:2.22.2-0ubuntu1.1) ...
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (>= 1:2.22); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-panel-data (<< 1:2.23); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-applets-data (>= 2.22); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-applets-data (<< 2.23); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-panel (>= 2.13.4); however:
  Package gnome-panel is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
Setting up cheese (2.22.3-0ubuntu1) ...
dpkg: error processing cheese (--configure):
 subprocess post-installation script returned error exit status 139
Setting up deskbar-applet (2.22.3-0ubuntu1) ...
dpkg: error processing deskbar-applet (--configure):
 subprocess post-installation script returned error exit status 139
Setting up eog (2.22.3-0ubuntu2) ...
dpkg: error processing eog (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evince (2.22.2-0ubuntu1) ...
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evolution-common (2.22.3.1-0ubuntu1) ...
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on evolution-common (= 2.22.3.1-0ubuntu1); however:
  Package evolution-common is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.22.3.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.22.3.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up f-spot (0.4.3.1-0ubuntu1) ...
dpkg: error processing f-spot (--configure):
 subprocess post-installation script returned error exit status 139
Setting up file-roller (2.22.3-0ubuntu1) ...
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gcalctool (5.22.3-0ubuntu0.1) ...
dpkg: error processing gcalctool (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gdm (2.20.7-0ubuntu1.1) ...
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gedit-common (2.22.3-0ubuntu1) ...
dpkg: error processing gedit-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on gedit-common (>= 2.22); however:
  Package gedit-common is not configured yet.
 gedit depends on gedit-common (<< 2.23); however:
  Package gedit-common is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-app-install (0.5.2.8-0ubuntu1) ...
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-games-data (1:2.22.3-0ubuntu2) ...
dpkg: error processing gnome-games-data (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-system-monitor (2.22.3-0ubuntu2) ...
dpkg: error processing gnome-system-monitor (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of libdeskbar-tracker:
 libdeskbar-tracker depends on deskbar-applet (>= 2.20.0); however:
  Package deskbar-applet is not configured yet.
dpkg: error processing libdeskbar-tracker (--configure):
 dependency problems - leaving unconfigured
Setting up rhythmbox (0.11.5-0ubuntu8) ...
dpkg: error processing rhythmbox (--configure):
 subprocess post-installation script returned error exit status 139
Setting up seahorse (2.22.2-0ubuntu1) ...
dpkg: error processing seahorse (--configure):
 subprocess post-installation script returned error exit status 139
Setting up tomboy (0.10.2-0ubuntu1) ...
dpkg: error processing tomboy (--configure):
 subprocess post-installation script returned error exit status 139
Setting up update-manager (1:0.87.27) ...
dpkg: error processing update-manager (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 gnome-applets-data
 gnome-panel-data
 gnome-panel
 gnome-applets
 cheese
 deskbar-applet
 eog
 evince
 evolution-common
 evolution
 evolution-exchange
 evolution-plugins
 f-spot
 file-roller
 gcalctool
 gdm
 gedit-common
 gedit
 gnome-app-install
 gnome-games-data
 gnome-system-monitor
 libdeskbar-tracker
 rhythmbox
 seahorse
 tomboy
 update-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

this problem starts after installing updates. which i had done after 79 days

if any bodu can help me how to solve this dependency problem

---

### Post by Qchan on 2008-08-05
[b][color=darkred]
Your answer lies here:

[http://ubuntuforums.org/showthread.php?t=21672](http://ubuntuforums.org/showthread.php?t=21672)

[/b][/color]

---

### Post by tollboy on 2008-08-05
i already gone through that thread 
bt didnt get solved it 
in my /var/crash there r four files 
i removed bt skype bt is it safe to remove gnome applets and gdm > panky@TiGER:/var/crash$ ls
gnome-applets-data.0.crash  gnome-panel-data.0.crash
gnome-panel.0.crash         skype.0.crash
panky@TiGER:/var/crash$ 



these r d four packages

---

