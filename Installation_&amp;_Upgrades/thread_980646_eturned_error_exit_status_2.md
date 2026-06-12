---
title: "eturned error exit status 2"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2008-11-13
Hi all,

whenever i try to upgrade via update manager i am getting the following 
message 

[B]E: base-files: subprocess post-installation script returned error exit status 2
[/B]

what should i do to make  updates possible ?

NB:- I use ubuntu 8.04.1

---

### Post by Partyboi2 on 2008-11-14
Need more info about the error. Can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Waraqa on 2009-01-03
I have the same problem
```

uae@uae-desktop:~$ [COLOR="Red"]sudo apt-get update[/COLOR]
Hit http://ae.archive.ubuntu.com hardy Release.gpg
Hit http://archive.canonical.com hardy Release.gpg                             
Hit http://archive.ubuntu.com hardy Release.gpg                                
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Hit http://archive.ubuntu.com hardy Release                                    
Ign http://ae.archive.ubuntu.com hardy/main Translation-en_US                  
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Hit http://archive.ubuntu.com hardy/main Sources                               
Hit http://archive.ubuntu.com hardy/restricted Sources                         
Ign http://ae.archive.ubuntu.com hardy/restricted Translation-en_US            
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Hit http://archive.canonical.com hardy Release                       
Hit http://archive.canonical.com hardy/partner Packages                        
Ign http://ae.archive.ubuntu.com hardy/universe Translation-en_US    
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://ppa.launchpad.net hardy Release.gpg                       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://ppa.launchpad.net hardy/main Translation-en_US            
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]
Hit http://security.ubuntu.com hardy-security Release                      
Hit http://security.ubuntu.com hardy-security/main Packages                
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Ign http://ppa.launchpad.net hardy/main Packages      
Get:2 http://ppa.launchpad.net hardy/main Packages [7803B]
Ign http://ae.archive.ubuntu.com hardy/multiverse Translation-en_US
Get:3 http://ae.archive.ubuntu.com hardy-updates Release.gpg [189B]
Ign http://ae.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://ae.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://ae.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://ae.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://ae.archive.ubuntu.com hardy Release
Get:4 http://ae.archive.ubuntu.com hardy-updates Release [58.5kB]
Ign http://ae.archive.ubuntu.com hardy-updates Release
Hit http://ae.archive.ubuntu.com hardy/main Packages
Hit http://ae.archive.ubuntu.com hardy/restricted Packages
Hit http://ae.archive.ubuntu.com hardy/restricted Sources
Hit http://ae.archive.ubuntu.com hardy/main Sources     
Hit http://ae.archive.ubuntu.com hardy/multiverse Sources
Hit http://ae.archive.ubuntu.com hardy/universe Sources
Hit http://ae.archive.ubuntu.com hardy/universe Packages                       
Hit http://ae.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://ae.archive.ubuntu.com hardy-updates/main Packages                   
Hit http://ae.archive.ubuntu.com hardy-updates/restricted Packages             
Hit http://ae.archive.ubuntu.com hardy-updates/restricted Sources              
Hit http://ae.archive.ubuntu.com hardy-updates/main Sources                    
Hit http://ae.archive.ubuntu.com hardy-updates/multiverse Sources              
Hit http://ae.archive.ubuntu.com hardy-updates/universe Sources                
Hit http://ae.archive.ubuntu.com hardy-updates/universe Packages               
Hit http://ae.archive.ubuntu.com hardy-updates/multiverse Packages             
Fetched 35.6kB in 6s (5251B/s)                                                 
Reading package lists... Done
W: GPG error: http://ae.archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
uae@uae-desktop:~$ [COLOR="Red"]sudo apt-get upgrade[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libdns35 libisccc30 libisccfg30
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
The following packages will be upgraded:
  adobe-flashplugin alacarte anacron app-install-data-commercial apt apt-utils
  avahi-autoipd avahi-daemon compiz-fusion-plugins-main cupsys cupsys-bsd
  cupsys-client cupsys-common dbus dbus-x11 deskbar-applet eject eog evince
  evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-exchange evolution-plugins
  firefox-gnome-support foo2zjs gcalctool gdb gdm gnome-about gnome-cards-data
  gnome-desktop-data gnome-games gnome-games-data gnome-panel gnome-panel-data
  gnome-system-monitor grub gstreamer0.10-tools gtk2-engines
  gtk2-engines-murrine gtk2-engines-pixbuf gtk2-engines-ubuntulooks
  gtkhtml3.14 gvfs gvfs-backends gvfs-fuse hal hal-info hpijs hplip hplip-data
  initramfs-tools iproute jockey-common jockey-gtk language-pack-ar
  language-pack-ar-base language-pack-en language-pack-gnome-ar
  language-pack-gnome-ar-base language-pack-gnome-en libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-compat-libdnssd1
  libavahi-core5 libavahi-glib1 libavahi-gobject0 libavahi-qt3-1 libavahi-ui0
  libcamel1.2-11 libcupsimage2 libcupsys2 libdbus-1-3 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 libexif12
  libfreetype6 libgadu3 libgdata-google1.2-1 libgdata1.2-1 libgksu2-0
  libglib2.0-0 libglibmm-2.4-1c2a libgnome-desktop-2 libgnutls13 libgphoto2-2
  libgphoto2-port0 libgstreamer0.10-0 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libgtkhtml3.14-19 libgtksourceview2.0-0
  libgtksourceview2.0-common libgvfscommon0 libgweather-common libgweather1
  libhal-storage1 libhal1 libimlib2 liblcms1 liblwres30 libnautilus-extension1
  libnspr4-0d libnss3-1d libpanel-applet2-0 libpurple0 libsmbclient libsmbios1
  libsnmp-base libsnmp15 libsoup2.4-1 libvorbis0a libvorbisenc2 libvorbisfile3
  libwnck-common libwnck22 libxml2 libxml2-utils
  linux-restricted-modules-common logrotate module-init-tools nautilus
  nautilus-data nautilus-sendto nvidia-glx-new openoffice.org-base-core
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-gnome openoffice.org-gtk
  openoffice.org-help-en-gb openoffice.org-help-en-us openoffice.org-impress
  openoffice.org-l10n-common openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-style-human openoffice.org-writer
  passwd pciutils pidgin pidgin-data procps python-apt python-gobject
  python-gtkhtml2 python-libxml2 python-uno rdesktop samba-common smbclient
  sudo thunderbird-locale-en-gb ttf-opensymbol tzdata ubuntu-docs ufw
  update-manager update-manager-core update-notifier update-notifier-common
  vinagre winbind wine xkb-data xserver-xorg-video-intel xulrunner-1.9
  xulrunner-1.9-gnome-support
180 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
Need to get 7934kB/203MB of archives.
After this operation, 8315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  cupsys-common libdbus-1-3 libcupsys2 libcupsimage2 procps cupsys
  language-pack-ar language-pack-ar-base language-pack-en
  language-pack-gnome-ar language-pack-gnome-ar-base language-pack-gnome-en
  libglib2.0-0 libgtk2.0-common gtk2-engines-pixbuf libgtk2.0-0
  libgstreamer0.10-0 libnspr4-0d libnss3-1d ubuntu-docs libexif12 libhal1
  libgphoto2-port0 libgphoto2-2 wine apt tzdata apt-utils eject
  module-init-tools initramfs-tools iproute pciutils sudo xkb-data liblwres30
  anacron logrotate python-apt ufw update-manager update-manager-core
  gnome-about gnome-desktop-data gnome-panel-data libedataserver1.2-9
  libcamel1.2-11 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libsoup2.4-1 libegroupwise1.2-13 libgdata1.2-1
  libgdata-google1.2-1 evolution-data-server evolution-data-server-common
  libedataserverui1.2-8 libgnome-desktop-2 libgweather-common libgweather1
  libpanel-applet2-0 libwnck-common libwnck22 gnome-panel alacarte
  app-install-data-commercial dbus cupsys-bsd cupsys-client dbus-x11
  deskbar-applet eog libnautilus-extension1 evince evolution evolution-common
  libgtkhtml3.14-19 gtkhtml3.14 libexchange-storage1.2-3 evolution-exchange
  evolution-plugins foo2zjs gcalctool gdb gdm gnome-cards-data
  gnome-games-data gnome-games libglibmm-2.4-1c2a gnome-system-monitor grub
  gstreamer0.10-tools gtk2-engines gtk2-engines-murrine
  gtk2-engines-ubuntulooks libgvfscommon0 libsmbclient gvfs-backends gvfs
  gvfs-fuse hal-info libhal-storage1 libsmbios1 hal jockey-gtk jockey-common
  libgksu2-0 libgtk2.0-bin libgtksourceview2.0-common libgtksourceview2.0-0
  nautilus-sendto nautilus-data nautilus python-gobject python-gtkhtml2
  winbind smbclient samba-common thunderbird-locale-en-gb
  update-notifier-common update-notifier xserver-xorg-video-intel
Install these packages without verification [y/N]? y
Get:1 http://ppa.launchpad.net hardy/main wine 1.1.11~winehq0~ubuntu~8.04-0ubuntu1 [7934kB]
Fetched 7934kB in 2min24s (54.9kB/s)                                           
Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up base-files (4.0.1ubuntu5.8.04.3) ...
find: /var/cache/fonts: No such file or directory
find: /var/cache/anthy: No such file or directory
chgrp 0 /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/KacstLetter.ttf /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/KacstQura.ttf /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/KacstQuraFixed.ttf /var/lib/defoma/gs.d/dirs/fonts/KacstLetter.ttf /var/lib/defoma/gs.d/dirs/fonts/KacstQura.ttf /var/lib/defoma/gs.d/dirs/fonts/KacstQuraFixed.ttf 
chgrp: cannot dereference `/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/KacstLetter.ttf': No such file or directory
chgrp: cannot dereference `/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/KacstQura.ttf': No such file or directory
chgrp: cannot dereference `/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/KacstQuraFixed.ttf': No such file or directory
chgrp: cannot dereference `/var/lib/defoma/gs.d/dirs/fonts/KacstLetter.ttf': No such file or directory
chgrp: cannot dereference `/var/lib/defoma/gs.d/dirs/fonts/KacstQura.ttf': No such file or directory
chgrp: cannot dereference `/var/lib/defoma/gs.d/dirs/fonts/KacstQuraFixed.ttf': No such file or directory
dpkg: error processing base-files (--configure):
 subprocess post-installation script returned error exit status 123
Errors were encountered while processing:
 base-files
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can anyone help me ?

---

### Post by Waraqa on 2009-01-04
I'm currently unable to install any package due to this error !

Any help would be appreciated !

---

