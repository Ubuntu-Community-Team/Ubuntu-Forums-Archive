---
title: "apt-get update &amp;&amp; dist-upgrade wants to install &gt; 500 packages and install X (server)"
date: 2014-12-23
forum: Installation &amp; Upgrades
---

### Post by matonga on 2014-12-23
Hi !

Since about a week Ubuntu 14.04.1 wants to install > 500 packages (including X) when I do a apt-get update && dist-upgrade

There is no X server installed, as it is a server, I can let the update run and remove the xserver which also removes the > 500 dependencies and desktop stuff but why I Ubuntu suddenly almost trying to turn my server into a Desktop PC ? I did no special installations and got this on about 10 servers now...

thanks

---

### Post by -Marco on 2014-12-23
> **matonga said:**
> Hi !

Since about a week Ubuntu 14.04.1 wants to install > 500 packages (including X) when I do a apt-get update && dist-upgrade

There is no X server installed, as it is a server, I can let the update run and remove the xserver which also removes the > 500 dependencies and desktop stuff but why I Ubuntu suddenly almost trying to turn my server into a Desktop PC ? I did no special installations and got this on about 10 servers now...

thanks
It's normal, man. Keep update your server.. and yes, X server is installed on every Ubuntu machines, including server (for graphics ecc.).
Ubuntu is normally developed for PC, there are some distro created especially for server.

Keep me updated about this "problem" :)

---

### Post by matonga on 2014-12-23
Hmm but I have installed the server distribution of ubuntu and never ever had this "problem". I'm only running the minimal server distro and don't want any kind of desktop stuff on the machine

Ubuntu installs a previously non-installed X server with all kind of dependencies including bluetooth and stuff, and after it has done the "updates" and installs - i remove them and everyhing is good again.. 

Very weird..

---

### Post by schragge on 2014-12-23
What would you get if you just did *apt-get upgrade* (as opposite to *apt-get dist-upgrade*)? What packages would be held back then?

---

### Post by -Marco on 2014-12-23
> **matonga said:**
> Hmm but I have installed the server distribution of ubuntu and never ever had this "problem". I'm only running the minimal server distro and don't want any kind of desktop stuff on the machine

Ubuntu installs a previously non-installed X server with all kind of dependencies including bluetooth and stuff, and after it has done the "updates" and installs - i remove them and everyhing is good again.. 

Very weird..
Have you installed this Ubuntu? [http://www.ubuntu.com/server](http://www.ubuntu.com/server)
Anyway, i reccomended to use Debian for Server. It's very slim and fast for this use and have all packages updated and it's useful to update them (all are updated for 1-2 year of usage), without problem. For this much user choose Debian for its servers.

---

### Post by matonga on 2014-12-23
Thanks ! That did the trick and just the updates are installed, not the new packages, very interesting

---

### Post by schragge on 2014-12-23
Well, that was to be expected. Citing [apt-get(8)]("http://apt-get(8)") manpage:
> 
**upgrade**
           upgrade is used to install the newest versions of all packages currently installed on the system from the sources enumerated in /etc/apt/sources.list. Packages currently installed with new versions available are retrieved and upgraded; under no circumstances are currently installed packages removed, or packages not already installed retrieved and installed. New versions of currently installed packages that cannot be upgraded without changing the install status of another package will be left at their current version.

More interesting is what packages were held back as one of those probably caused X to be installed as its dependency.

---

### Post by matonga on 2014-12-23
This happens when saying "dist-upgrade":

```
apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  libnet1
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  arping
The following NEW packages will be installed:
  acl apg aptdaemon aspell aspell-en at-spi2-core avahi-daemon avahi-utils
  bbswitch-dkms bluez cheese-common colord cracklib-runtime cups-pk-helper
  dbus-x11 dconf-cli dconf-gsettings-backend dconf-service desktop-file-utils
  dialog dictionaries-common diffstat dkms dnsmasq-base enchant
  evolution-data-server evolution-data-server-common
  evolution-data-server-online-accounts fontconfig gconf-service
  gconf-service-backend gconf2 gconf2-common gcr geoclue geoclue-ubuntu-geoip
  gettext gir1.2-atk-1.0 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0
  gir1.2-gnomebluetooth-1.0 gir1.2-gtk-3.0 gir1.2-ibus-1.0 gir1.2-notify-0.7
  gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gkbd-capplet glib-networking
  glib-networking-common glib-networking-services gnome-bluetooth
  gnome-control-center-shared-data gnome-desktop3-data gnome-icon-theme
  gnome-icon-theme-symbolic gnome-keyring gnome-menus gnome-power-manager
  gnome-screensaver gnome-session-bin gnome-settings-daemon-schemas
  gnome-user-guide gnome-user-share gsettings-desktop-schemas
  gsettings-ubuntu-schemas gstreamer0.10-pulseaudio gstreamer1.0-clutter
  gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-x gvfs
  gvfs-backends gvfs-common gvfs-daemons gvfs-libs hardening-includes
  hicolor-icon-theme humanity-icon-theme hunspell-en-us hwdata ibus ibus-gtk
  ibus-gtk3 im-config indicator-applet indicator-application
  indicator-bluetooth indicator-datetime indicator-keyboard indicator-messages
  indicator-power indicator-session indicator-sound intltool-debian
  iputils-arping lib32gcc1 libaa1 libaccount-plugin-1.0-0
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-glib0
  libaccounts-qt5-1 libappindicator3-1 libapt-pkg-perl libarchive-zip-perl
  libarchive13 libasound2 libasound2-data libasound2-plugins libaspell15
  libasprintf-dev libasyncns0 libatasmart4 libatk-bridge2.0-0 libatk1.0-0
  libatk1.0-data libatspi2.0-0 libauthen-sasl-perl libautodie-perl
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core7
  libavahi-glib1 libavc1394-0 libbluetooth3 libc6-i386 libcaca0
  libcairo-gobject2 libcairo2 libcamel-1.2-45 libcanberra-gtk3-0
  libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcdio-cdda1
  libcdio-paranoia1 libcdio13 libcdparanoia0 libcheese-gtk23 libcheese7
  libclone-perl libclutter-1.0-0 libclutter-1.0-common libclutter-gst-2.0-0
  libclutter-gtk-1.0-0 libcogl-common libcogl-pango15 libcogl15 libcolord1
  libcolorhug1 libcrack2 libcroco3 libcuda1-331-updates libcups2 libdaemon0
  libdatrie1 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdconf1
  libdigest-hmac-perl libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdv4
  libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16
  libedata-book-1.2-20 libedata-cal-1.2-23 libedataserver-1.2-18 libegl1-mesa
  libegl1-mesa-drivers libelfg0 libemail-valid-perl libenchant1c2a libexif12
  libfftw3-single3 libfile-basedir-perl libflac8 libfontenc1 libgbm1
  libgconf-2-4 libgcr-ui-3-1 libgdata-common libgdata13 libgdk-pixbuf2.0-0
  libgdk-pixbuf2.0-common libgee2 libgeoclue0 libgettextpo-dev libgettextpo0
  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libgles2-mesa libglib2.0-bin
  libglu1-mesa libgnome-bluetooth11 libgnome-desktop-3-7
  libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0
  libgnomekbd-common libgnomekbd8 libgoa-1.0-0b libgoa-1.0-common libgphoto2-6
  libgphoto2-l10n libgphoto2-port10 libgraphite2-3
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base1.0-0
  libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0
  libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libgtop2-7 libgtop2-common libgudev-1.0-0 libgusb2
  libgweather-3-6 libgweather-common libharfbuzz-icu0 libharfbuzz0b
  libhunspell-1.3-0 libibus-1.0-5 libical1 libice6 libido3-0.1-0 libiec61883-0
  libieee1284-3 libimobiledevice4 libindicator3-7 libio-pty-perl
  libio-socket-inet6-perl libio-socket-ssl-perl libipc-run-perl
  libipc-system-simple-perl libjack-jackd2-0 libjasper1
  libjavascriptcoregtk-3.0-0 libjson-glib-1.0-0 libjson-glib-1.0-common
  liblcms2-2 libldb1 liblightdm-gobject-1-0 liblist-moreutils-perl libllvm3.4
  liblzo2-2 libmailtools-perl libmbim-glib0 libmm-glib0 libmnl0 libmtdev1
  libmtp-common libmtp-runtime libmtp9 libnet-dns-perl libnet-domain-tld-perl
  libnet-ip-perl libnet-libidn-perl libnet-smtp-ssl-perl libnet-ssleay-perl
  libnetfilter-conntrack3 libnettle4 libnl-route-3-200 libnm-glib-vpn1
  libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify4 libnspr4
  libnss-mdns libnss3 libnss3-nssdb libntdb1 liboauth0 libogg0 libopenobex1
  libopenvg1-mesa liborc-0.4-0 libp11-kit-gnome-keyring libpackagekit-glib2-16
  libpam-gnome-keyring libpanel-applet-4-0 libpango-1.0-0 libpango1.0-0
  libpangocairo-1.0-0 libpangoft2-1.0-0 libpangox-1.0-0 libpangoxft-1.0-0
  libperlio-gzip-perl libpixman-1-0 libplist1 libproxy1
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libpwquality-common
  libpwquality1 libqmi-glib0 libqt5core5a libqt5dbus5 libqt5gui5
  libqt5network5 libqt5opengl5 libqt5positioning5 libqt5printsupport5
  libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite
  libqt5test5 libqt5webkit5 libqt5widgets5 libqt5xml5 libraw1394-11
  librest-0.7-0 librsvg2-2 librsvg2-common libsamplerate0 libsane
  libsane-common libsecret-1-0 libsecret-common libshout3 libsignon-extension1
  libsignon-glib1 libsignon-plugins-common1 libsignon-qt5-1 libsm6
  libsmbclient libsndfile1 libsocket6-perl libsoup-gnome2.4-1 libsoup2.4-1
  libspeex1 libspeexdsp1 libsub-identify-perl libsystemd-journal0
  libtag1-vanilla libtag1c2a libtalloc2 libtdb1 libtevent0
  libtext-levenshtein-perl libthai-data libthai0 libtheora0 libtimezonemap1
  libtxc-dxtn-s2tc0 libudisks2-0 libunistring0 libunity-control-center1
  libupower-glib1 liburi-perl liburl-dispatcher1 libusbmuxd2 libv4l-0
  libv4lconvert0 libvdpau1 libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a
  libvorbisenc2 libvorbisfile3 libwacom-common libwacom2 libwavpack1
  libwayland-client0 libwayland-cursor0 libwayland-egl1-mesa
  libwayland-server0 libwbclient0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
  libwebp5 libx11-xcb1 libxaw7 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0
  libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-present0 libxcb-randr0
  libxcb-render-util0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1
  libxcb-util0 libxcb-xfixes0 libxcb-xkb1 libxcomposite1 libxcursor1
  libxdamage1 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1
  libxkbcommon-x11-0 libxkbcommon0 libxkbfile1 libxklavier16 libxmu6
  libxrandr2 libxrender1 libxshmfence1 libxslt1.1 libxt6 libxtst6 libxv1
  libxxf86dga1 libxxf86vm1 libyelp0 lightdm lintian linux-headers-3.13.0-43
  linux-headers-3.13.0-43-generic linux-image-3.13.0-43-generic
  linux-image-extra-3.13.0-43-generic mobile-broadband-provider-info
  modemmanager mousetweaks nautilus-data network-manager network-manager-gnome
  network-manager-pptp network-manager-pptp-gnome notification-daemon
  nvidia-331-updates nvidia-331-updates-uvm nvidia-opencl-icd-331-updates
  nvidia-prime nvidia-settings obex-data-server obexd-client p11-kit
  p11-kit-modules patchutils policykit-1-gnome pptp-linux pulseaudio
  pulseaudio-module-x11 pulseaudio-utils python-cairo python-cups
  python-cupshelpers python-dbus python-dbus-dev python-gi python-gnomekeyring
  python-gobject python-gobject-2 python-gtk2 python-libxml2 python-notify
  python-pycurl python-smbc python-talloc python3-aptdaemon
  python3-aptdaemon.pkcompat python3-defer python3-pkg-resources python3-xdg
  python3-xkit rtkit samba-libs screen-resolution-extra session-migration
  signon-keyring-extension signon-plugin-oauth2 signon-ui signond
  sound-theme-freedesktop system-config-printer-common
  system-config-printer-gnome system-config-printer-udev t1utils
  ubuntu-system-service udisks2 unity-control-center
  unity-control-center-signon unity-greeter unity-settings-daemon upower
  usb-modeswitch usb-modeswitch-data usbmuxd wamerican x11-common x11-utils
  x11-xkb-utils xfonts-base xfonts-encodings xfonts-utils xserver-common
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom yelp yelp-xsl zenity zenity-common
The following packages have been kept back:
  libhwloc-plugins
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
  nvidia-libopencl1-331-updates
4 upgraded, 521 newly installed, 1 to remove and 1 not upgraded.
Need to get 229 MB of archives.
After this operation, 1,020 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
```


So "libhwloc-plugins" is kept back - thats the reason for the mess ?

---

### Post by schragge on 2014-12-23
No, I don't think so. Now I see it's *nvidia-libopencl1-331-updates*. The dependency chain looks like this:

nvidia-libopencl1-331-updates > nvidia-331-updates-uvm > nvidia-331-updates > [a lot of packages including X server]

Put just this package on hold with
```

sudo apt-mark hold nvidia-libopencl1-331-updates

```
then try *dist-upgrade* again.

Looks like [this change]("http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/trusty/nvidia-graphics-drivers-331-updates/trusty-security/revision/18#debian/control") caused all the mess, specifically this line in *debian/control* (added text marked in [COLOR=red]red[/COLOR]):
```

Depends: [COLOR=red]nvidia-331-updates-uvm, [/COLOR]${shlibs:Depends}, ${misc:Depends}

```
You probably should file a bug against [nvidia-graphics-drivers-331-updates]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates").

OK, I've just filed the bug myself: LP#[lpbug]1405253[/lpbug]. Please subscribe to it.

---

### Post by matonga on 2014-12-23
That worked well, everything is now as expected when I hold the package. 

Subscribed to the Bug Report too.

Thank you very much for your help.

---

### Post by oldos2er on 2014-12-24
Could you please mark the thread 'Solved' under Thread Tools at the top of the page? It will help others who might encounter the same problem.

---

### Post by deadflowr on 2014-12-24
> **-Marco said:**
> It's normal, man. Keep update your server.. and yes, X server is installed on every Ubuntu machines, including server (for graphics ecc.).


I have yet to see that.
Though I know you can install X during the installation.

But the real reason the OP has so many x-packages, is because, without realizing it, they have a whole list of gnome packages.
Gnome is a graphical desktop, so it would be suffice to say that X was installed whenever they install those gnome packages, however they install those gnome packages.
(Most likely they're from a -desktop metapackage installed somewhere along the way)

---

