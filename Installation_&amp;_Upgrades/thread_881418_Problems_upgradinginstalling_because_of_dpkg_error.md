---
title: "Problems upgrading/installing because of dpkg error"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by conscott on 2008-08-06
While updating/installing I now get the error message

> conor@conor-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  evolution-data-server evolution-data-server-common f-spot gucharmap gvfs
  gvfs-backends libebook1.2-9 libedata-book1.2-2 libedataserverui1.2-8
  libenchant1c2a libsmbclient linux-generic linux-headers-generic
  linux-image-generic linux-restricted-modules-generic rhythmbox samba-common
  smbclient ubuntu-desktop winbind
The following packages will be upgraded:
  acpid alsa-utils anacron app-install-data apport apport-gtk apt apt-utils
  apturl at-spi bluez-audio bluez-cups bluez-utils brltty brltty-x11 bsh
  bug-buddy capplets-data consolekit cpp-4.3 dbus dbus-x11 dhcdbd dpkg-dev eog
  evolution-common fast-user-switch-applet file-roller friendly-recovery
  g++-4.3 gcalctool gcc-4.3 gcc-4.3-base gdebi gdebi-core gedit gedit-common
  gettext gettext-base ghostscript ghostscript-x gnome-about
  gnome-accessibility-themes gnome-cards-data gnome-control-center
  gnome-desktop-data gnome-games gnome-games-data gnome-keyring gnome-mag
  gnome-menus gnome-orca gnome-settings-daemon gnome-system-monitor
  gnome-themes gnome-volume-manager gnupg gparted gpgv grub gstreamer0.10-esd
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gtk2-engines
  gtk2-engines-pixbuf gvfs-fuse hal human-theme initramfs-tools java-common
  klibc-utils klogd libalut0 libatspi1.0-0 libbrlapi0.5 libcamel1.2-12
  libck-connector0 libdbus-1-3 libebackend1.2-0 libecal1.2-7 libedata-cal1.2-6
  libedataserver1.2-11 libeel2-2 libeel2-data libegroupwise1.2-13
  libexchange-storage1.2-3 libgcc1 libgd2-noxpm libgda3-3 libgda3-common
  libgdata-google1.2-1 libgdata1.2-1 libgfortran3 libgl1-mesa-dri
  libgl1-mesa-glx libglib2.0-0 libglib2.0-data libglu1-mesa
  libgnome-desktop-2-7 libgnome-keyring0 libgnome-mag2 libgnome-menu2
  libgnome-speech7 libgnome-window-settings1 libgnomevfs2-0 libgnomevfs2-bin
  libgnomevfs2-common libgnomevfs2-extra libgomp1 libgphoto2-2
  libgphoto2-port0 libgs8 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libgtkhtml3.14-19 libgvfscommon0 libhal-storage1 libhal1 libhsqldb-java
  libjaxp1.3-java libjline-java libklibc libldap-2.4-2 libloudmouth1-0
  libltdl7 libnautilus-extension1 libpam-gnome-keyring libpciaccess0 libpcre3
  libpcrecpp0 libpixman-1-0 libpoppler-glib3 libpoppler3 libpulse-browse0
  libpulse0 libpulsecore5 libqt4-assistant libqt4-core libqt4-dbus
  libqt4-designer libqt4-gui libqt4-network libqt4-opengl libqt4-script
  libqt4-sql libqt4-svg libqt4-test libqt4-xml libqtcore4 libqtgui4
  libservlet2.4-java libsoup2.4-1 libstdc++6 libstdc++6-4.3-dev
  libxerces2-java libxxf86vm1 linux-libc-dev mesa-utils mousetweaks nautilus
  nautilus-data openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
  openoffice.org-writer2latex poppler-utils pulseaudio
  pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal
  pulseaudio-module-x11 pulseaudio-utils python-apport python-apt
  python-brlapi python-cups python-cupshelpers python-gmenu
  python-problem-report python-pyatspi python2.5 python2.5-minimal rhino
  shared-mime-info sound-juicer sun-java6-bin sun-java6-jre sun-java6-plugin
  synaptic sysklogd system-config-printer-common system-config-printer-gnome
  texmaker tgif tomboy totem totem-common totem-gstreamer totem-mozilla
  totem-plugins totem-xine tzdata tzdata-java ubuntu-artwork ubuntu-docs
  ubuntu-minimal ubuntu-standard update-manager update-manager-core vinagre
  vino wacom-tools xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-synaptics xserver-xorg-input-wacom xserver-xorg-video-mga
  xserver-xorg-video-openchrome xutils-dev
220 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
1 not fully installed or removed.
Need to get 0B/205MB of archives.
After this operation, 7840kB disk space will be freed.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
[B]dpkg: error processing dpkg (--configure):
 package dpkg is not ready for configuration
 cannot configure (current status `triggers-awaited')
Errors were encountered while processing:
 dpkg
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]


i have tried
> sudo dpkg --configure -a 

with no luck

any ideas?

---

### Post by zvacet on 2008-08-06
```
sudo apt-get -f install
```

---

### Post by kemadruma on 2008-09-26
still, I m getting error like ```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


```

when i perform sudo dpkg --configure -a

it says

```

dpkg: parse error, in file `/var/lib/dpkg/updates/0049' near line 1:
 newline in field name `#padding'


```

the file /var/lib/dpkg/updates/0049 contains on
```

#padding
#padding
#padding
.
.
.
.



```
without any new line.

wat to do???

---

### Post by ichigo6420 on 2011-03-19
i'm having exactly the same problem...what do i do?!

---

