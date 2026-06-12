---
title: "ubuntu-desktop package has unresolvable depedencies"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by Velotix on 2006-11-11
OK, I'm moving this query here because it's become obvious to me that this is actually too serious an issue to leave in the newb forum.

Original topic: [http://www.ubuntuforums.org/showthread.php?t=297662](http://www.ubuntuforums.org/showthread.php?t=297662)

Original post:

> This computer originally ran Xubuntu 6.10, but last night I installed Kubuntu with no problems. However, when I try to install the ubuntu-desktop package, I seem to run into problems. The important parts are highlighted in bold:

```
****@****:~$ sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
[b]The following packages are BROKEN:
  evince-gtk xubuntu-system-tools[/b] 
The following packages have been automatically kept back:
  libavahi-client3 libavahi-compat-libdnssd1 libavahi-qt3-1 
  linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common 
The following NEW packages will be automatically installed:
  alacarte aspell aspell-en at-spi binfmt-support bittorrent brltty-x11 
  bug-buddy capplets-data cli-common contact-lookup-applet deskbar-applet 
  desktop-base ekiga eog esound evince evolution evolution-data-server 
  evolution-data-server-common evolution-exchange evolution-plugins 
  evolution-webcal f-spot festival festlex-cmu festlex-poslex 
  festvox-kallpc16k file-roller firefox-gnome-support gcalctool 
  gconf-editor gedit gedit-common gimp-python gnome-about gnome-applets 
  gnome-applets-data gnome-btdownload gnome-control-center 
  gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games 
  gnome-games-data gnome-keyring-manager gnome-mag gnome-media 
  gnome-media-common gnome-menus gnome-mime-data gnome-netstatus-applet 
  gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot 
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session 
  gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal 
  gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager 
  gnome2-user-guide gstreamer0.10-alsa gstreamer0.10-esd 
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-base 
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good 
  gstreamer0.10-tools gstreamer0.10-x gthumb gtkhtml3.8 gucharmap 
  guile-1.6-libs hal-device-manager hwdb-client-gnome libatspi1.0-0 
  libavahi-glib1 libavc1394-0 libbeagle0 libbeecrypt6 libbonobo2-0 
  libbonobo2-common libbonoboui2-0 libbonoboui2-common libbtctl4 
  libcairo-perl libcamel1.2-8 libcdio6 libdbus-1-cil libdjvulibre15 libdv4 
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 
  libedataserver1.2-7 libedataserverui1.2-8 libeel2-2 libeel2-data 
  libegroupwise1.2-12 libestools1.2 libexchange-storage1.2-2 
  libgconf2.0-cil libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common 
  libgksu1.2-1 libgksuui1.0-1 libglade2.0-cil libglew1 libglib-perl 
  libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-desktop-2 
  libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 
  libgnome-speech3 libgnome-window-settings1 libgnome2-0 
  libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl 
  libgnome2.0-cil libgnomebt0 libgnomecupsui1.0-1c2a libgnomeui-0 
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common 
  libgnomevfs2-extra libgtk2-perl libgtk2.0-cil libgtkhtml3.8-15 
  libgtksourceview-common libgtksourceview1.0-0 libgucharmap5 
  libguile-ltdl-1 libiec61883-0 liblpint-bonobo0 libmetacity0 
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil 
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil 
  libmono-system1.0-cil libmono0 libmono1.0-cil libnautilus-burn4 
  libnautilus-extension1 liboil0.3 libopal-2.2.0 libpanel-applet2-0 
  libpisock9 libpisync0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l 
  libpt-plugins-v4l2 libqthreads-12 librpm4 libshout3 libsoup2.2-8 
  libtotem-plparser1 libxevie1 libxklavier11 libxml2-utils metacity 
  metacity-common mono-common mono-gac mono-jit mono-runtime nautilus 
  nautilus-cd-burner nautilus-data nautilus-sendto openoffice.org-evolution 
  openoffice.org-gnome openoffice.org-gtk python-at-spi python-gmenu 
  python-gnome2 python-gnome2-desktop python-gnome2-extras 
  python-gnomecanvas python-gst0.10 rdesktop rhythmbox rpm rss-glx 
  screensaver-default-images serpentine sharutils sound-juicer 
  ssh-askpass-gnome tangerine-icon-theme tomboy totem totem-gstreamer 
  totem-mozilla tsclient ubuntu-docs update-notifier usplash-theme-ubuntu 
  vino vnc-common whois xsane xsane-common xsltproc xvncviewer yelp zenity 
The following packages will be automatically REMOVED:
  gcalctool-gtk 
The following packages have been kept back:
  avahi-daemon info libavahi-common-data libavahi-common3 libavahi-core4 
  screen 
The following NEW packages will be installed:
  alacarte aspell aspell-en at-spi binfmt-support bittorrent brltty-x11 
  bug-buddy capplets-data cli-common contact-lookup-applet deskbar-applet 
  desktop-base ekiga eog esound evince evolution evolution-data-server 
  evolution-data-server-common evolution-exchange evolution-plugins 
  evolution-webcal f-spot festival festlex-cmu festlex-poslex 
  festvox-kallpc16k file-roller firefox-gnome-support gcalctool 
  gconf-editor gedit gedit-common gimp-python gnome-about gnome-applets 
  gnome-applets-data gnome-btdownload gnome-control-center 
  gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games 
  gnome-games-data gnome-keyring-manager gnome-mag gnome-media 
  gnome-media-common gnome-menus gnome-mime-data gnome-netstatus-applet 
  gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot 
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session 
  gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal 
  gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager 
  gnome2-user-guide gstreamer0.10-alsa gstreamer0.10-esd 
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-base 
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good 
  gstreamer0.10-tools gstreamer0.10-x gthumb gtkhtml3.8 gucharmap 
  guile-1.6-libs hal-device-manager hwdb-client-gnome libatspi1.0-0 
  libavahi-glib1 libavc1394-0 libbeagle0 libbeecrypt6 libbonobo2-0 
  libbonobo2-common libbonoboui2-0 libbonoboui2-common libbtctl4 
  libcairo-perl libcamel1.2-8 libcdio6 libdbus-1-cil libdjvulibre15 libdv4 
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 
  libedataserver1.2-7 libedataserverui1.2-8 libeel2-2 libeel2-data 
  libegroupwise1.2-12 libestools1.2 libexchange-storage1.2-2 
  libgconf2.0-cil libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common 
  libgksu1.2-1 libgksuui1.0-1 libglade2.0-cil libglew1 libglib-perl 
  libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-desktop-2 
  libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 
  libgnome-speech3 libgnome-window-settings1 libgnome2-0 
  libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl 
  libgnome2.0-cil libgnomebt0 libgnomecupsui1.0-1c2a libgnomeui-0 
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common 
  libgnomevfs2-extra libgtk2-perl libgtk2.0-cil libgtkhtml3.8-15 
  libgtksourceview-common libgtksourceview1.0-0 libgucharmap5 
  libguile-ltdl-1 libiec61883-0 liblpint-bonobo0 libmetacity0 
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil 
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil 
  libmono-system1.0-cil libmono0 libmono1.0-cil libnautilus-burn4 
  libnautilus-extension1 liboil0.3 libopal-2.2.0 libpanel-applet2-0 
  libpisock9 libpisync0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l 
  libpt-plugins-v4l2 libqthreads-12 librpm4 libshout3 libsoup2.2-8 
  libtotem-plparser1 libxevie1 libxklavier11 libxml2-utils metacity 
  metacity-common mono-common mono-gac mono-jit mono-runtime nautilus 
  nautilus-cd-burner nautilus-data nautilus-sendto openoffice.org-evolution 
  openoffice.org-gnome openoffice.org-gtk python-at-spi python-gmenu 
  python-gnome2 python-gnome2-desktop python-gnome2-extras 
  python-gnomecanvas python-gst0.10 rdesktop rhythmbox rpm rss-glx 
  screensaver-default-images serpentine sharutils sound-juicer 
  ssh-askpass-gnome tangerine-icon-theme tomboy totem totem-gstreamer 
  totem-mozilla tsclient ubuntu-desktop ubuntu-docs update-notifier 
  usplash-theme-ubuntu vino vnc-common whois xsane xsane-common xsltproc 
  xvncviewer yelp zenity 
[b]The following packages will be REMOVED:
  gcalctool-gtk[/b] 
0 packages upgraded, 233 newly installed, 1 to remove and 11 not upgraded.
Need to get 119MB of archives. After unpacking 567MB will be used.
[b]The following packages have unmet dependencies:
  xubuntu-system-tools: Conflicts: gnome-system-tools but 2.15.5-0ubuntu2 is to be installed.
  evince-gtk: Conflicts: evince but 0.6.1-0ubuntu1 is to be installed.
[i]Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
deskbar-applet [Not Installed]
evince [Not Installed]
file-roller [Not Installed]
gedit [Not Installed]
gnome-applets [Not Installed]
gnome-games [Not Installed]
gnome-games-data [Not Installed]
gnome-media [Not Installed]
gnome-media-common [Not Installed]
gnome-panel [Not Installed]
gnome-panel-data [Not Installed]
gnome-session [Not Installed]
gnome-system-tools [Not Installed]
gnome-volume-manager [Not Installed]
gstreamer0.10-plugins-good [Not Installed]
libdv4 [Not Installed]
libgda2-3 [Not Installed]
libgda2-common [Not Installed]
libgnome-media0 [Not Installed]
nautilus [Not Installed]
nautilus-cd-burner [Not Installed]
nautilus-data [Not Installed]
nautilus-sendto [Not Installed]
python-gnome2-desktop [Not Installed]
python-gnome2-extras [Not Installed]
rhythmbox [Not Installed]
serpentine [Not Installed]
sound-juicer [Not Installed]
totem [Not Installed]
totem-gstreamer [Not Installed]
totem-mozilla [Not Installed]
ubuntu-desktop [Not Installed]

Leave the following dependencies unresolved:
gnome-control-center recommends gnome-session
Score is 80[/i][/b]

Accept this solution? [Y/n/q/?]
```

Am I simply worrying over nothing or is there something I need to sort out before I install this package? I don't want to break Xubuntu in the process. ^^

(BTW, KDE kicks butt. ^^)

**EDIT:** Also, it seems Kubuntu uses a different system to log in, which has had a bizarre effect on my Xubuntu desktop: when I select the log out option, it instead shuts down the machine instead and then doesn't switch it off automatically. I'm guessing I need to get back the old session manager somehow - with Ubuntu?

> Just remembered something: I set the default display manager to kdm, which would explain this, and it seems to have broken my Xfce sessions. So how do I switch it back to gdm? I think I need to open the /etc/X11/default-display-manager file and change:

```
/usr/bin/kdm
```

to

```
/usr/bin/gdm
```

but I'm weary of doing this because I can't seem to find any file named gdm, though there are a few files that relate to it. (I can see hidden files.) What do I need to do?

**EDIT:** Yup, tried this and it broke, so I can only assume it doesn't exist. I have a horrible feeling it was uninstalled when I installed Kubuntu, so installing xubuntu- or ubuntu-desktop will probably fix it. Still... D:

**Update:** There are several locations returned by whereis gdm, and I think I've finally found it - I'll test it out tomorrow. What bothers me is  - assuming I've found it - why is it in the /usr/sbin/ directory instead of /usr/bin/ like kdm? (Lemme guess: because gdm is shared with Xfce to enable it to boot? ](*,) )

**Update 2:** I did indeed find GDM. Hopefully Xfce now works properly once more, which would be nice. ^^

---

