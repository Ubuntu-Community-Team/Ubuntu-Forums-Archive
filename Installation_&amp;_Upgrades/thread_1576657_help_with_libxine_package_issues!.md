---
title: "help with libxine package issues?!"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by gimpchrist on 2010-09-17
Heyy, so I'm fairly non-technical when it comes to knowing how to figure out linux, so please go easy on me. 
I haven't been able to DL updates for a really long time for some reason it keeps telling me there is a package broken. I utilized the pacman to find out that its saying the libxine1-bin pack is broken. Its version 1.1.16.3-0ubuntu2~xine.vdpau~karmic~ppa7

I duno if this helps, but its saying to run sudo apt-get install -f, but then when I run it in terminal it says


root@jessica:/home/jessica# sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libxfcegui4-4 libfreebob0 libqca2 linux-headers-2.6.31-14 ttf-wqy-zenhei
  nvidia-190-libvdpau upower libburn4 libupower-glib1 amarok-common
  kdemultimedia-kio-plugins libkcddb4 binutils-static libakonadiprivate1
  libqtscript4-core libexo-0.3-0 libgnomecanvasmm-2.6-1c2a libclutter-1.0-0
  libqtscript4-gui libqtscript4-uitools libffado1 libclutter-gtk-0.10-0
  libindicate-qt0 thunar-data libqtscript4-sql kdepimlibs5 libxml++2.6-2
  libgnomemm-2.6-1c2 libqtscript4-xml libgconfmm-2.6-1c2 libtag-extras1
  libgnome-vfsmm-2.6-1c2a libisofs6 liblastfm0 libgnomeuimm-2.6-1c2a
  linux-headers-2.6.31-14-generic amarok-utils kdepimlibs-data
  libqtscript4-network libglademm-2.4-1c2a libthunar-vfs-1-2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  consolekit fontconfig-config gdm ifupdown indicator-applet
  indicator-applet-session initramfs-tools initramfs-tools-bin libasound2
  libatk1.0-0 libatk1.0-dev libc-bin libc-dev-bin libc6 libc6-dev libc6-i686
  libdevkit-power-gobject1 libdrm-nouveau1 libdrm-radeon1 libfontconfig1
  libfontconfig1-dev libglib2.0-0 libglib2.0-dev libindicator0 libjack0
  libmagickcore2 libmagickwand2 libnih-dbus1 libnih1 libplymouth2 libpopt0
  libudev0 libupower-glib1 libxine1 libxine1-bin libxine1-console
  libxine1-ffmpeg libxine1-misc-plugins libxine1-x libxklavier16 mountall
  plymouth udev upower upstart ureadahead
Suggested packages:
  uswsusp gok glibc-doc libglib2.0-doc python-subunit jackd
  libmagickcore2-extra libxine1-doc libxine-doc watershed
Recommended packages:
  indicator-sound indicator-application indicator-me manpages-dev
  plymouth-theme-ubuntu-text plymouth-theme
The following packages will be REMOVED:
  devicekit-power gnome-power-manager indicator-session ubuntu-desktop usplash
  usplash-theme-ubuntu
The following NEW packages will be installed:
  initramfs-tools-bin libdrm-nouveau1 libindicator0 libnih-dbus1 libnih1
  libplymouth2 libupower-glib1 libxklavier16 plymouth upower
The following packages will be upgraded:
  consolekit fontconfig-config gdm ifupdown indicator-applet
  indicator-applet-session initramfs-tools libasound2 libatk1.0-0
  libatk1.0-dev libc-bin libc-dev-bin libc6 libc6-dev libc6-i686
  libdevkit-power-gobject1 libdrm-radeon1 libfontconfig1 libfontconfig1-dev
  libglib2.0-0 libglib2.0-dev libjack0 libmagickcore2 libmagickwand2 libpopt0
  libudev0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg
  libxine1-misc-plugins libxine1-x mountall udev upstart ureadahead
36 upgraded, 10 newly installed, 6 to remove and 1499 not upgraded.
7 not fully installed or removed.
Need to get 0B/22.9MB of archives.
After this operation, 8,081kB disk space will be freed.
Do you want to continue [Y/n]? y
E: Internal Error, Could not perform immediate configuration (2) on mountall
root@jessica:/home/jessica# 



Sooo, at this point I have no idea wot im doing. Had no idea anyways, but if someone could help?

---

### Post by gimpchrist on 2010-09-17
Also, when I try to do a partial upgrade, it says:

Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.

and I have no idear what that means.

---

