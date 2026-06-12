---
title: "Partial Update is becoming very annoying!"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by Elie-M on 2010-04-09
hello, I always get the partial update annoying pop-up! so I decided to get rid of it

I ran sudo apt-get dist-upgrade

I got this:

elie-m@elie-m-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  acpi-support acpid alsa-base alsa-utils apache2 apache2-mpm-prefork apache2.2-common apport apport-gtk at avahi-daemon bind9 blueman bluetooth bluez
  bluez-cups bluez-utils brltty brltty-x11 checkbox checkbox-gtk console-setup couchdb-bin cron cups cups-driver-gutenprint cupsys cupsys-driver-gimpprint
  cupsys-driver-gutenprint desktopcouch dkms dmsetup erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl
  erlang-syntax-tools erlang-xmerl evolution-couchdb foo2zjs foomatic-db foomatic-db-engine friendly-recovery ftp fuse-utils gdm gdm-guest-session
  ghostscript-cups gnome-bluetooth gnome-system-tools gnome-user-share gvfs-fuse hal hpijs hplip icoutils ifupdown indicator-applet-session
  indicator-session initramfs-tools kbd lftp libapache2-mod-dnssd libapache2-mod-php5 libcanberra-pulse libnet-dbus-perl libnss-mdns liboobs-1-4
  librpc-xml-perl libwww-perl libwww-search-perl libxml-parser-perl libxml-twig-perl libxml-xpath-perl linux-generic linux-image-2.6.31-14-generic
  linux-image-2.6.31-16-generic linux-image-generic linux-sound-base media-player-info module-init-tools netbase network-manager network-manager-gnome
  nfs-common ntfs-3g ntpdate openoffice.org-emailmerge openprinting-ppds openssh-server pcmciautils playonlinux pm-utils portmap powermgmt-base ppp
  pppconfig pppoeconf procps proftpd proftpd-common pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf
  pulseaudio-module-udev pulseaudio-module-x11 pxljr python-desktopcouch python-desktopcouch-records rhythmbox rsyslog samba smbfs splix sreadahead ssh
  system-tools-backends telepathy-salut telnet truecrypt ubuntu-desktop ubuntu-minimal ubuntu-standard udev ufw ureadahead usplash usplash-theme-ubuntu
  virtualbox-ose-source wine1.2 wireless-crda xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb
  xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vmware
  xserver-xorg-video-voodoo
The following NEW packages will be installed:
  libgnutls12 liblzo1 libmysqlclient15off libopencdk8 libpq4 libtasn1-2 libtasn1-2-bin linux-headers-2.6.31-21 linux-headers-2.6.31-21-generic
The following packages will be upgraded:
  linux-headers-generic
1 upgraded, 9 newly installed, 176 to remove and 0 not upgraded.
Need to get 12.9MB of archives.
After this operation, 374MB disk space will be freed.
Do you want to continue [Y/n]? 


but the thing is what's this??? Why is it trying to remove many applications I use including apache2, telnet, bind9, wine1.2, cron, cups, linux-image among many many others packages?? what exactly is partial update and why is it doing this? and any other way to get rid of it?

---

### Post by mikewhatever on 2010-04-09
Can you post the output of 'uname -r', just wondering what's the kernel version you are currently running.

---

### Post by Elie-M on 2010-04-09
elie-m@elie-m-laptop:~$ uname -r
2.6.31-16-generic

---

### Post by mikewhatever on 2010-04-09
Very odd, it want's to remove the currently used kernel. How did you start getting the 'partial update' message?

---

### Post by Elie-M on 2010-04-09
believe me I dont remember how.. all I remember is being asked 1 day to do a partial update and I didn't know that it does this to save info about it :-/

---

### Post by Elie-M on 2010-04-09
also there's this: [http://i156.photobucket.com/albums/t18/Mankind-195/Screenshot-1.png](http://i156.photobucket.com/albums/t18/Mankind-195/Screenshot-1.png)

I can't even update the distro I think, nor vlc

---

### Post by Elie-M on 2010-04-09
bump

---

### Post by Elie-M on 2010-05-17
manually updated through synaptic and renewed all the ppas and removed broken ones.

---

