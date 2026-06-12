---
title: "Lucid Login problem - AMD64"
date: 2010-04-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gare on 2010-04-04
Hello,

Installed Lucid and been updating it. Updates 4 days ago caused a a login loop ,  and I am now unable to get past the Login Prompt.

After recent updates, the login prompt shows a little terminal window on top of the login screen, but same no love.

my hardward profile attached.

Thank you for any help.


Update for clarity:  I can not log in to this computer's Gnome Desktop at all, and am unable to use the machine for its intended purpose.  This computer is in our living room as my home theater pc - and my wife wants it fixed asap so she can watch hulu!  (Have now learned my lesson about Beta on a 'production' machine. :)

---

### Post by gare on 2010-04-04
Hello again -

searching the Lucid bug reports suggests to me that plymouth is the problem.

so my question is when I try to unistall plymouth, why does it appear to want to uninstall my whole system?

```
live@live-desktop:~$ sudo apt-get remove plymouth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-coherence libnumber-compare-perl libswscale0 libtwolame0 gnome-js-common libxml-sax-perl libavutil49 libdigest-sha1-perl libflite1 python-moovida libnet-ip-perl python-mako libnet-dns-perl gstreamer0.10-plugins-bad
  libkpathsea5 intel-gpu-tools libevdocument2 libpthread-stubs0 libnunit2.4-cil gstreamer0.10-plugins-ugly libmodplug0c2 libmysqlclient15off gir1.0-clutter-gtk-0.10 ttf-liberation comerr-dev python-pygoocanvas wesnoth-data
  libboost-python1.40.0 libqt4-test libqt4-script python-louie openoffice.org-l10n-en-gb libqt4-network libfile-find-rule-perl libqt4-dbus liblaunchpad-integration1.0-cil empathy-common python-nevow libevview2 python-mutagen
  docbook-xsl libdca0 libgoocanvas3 libindicate-gtk2 python-twisted-conch liblualib50 libxml-namespacesupport-perl libboost-iostreams1.40.0 libiso9660-7 libxalan110 libfftw3-3 libass4 libxml-libxml-perl python-axiom libkrb5-dev
  libclamav6 python2.4 gir1.0-clutter-1.0 python-encutils x11proto-kb-dev libdvbpsi5 grub-pc libmono-system-runtime2.0-cil libavcodec52 libcurl4-openssl-dev libgssrpc4 libqt4-xmlpatterns libqt4-sql-sqlite libtre4 python-epsilon
  gstreamer0.10-gnonlin libx264-85 libpigment0.3-11 librecode0 libvlc2 python-pgm x11proto-input-dev gstreamer0.10-ffmpeg libenca0 rtkit python-clientform libibus-qt1 vlc-nox libqtcore4 libgoocanvas-common libreadline5 python-storm
  libmatroska0 libgme0 libidn11-dev libxerces-c28 freepats libiptcdata0 gir1.0-gstreamer-0.10 python-mechanize liba52-0.7.4 gir1.0-gtk-2.0 gir1.0-freedesktop libpostproc51 python-tagpy libdate-calc-perl python-sqlite gir1.0-pango-1.0
  libqt4-sql libwildmidi0 ubuntu-mono python-appindicator liborc-0.4-0 python-twisted-web2 libgsm1 libdvdnav4 python-configobj libcarp-clan-perl os-prober libdvdread4 libqt4-xml docbook-xsl-doc-html libtext-glob-perl
  libschroedinger-1.0-0 libtotem-plparser17 libavformat52 libdc1394-22 libqt4-assistant libkate1 libcdaudio1 libmimic0 libkadm5clnt-mit7 libcap-ng0 libsidplay1 libkadm5srv-mit7 libupower-glib1 libfaad-dev libsoundtouch1c2 libmad0
  libdb4.6 libtommath0 libid3tag0 xsel python-pexpect libopencore-amrnb0 vlc-data kdelibs5-data libtar libkdb5-4 kdelibs-data libcelt0-0 libdirac-encoder0 libboost-regex1.40.0 libxmlrpc-c3 libqt4-sql-mysql grub-common liblua50
  krb5-multidev libvlccore2 python-pysqlite2 libvcdinfo0 libxmlrpc-core-c3 libebml0 libgmime2.4-cil libmpcdec3 python-gpod libopencore-amrwb0 python-twill x11proto-core-dev adium-theme-ubuntu python-cssutils libdigest-hmac-perl
  libxdmcp-dev libpthread-stubs0-dev libofa0 libmpeg2-4 libmms0 libbit-vector-perl python-pyasn1 python-pyparsing libfaac0 libfaad2 libldap2-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  acpi-support acpid aisleriot alsa-base alsa-utils anacron anymeal apparmor apparmor-utils apport apport-gtk aptdaemon apturl at at-spi automoc avahi-daemon avahi-utils bluetooth bluez bluez-cups bluez-utils boxee brasero
  brasero-common brltty brltty-x11 bsd-mailx capplets-data checkbox checkbox-gtk clamav clamav-base clamav-freshclam clamtk compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins
  compizconfig-backend-gconf computer-janitor-gtk console-setup consolekit couchdb-bin cron cryptsetup cups cups-driver-gutenprint dbus dbus-x11 desktopcouch dmsetup e2fsprogs empathy eog erlang-base erlang-crypto erlang-inets
  erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl evince evolution-data-server evolution-webcal f-spot file-roller firefox firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support
  firefox-branding firefox-gnome-support flashplugin-installer foo2zjs foomatic-db foomatic-db-engine friendly-recovery ftp gbrainy gcalctool gconf-defaults-service gconf-editor gconf2 gconf2-common gdebi gdm gedit getlibs
  ghostscript-cups ghostscript-x gimp gir1.0-gconf-2.0 gksu glchess glines gnect gnibbles gnobots2 gnome-about gnome-applets-data gnome-bluetooth gnome-codec-install gnome-disk-utility gnome-games gnome-games-common gnome-keyring
  gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-nettool gnome-orca gnome-panel-data gnome-power-manager gnome-screensaver gnome-session-bin gnome-session-canberra gnome-settings-daemon gnome-sudoku gnome-system-monitor
  gnome-system-tools gnome-terminal gnome-terminal-data gnome-user-guide gnome-user-share gnome-utils gnomine gnotravex gnotski google-chrome-beta gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gtali gucharmap gvfs gvfs-backends
  gvfs-bin gvfs-fuse hal hostname hplip hplip-cups iagno ibus ibus-m17n ibus-qt4 ibus-table ifupdown imagemagick indicator-session initramfs-tools initscripts irqbalance jockey-common jockey-gtk kbd kdelibs4c2a language-selector lftp
  libasound
```
MORE ..
```

 libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgstfarsight0.10-0 libgtkhtml-editor0 libgtkhtml3.14-19 libgweather-common libgweather1 libice6 liblpint-bonobo0 libm17n-0 libmagickcore2 libmagickcore2-extra libmagickwand2
  libmetacity-private0 libnet-dbus-perl libnss-mdns liboobs-1-4 libpanel-applet2-0 libphonon4 libpolkit-gtk-1-0 libpulse-browse0 libpulse-mainloop-glib0 libpulse0 libpurple0 libqt3-mt libqt4-designer libqt4-dev libqt4-gui libqt4-help
  libqt4-multimedia libqt4-opengl libqt4-opengl-dev libqt4-qt3support libqt4-scripttools libqt4-svg libqt4-webkit libqtgui4 librpc-xml-perl libsdl-gfx1.2-4 libsdl-image1.2 libsdl-mixer1.2 libsdl-net1.2 libsdl-ttf2.0-0 libsdl1.2debian
  libsdl1.2debian-pulseaudio libseed0 libsm6 libsmpeg0 libsoup-gnome2.4-1 libstartup-notification0 libtelepathy-farsight0 libubuntuone-1.0-1 libwebkit-1.0-2 libwnck22 libwww-perl libx11-dev libxau-dev libxaw7 libxcb1-dev libxklavier16
  libxml-parser-perl libxml-sax-expat-perl libxml-twig-perl libxml-xpath-perl libxmu6 libxres1 libxss1 libxt6 libxtst6 libxvmc1 libxxf86dga1 light-themes lightsoff linux-generic linux-image-2.6.32-16-generic
  linux-image-2.6.32-17-generic linux-image-2.6.32-18-generic linux-image-2.6.32-19-generic linux-image-generic linux-sound-base logrotate m17n-contrib m17n-db media-player-info mesa-common-dev metacity metacity-common
  module-init-tools moovida moovida-plugins-bad moovida-plugins-good moovida-plugins-ugly mountall mousetweaks nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share netbase network-manager network-manager-gnome
  network-manager-pptp network-manager-pptp-gnome notify-osd nspluginwrapper ntfs-3g ntpdate obex-data-server onboard openoffice.org-base-core openoffice.org-calc openoffice.org-core openoffice.org-draw openoffice.org-emailmerge
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-gb openoffice.org-help-en-us openoffice.org-impress openoffice.org-math openoffice.org-writer openprinting-ppds openssh-server pcmciautils pitivi plymouth plymouth-label
  plymouth-theme-fade-in plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text plymouth-x11 pm-utils pm-utils-powersave-policy policykit-1 policykit-1-gnome postfix powermgmt-base ppp pppconfig pppoeconf pptp-linux procps pulseaudio
  pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils pxljr python-aptdaemon python-aptdaemon-gtk python-desktopcouch python-desktopcouch-records python-farsight
  python-gconf python-gnome2 python-gnomeapplet python-papyon python-pyatspi python-speechd python-ubuntuone python-uno python-virtkey python-webkit qbittorrent quadrapassel rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins
  rhythmbox-ubuntuone-music-store rsyslog samba screen-resolution-extra screensaver-default-images seahorse seed simple-scan software-center software-properties-gtk speech-dispatcher splix sreadahead swell-foop
  system-config-printer-common system-config-printer-gnome system-tools-backends telepathy-butterfly telepathy-haze telepathy-salut telnet tomboy totem totem-common totem-mozilla totem-plugins transmission-gtk tsclient ubufox
  ubuntu-artwork ubuntu-docs ubuntu-minimal ubuntu-standard ubuntu-system-service ubuntu-wallpapers ubuntuone-client-gnome udev udisks ufw update-manager update-notifier upower upstart ureadahead usb-creator-common usb-creator-gtk
  util-linux vinagre vino vlc vlc-plugin-pulse wesnoth-core wesnoth-httt wesnoth-tsg wesnoth-ttb wireless-crda x-ttcidfont-conf x11-apps x11-common x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils xfonts-100dpi
  xfonts-75dpi xfonts-base xfonts-encodings xfonts-mathml xfonts-scalable xfonts-utils xinit xorg xscreensaver-data xscreensaver-gl xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-i128 xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage xserver-xorg-video-siliconmotion
  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vmware xserver-xorg-video-voodoo xterm
  xtrans-dev xulrunner-1.9.1 xulrunner-1.9.2 yelp
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  e2fsprogs util-linux (due to e2fsprogs) hostname upstart (due to hostname)
0 upgraded, 0 newly installed, 497 to remove and 0 not upgraded.
After this operation, 2,150MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'


```


Thanks for any pointers on this.  I just wanted to remove plymouth and see what would happen.

I am sort of watching this bug: [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/533135](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/533135)

thanks to anyone for pointers on uninstalling plymouth.

---

### Post by gare on 2010-04-04
I have submitted my problem to launchpad:

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/555263](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/555263)

---

### Post by jjcv on 2010-04-04
Had a similar problem.  Try the fololwing:

[INDENT]ctrl-alt-F5[/INDENT]

Login and then do the following:

[INDENT]sudo aptitude update[/INDENT]

[INDENT]sudo aptitude safe-upgrade[/INDENT]

then finally

[INDENT]sudo aptitude full-upgrade[/INDENT]

A lot of stuff got deleted and reinstalled through this process and eventually I was able to login again.

---

### Post by gare on 2010-04-04
Thanks ! 

Will do.

Was reading a little about how aptitude  and apt-get differ ....

> 
>man apt-get
 apt-get - APT package handling utility -- command-line interface

and
>man aptitude

aptitude - high-level interface to the package manager


I have been doing 
> 
sudo apt-get update 
and
sudo apt-get upgrade 

all weekend hoping that the fix would come through ...

will report back ...

---

### Post by gare on 2010-04-04
alas, no joy in mudville.  I am all up to date.


> 

live@live-desktop:~$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

live@live-desktop:~$ sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done



---

### Post by gare on 2010-04-04
reading the post about status of plymouth I tried:


```
sudo mv -f /bin/plymouth /bin/plymouth_bkup

& tried to log in

Now I can see this message:

getpwuid_r(): failed due to unknown user id (0)
could not write bytes: broken pipe ...... could not write bytes: broken pipe ......could not write bytes: broken pipe ......could not write bytes: broken pipe ......

and see 5 blinking dots ...
```

---

### Post by gare on 2010-04-13
I reinstalled Beta 2 from scratch & am now greatly enjoying Lucid.
Can log in.

Works great.

Seeing some lag on VLC / Media players , but look forward to that being fixed.

---

