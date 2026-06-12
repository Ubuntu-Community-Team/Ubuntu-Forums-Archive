---
title: "Install minimum X11 on Ubuntu Server?"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by danfluidmind on 2007-04-11
Hi all.

I just installed Ubuntu 6.06 Server to be the host OS for VMware Server. I'd like to run X11 with XFCE, but if I do "apt-get install xubuntu-desktop" it installs a massive amount of desktop apps (Abiword, OpenOffice, etc.) that I don't need. Could someone either enumerate or point me to a list of the minimum packages I'd need to install to just have as small an installation of X11 with XFCE as possible?

Thanks
--Dan

---

### Post by pxwpxw on 2007-04-11
Probably 
```

apt-get install xdm xfce4

```
or gdm instead of xdm .

I did a similar install, may need some more packages depending on what you want.
See xfce web site.
Some other threads cover this fairly well.

---

### Post by danfluidmind on 2007-04-11
> **pxwpxw said:**
> ```

apt-get install xdm xfce4
```

Thanks pxwpxw. xdm isn't there, but gdm is.

xfce4 isn't a package name in 6.06. And there doesn't seem to be just one package you can install to get just xfce without all the extra desktop apps that go with the xubuntu-desktop package.

--Dan

---

### Post by pxwpxw on 2007-04-11
**danfluidmind**

Yes, sorry about that, Just checked back and that was for a debian etch comandline install.
I  used xubuntu-desktop install on ubuntu610 server, i386 around 1.8GB.

Try here for more on xfce:
[http://www.xfce.org/](http://www.xfce.org/) 

For debian i had to install xorg, gdm (or xdm),  xfce4, and xfce4goodies.
Some are virtual packages. Finished up with around 1 GB disk used, applemacppc64.

I will try find a link to minimal desktop installs, and post here.

---

### Post by pxwpxw on 2007-04-12
There are some ubuntu threads about xfce and fluxbox if you search for those, there  is more in debian forums.

xfce4 is a metapackage for ubuntu610, maybe not in 606:

Very useful info here for packages:

[http://packages.ubuntu.com/edgy/x11/](http://packages.ubuntu.com/edgy/x11/)

xfce4 (4.3.90.2) [universe]
    meta-package for xfce4 dependencies

[http://packages.ubuntu.com/edgy/x11/xfce4](http://packages.ubuntu.com/edgy/x11/xfce4)
(lists packages)

For comparison, listed here the xfce4 packages in this ubuntu610server plus xubuntu-desktop:

```

$ aptitude search xfce

i   gtk2-engines-xfce               - A GTK+-2.0 theme engine for Xfce          
i   libxfce4mcs-client3             - Client library for Xfce4 configure interfa
p   libxfce4mcs-dev                 - Development files for libxfce4mcs-client a
i   libxfce4mcs-manager3            - Manager library for Xfce4 configure interf
p   libxfce4util-dev                - Development files for libxfce4util        
i   libxfce4util4                   - Utility functions library for Xfce4       
i   libxfcegui4-4                   - Basic GUI C functions for Xfce4           
p   libxfcegui4-dev                 - Development files for libxfcegui4-4       
p   python-xfce                     - Python bindings for Xfce                  
v   python2.4-xfce                  -                                           
p   xfce4                           - meta-package for xfce4 dependencies       
i   xfce4-appfinder                 - Application finder for the Xfce4 Desktop E
p   xfce4-artwork                   - additional artwork for the Xfce4 Desktop E
i   xfce4-battery-plugin            - battery monitor plugin for the Xfce4 panel
i   xfce4-clipman-plugin            - clipboard history plugin for the Xfce4 pan
p   xfce4-cpu-freq-plugin           - display the CPU informations in the Xfce p
i   xfce4-cpugraph-plugin           - CPU load graph plugin for the Xfce4 panel 
p   xfce4-dev-tools                 - Xfce4 development tools                   
p   xfce4-devel                     - The Xfce4 Desktop Environment -- developme
i   xfce4-dict-plugin               - Translation plugin for the Xfce panel     
p   xfce4-diskperf-plugin           - disk performance display plugin for the Xf
i   xfce4-fsguard-plugin            - filesystem monitor plugin for the Xfce4 pa
p   xfce4-genmon-plugin             - Generic Monitor for the Xfce4 panel       
p   xfce4-goodies                   - enhancements for the Xfce4 Desktop Environ
i   xfce4-icon-theme                - Xfce Standard icon theme                  
i   xfce4-mailwatch-plugin          - mail watcher plugin for the Xfce4 panel   
i   xfce4-mcs-manager               - Settings manager for Xfce4                
p   xfce4-mcs-manager-dev           - Development files and static plugins      
i   xfce4-mcs-plugins               - Special modules for the xfce4-mcs-manager 
p   xfce4-messenger-plugin          - Dbus messages plugin for xfce4-panel      
p   xfce4-minicmd-plugin            - Mini-command line plugin for the Xfce4 pan
i   xfce4-mixer                     - Xfce4 Mixer frontend                      
i   xfce4-mixer-alsa                - Xfce4 Mixer ALSA backend                  
i   xfce4-mount-plugin              - mount plugin for the Xfce4 panel          
i   xfce4-netload-plugin            - network load monitor plugin for the Xfce4 
i   xfce4-notes-plugin              - Notes plugin for the Xfce4 desktop        
i   xfce4-panel                     - The Xfce4 desktop environment panel       
p   xfce4-panel-dev                 - The Xfce4 panel development files         
i   xfce4-quicklauncher-plugin      - rapid launcher plugin for the Xfce4 panel 
p   xfce4-radio-plugin              - v4l radio control plugin for the Xfce4 pan
i   xfce4-screenshooter-plugin      - xfce4-panel plugin to take screenshots    
p   xfce4-sensors-plugin            - hardware sensors plugin for the Xfce4 pane
i   xfce4-session                   - Xfce4 Session Manager                     
i   xfce4-smartbookmark-plugin      - search the web via the Xfce4 panel        
i   xfce4-systemload-plugin         - system load monitor plugin for the Xfce4 p
i   xfce4-taskmanager               - process manager for the Xfce4 Desktop Envi
i   xfce4-terminal                  - Xfce terminal emulator                    
p   xfce4-theme-brushedchrome       - BrushedChrome theme for Xfwm4 and Gtk+ 2.0
p   xfce4-trigger-launcher          - Panel plugin to start/stop programs       
i   xfce4-utils                     - Various tools for Xfce                    
i   xfce4-verve-plugin              - Command line plugin for the Xfce panel    
p   xfce4-wavelan-plugin            - wavelan status plugin for the Xfce4 panel 
i   xfce4-weather-plugin            - weather information plugin for the Xfce4 p
p   xfce4-xfapplet-plugin           - Gnome applets plugin for Xfce panel       
i   xfce4-xkb-plugin                - xkb layout switch plugin for the Xfce4 pan
p   xfce4-xmms-plugin               - xmms plugin for the Xfce panel            

```

---

### Post by kerry_s on 2007-04-12
sudo apt-get install xorg gdm xfce4
or
sudo apt-get install xorg gdm fluxbox
or
sudo apt-get install xorg gdm icewm
or
sudo apt-get install xorg gdm gnome-core
or
sudo apt-get install xorg gdm kde-core

main thing is "sudo apt-get install xorg gdm" that is the X environment.

---

### Post by Titus A Duxass on 2007-04-12
Search the cache with "apt-cache search xcfe"

That should list every package with a name that contains the letters "xfce".

If it is not there you will have to add new repositories, but I'm sure it's there.

You may also need to add some more packages for a minimal install, I always go for "gdm, xterm, gnome-core" this gives me an recognizeable GUi without all the bloat.

---

### Post by danfluidmind on 2007-04-13
Thanks a lot guys. I'll give that a try.

The "xfce4" package is indeed in "universe" (I didn't have the universe lines uncommented in sources.list). I'm gonna try just "apt-get install xorg xfce4" (or maybe even fluxbox instead of xfce4).

What I want it to have the server normally run without X running at all. But for the times when I'm at the physical server I'd like to be able to type "startx" so that I can run the VMware Server Consol right there on the server, then quit out of X again when I'm finished so that it's not taking up RAM.

Cheers
--Dan

---

