---
title: "can't install g++ and build-essential"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by mefistofeles666 on 2008-10-06
hey guys, i was trying to install g++ and build essentials but i can't do it. and i get this back

tan@sakura:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for build-essential
No candidate version found for build-essential
The following packages have been automatically kept back:
  libavcodec1d libavformat1d libavutil1d libc6-dev libfaad0 libpostproc1d 
  libvlc0 vlc-nox 
The following packages have been kept back:
  anacron app-install-data-commercial compiz-fusion-plugins-main 
  deskbar-applet eject eog evolution-data-server 
  evolution-data-server-common firefox firefox-3.0 
  firefox-3.0-gnome-support firefox-gnome-support gcalctool gdb gdm 
  gnome-about gnome-cards-data gnome-desktop-data gnome-games 
  gnome-games-data kaffeine libc6 libc6-i686 libfreetype6 libglib2.0-0 
  libnautilus-extension1 libnspr4-0d libsmbclient libsmbios1 libsoup2.4-1 
  libxml2 libxml2-utils mplayer nautilus nautilus-data python-gtkhtml2 
  python-libxml2 rdesktop sudo ufw update-manager update-manager-core 
  update-notifier update-notifier-common vlc vlc-plugin-esd 
  vlc-plugin-pulse xulrunner-1.9 xulrunner-1.9-gnome-support 
0 packages upgraded, 0 newly installed, 0 to remove and 57 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done  





an@sakura:~$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  g++: Depends: g++-4.2 (>= 4.2.3-1) but it is not installable
E: Broken packages

any ideas?

---

### Post by Pumalite on 2008-10-06
Try:
sudo dpkg --configure -a 
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by Partyboi2 on 2008-10-06
Also check that you have the repositories enabled under Software Sources (System>Admin>>Software Sources)

---

### Post by cariboo on 2008-10-07
If worse comes to worse, build-essential is on the LiveCD.

Jim

---

### Post by abhilashm86 on 2008-10-07
sudo aptitude update && sudo aptitude install build-essential
u better try this,automatically g++ compiler gets installed............pls reply after u do:)

---

### Post by Sealbhach on 2008-10-18
> **abhilashm86 said:**
> sudo aptitude update && sudo aptitude install build-essential
u better try this,automatically g++ compiler gets installed............pls reply after u do:)

Thank you!  That fixed it for me.


.

---

