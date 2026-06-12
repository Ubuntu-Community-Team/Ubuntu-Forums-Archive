---
title: "Error installing removing KeD"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by leeley on 2006-12-31
:(   I am having a problem with trying to remove K3D from edgy this is what I get when doing what the system tells me to do.](*,) 
lee@lee-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  f-spot libgnomecupsui1.0-1c2a krec tomboy evolution-webcal ekiga
  edgy-community-wallpapers gcalctool libaspell-dev libtunepimp-bin
  gnome-nettool libtasn1-3-dev ubuntu-docs python-at-spi xsane libaudio-dev
  tangerine-icon-theme python-apport-utils gucharmap brltty-x11
  edgy-session-splashes zenity libbtctl4 hwdb-client-gnome gdebi vnc-common
  evolution-exchange x11proto-xinerama-dev resilience-theme
  human-cursors-theme gnome-screensaver rhythmbox x11proto-render-dev
  ubuntu-artwork libxi-dev gnome-themes libxmu-headers libxrender-dev
  python-virtkey ubuntu-sounds mesa-common-dev whois libpt-plugins-v4l2
  scim-modules-socket scim update-notifier qt3-dev-tools apport
  edgy-gdm-themes libavahi-client-dev libjasper-1.701-dev usplash-theme-ubuntu
  mpeglib libpcrecpp0 scim-gtk2-immodule industrialtango-theme k3d human-theme
  gnome-btdownload libxcursor-dev gnome-orca lua50 xvncviewer gtk2-engines
  libpt-plugins-v4l edgy-wallpapers eog gdm screensaver-default-images
  x11proto-randr-dev hspell gtk2-engines-ubuntulooks libdbus-1-cil
  libdbus-1-dev gnome-spell bug-buddy bittorrent language-selector libxmu-dev
  tsclient rdesktop juk gnome-keyring-manager firefox-gnome-support
  human-icon-theme python-problem-report libarts1-mpeglib x11proto-fixes-dev
  kaboodle contact-lookup-applet libgraphics-magick-perl gray-theme
  human-gtk-theme outdoors-theme libqt3-headers xsane-common
  libgraphicsmagick++1 libtiffxx0c2 liblcms1-dev libxrandr-dev libkadm55
  libpt-plugins-alsa hal-device-manager onboard
  gstreamer0.10-plugins-base-apps rss-glx libopal-2.2.0 gconf-editor
  libgnomebt0 libxfixes-dev legacyhuman-theme libgraphicsmagick1
  libavahi-common-dev gnome-accessibility-themes libxinerama-dev apport-gtk
  kdesdk-scripts silicon-theme gstreamer0.10-tools x-dev gettext-kde
  libarts1-xine libidn11-dev file-roller nautilus-sendto gnome-cups-manager
  kmid ssh-askpass-gnome sound-juicer
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  k3d
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 44.5MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... files and directories currently installed.)
Removing k3d ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 932, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing k3d (--remove):
 subprocess pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 k3d
E: Sub-process /usr/bin/dpkg returned an error code (1)
lee@lee-desktop:~$ 



I hope this helps
Thanks Lee:???:

---

### Post by freddyg on 2007-01-01
see here [http://www.ubuntuforums.org/showthread.php?t=303289&page=2&highlight=k3d](http://www.ubuntuforums.org/showthread.php?t=303289&page=2&highlight=k3d)

---

