---
title: "Getting only terminal after booting after 12.0.4 upgrade"
date: 2013-11-21
forum: Installation &amp; Upgrades
---

### Post by theredbaron908 on 2013-11-21
I only get the standard desktop after running startx in terminal. I tried running

 sudo apt-get -f install --reinstall ubuntu-desktop xorg build-essential

But got

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-desktop : Depends: baobab but it is not going to be installed
                  Depends: eog but it is not going to be installed
                  Depends: evince but it is not going to be installed
                  Depends: file-roller but it is not going to be installed
                  Depends: gcalctool but it is not going to be installed
                  Depends: gedit but it is not going to be installed
                  Depends: gnome-control-center but it is not going to be installed
                  Depends: gnome-font-viewer but it is not going to be installed
                  Depends: gnome-media but it is not going to be installed
                  Depends: gnome-nettool but it is not going to be installed
                  Depends: gnome-power-manager but it is not going to be installed
                  Depends: gnome-screenshot but it is not going to be installed
                  Depends: gnome-session but it is not going to be installed
                  Depends: gnome-session-canberra but it is not going to be installed
                  Depends: gnome-system-log but it is not going to be installed
                  Depends: gnome-system-monitor but it is not going to be installed
                  Depends: gnome-terminal but it is not going to be installed
                  Depends: gucharmap but it is not going to be installed
                  Depends: language-selector-gnome but it is not going to be installed
                  Depends: nautilus but it is not going to be installed
                  Depends: nautilus-sendto but it is not going to be installed
                  Depends: notify-osd but it is not going to be installed
                  Depends: seahorse but it is not going to be installed
                  Depends: software-center but it is not going to be installed
                  Depends: software-properties-gtk but it is not going to be installed
                  Depends: ssh-askpass-gnome but it is not going to be installed
                  Depends: system-config-printer-gnome but it is not going to be installed
                  Depends: ubuntu-artwork but it is not going to be installed
                  Depends: unity but it is not going to be installed
                  Depends: unity-2d but it is not going to be installed
                  Depends: unity-greeter but it is not going to be installed
                  Depends: update-manager but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
                  Depends: xdg-user-dirs-gtk but it is not going to be installed
                  Depends: xdiagnose but it is not going to be installed
                  Depends: yelp but it is not going to be installed
                  Depends: zenity
                  Recommends: acpi-support but it is not going to be installed
                  Recommends: activity-log-manager-control-center but it is not going to be installed
                  Recommends: aisleriot but it is not going to be installed
                  Recommends: apport-gtk but it is not going to be installed
                  Recommends: brasero but it is not going to be installed
                  Recommends: deja-dup but it is not going to be installed
                  Recommends: empathy but it is not going to be installed
                  Recommends: firefox but it is not going to be installed
                  Recommends: firefox-gnome-support but it is not going to be installed
                  Recommends: fonts-liberation but it is not going to be installed
                  Recommends: fonts-takao-pgothic but it is not going to be installed
                  Recommends: ginn but it is not going to be installed
                  Recommends: gnome-bluetooth but it is not going to be installed
                  Recommends: gnome-disk-utility but it is not going to be installed
                  Recommends: gnome-orca but it is not going to be installed
                  Recommends: gnome-screensaver but it is not going to be installed
                  Recommends: gnome-sudoku but it is not going to be installed
                  Recommends: gnomine but it is not going to be installed
                  Recommends: gvfs-fuse but it is not going to be installed
                  Recommends: gwibber but it is not going to be installed
                  Recommends: ibus but it is not going to be installed
                  Recommends: ibus-gtk3 but it is not going to be installed
                  Recommends: ibus-pinyin but it is not going to be installed
                  Recommends: ibus-table but it is not going to be installed
                  Recommends: jockey-gtk but it is not going to be installed
                  Recommends: landscape-client-ui-install but it is not going to be installed
                  Recommends: libgail-common but it is not going to be installed
                  Recommends: libreoffice-calc but it is not going to be installed
                  Recommends: libreoffice-gnome but it is not going to be installed
                  Recommends: libreoffice-help-en-us but it is not going to be installed
                  Recommends: libreoffice-impress but it is not going to be installed
                  Recommends: libreoffice-math but it is not going to be installed
                  Recommends: libreoffice-style-human but it is not going to be installed
                  Recommends: libreoffice-writer but it is not going to be installed
                  Recommends: mahjongg but it is not going to be installed
                  Recommends: mousetweaks but it is not going to be installed
                  Recommends: nautilus-share but it is not going to be installed
                  Recommends: network-manager-gnome but it is not going to be installed
                  Recommends: network-manager-pptp-gnome but it is not going to be installed
                  Recommends: onboard but it is not going to be installed
                  Recommends: overlay-scrollbar but it is not going to be installed
                  Recommends: remmina but it is not going to be installed
                  Recommends: rhythmbox but it is not going to be installed
                  Recommends: rhythmbox-plugin-magnatune but it is not going to be installed
                  Recommends: rhythmbox-ubuntuone but it is not going to be installed
                  Recommends: shotwell but it is not going to be installed
                  Recommends: simple-scan but it is not going to be installed
                  Recommends: thunderbird but it is not going to be installed
                  Recommends: thunderbird-gnome-support but it is not going to be installed
                  Recommends: totem but it is not going to be installed
                  Recommends: totem-mozilla but it is not going to be installed
                  Recommends: transmission-gtk but it is not going to be installed
                  Recommends: ubuntu-docs but it is not going to be installed
                  Recommends: ubuntuone-client-gnome but it is not going to be installed
                  Recommends: ubuntuone-installer but it is not going to be installed
                  Recommends: usb-creator-gtk but it is not going to be installed
                  Recommends: vino but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


Any idea what am I dealing with here?

---

