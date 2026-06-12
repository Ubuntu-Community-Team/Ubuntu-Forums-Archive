---
title: "Upgrade from 18 to 22 and stills says 742 updates can be applied immediately."
date: 2023-11-09
forum: Installation &amp; Upgrades
---

### Post by Raymond Day on 2023-11-09
I got up do do a lot of updates taking days. But it will still say 742 updates can be installed.

Here is the command line to show this:

```
root@cardboard's password:
Welcome to Ubuntu 22.04.3 LTS (GNU/Linux 5.15.0-88-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

Expanded Security Maintenance for Infrastructure is not enabled.

742 updates can be applied immediately.
To see these additional updates run: apt list --upgradable

Enable ESM Infra to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status


5 updates could not be installed automatically. For more details,
see /var/log/unattended-upgrades/unattended-upgrades.log
Last login: Wed Nov  8 20:45:23 2023 from 192.168.86.92
root@cardboard:~# apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@cardboard:~# apt list --upgradable
Listing... Done
root@cardboard:~# apt full-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@cardboard:~# apt dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@cardboard:~#
```

Been working at this a lot and reboot and it all ways says that's lots of updates but then **0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.**

How can I fix this maybe is is all upgraded but it just says that number. Something is messed up.

-Raymond Day

---

### Post by yancek on 2023-11-09
How did you upgrade from 18.04.  It is EOL so see the link below with instructions on it as you cannot upgrade directly to 22.04 from 18.04.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by MAFoElffen on 2023-11-09
If you did 
```

apt list --upgradable

```
What updates does it show?

---

### Post by Raymond Day on 2023-11-10
```
root@cardboard:~# apt list --upgradable
Listing... Done
root@cardboard:~#
```

So it comes back with showing no upgrades.

I did a upgrade by when booting it it said can upgrade and gave the command and it took all day.

-Raymond Day

---

### Post by Raymond Day on 2023-11-10
I just did a command that looked like it will install a lot but I think it wants to install the desktop this is a server. It looks like this:

```
root@cardboard:~# apt install update-manager
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  apg apport apport-gtk aptdaemon aptdaemon-data bluez bolt bubblewrap cheese-common cracklib-runtime cups-pk-helper
  dconf-cli dns-root-data dnsmasq-base docbook-xml enchant-2 evolution-data-server evolution-data-server-common gdb
  gdm3 gedit gedit-common gir1.2-accountsservice-1.0 gir1.2-adw-1 gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-freedesktop
  gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdesktopenums-3.0 gir1.2-gdkpixbuf-2.0 gir1.2-gdm-1.0 gir1.2-geoclue-2.0
  gir1.2-gnomebluetooth-3.0 gir1.2-gnomedesktop-3.0 gir1.2-goa-1.0 gir1.2-graphene-1.0 gir1.2-gstreamer-1.0
  gir1.2-gtk-3.0 gir1.2-gtk-4.0 gir1.2-gtksource-4 gir1.2-gweather-3.0 gir1.2-handy-1 gir1.2-harfbuzz-0.0
  gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-4.0 gir1.2-json-1.0 gir1.2-mutter-10 gir1.2-nm-1.0 gir1.2-nma-1.0
  gir1.2-notify-0.7 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-polkit-1.0 gir1.2-rsvg-2.0 gir1.2-secret-1 gir1.2-snapd-1
  gir1.2-soup-2.4 gir1.2-upowerglib-1.0 gir1.2-vte-2.91 gir1.2-webkit2-4.0 gir1.2-wnck-3.0 gkbd-capplet
  gnome-bluetooth-3-common gnome-bluetooth-common gnome-control-center gnome-control-center-data
  gnome-control-center-faces gnome-desktop3-data gnome-keyring gnome-menus gnome-online-accounts gnome-remote-desktop
  gnome-session-bin gnome-session-common gnome-settings-daemon gnome-settings-daemon-common gnome-shell
  gnome-shell-common gnome-startup-applications gnome-user-docs gstreamer1.0-clutter-3.0 gstreamer1.0-pipewire ibus
  ibus-data ibus-gtk ibus-gtk3 ibus-gtk4 im-config language-selector-common language-selector-gnome libadwaita-1-0
  libayatana-appindicator3-1 libayatana-ido3-0.4-0 libayatana-indicator3-7 libbabeltrace1 libbluetooth3
  libboost-regex1.74.0 libc6-dbg libcairo-gobject-perl libcairo-perl libcairo-script-interpreter2 libcamel-1.2-63
  libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcheese-gtk25 libcheese8
  libclutter-1.0-0 libclutter-1.0-common libclutter-gst-3.0-0 libclutter-gtk-1.0-0 libcogl-common libcogl-pango20
  libcogl-path20 libcogl20 libcolord-gtk1 libcrack2 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdebuginfod-common
  libdebuginfod1 libebackend-1.2-10 libebook-1.2-20 libebook-contacts-1.2-3 libecal-2.0-1 libedata-book-1.2-26
  libedata-cal-2.0-1 libedataserver-1.2-26 libedataserverui-1.2-3 libenchant-2-2 libextutils-depends-perl
  libfreerdp-client2-2 libfreerdp-server2-2 libfreerdp2-2 libgdata-common libgdata22 libgdm1 libgee-0.8-2
  libgeoclue-2-0 libgeocode-glib0 libgjs0g libglib-object-introspection-perl libglib-perl libgnome-autoar-0-0
  libgnome-bluetooth-3.0-13 libgnome-bluetooth13 libgnome-desktop-3-19 libgnomekbd-common libgnomekbd8 libgoa-1.0-0b
  libgoa-1.0-common libgoa-backend-1.0-1 libgsound0 libgspell-1-2 libgspell-1-common libgtk-4-1 libgtk-4-bin
  libgtk-4-common libgtk3-perl libgtksourceview-4-0 libgtksourceview-4-common libgtop-2.0-11 libgtop2-common
  libgupnp-av-1.0-3 libgupnp-dlna-2.0-4 libgweather-3-16 libgweather-common libhandy-1-0 libhyphen0 libibus-1.0-5
  libical3 libipt2 libjavascriptcoregtk-4.0-18 libmanette-0.2-0 libmediaart-2.0-0 libmozjs-91-0 libmutter-10-0 libndp0
  libnm0 libnma-common libnma0 libpam-gnome-keyring libpeas-1.0-0 libpeas-common libphonenumber8 libpipewire-0.3-0
  libpipewire-0.3-common libpipewire-0.3-modules libprotobuf23 libpulse-mainloop-glib0 libpwquality-common
  libpwquality1 librest-0.7-0 librygel-core-2.6-2 librygel-db-2.6-2 librygel-renderer-2.6-2 librygel-server-2.6-2
  libsmbclient libsoup-gnome2.4-1 libsource-highlight-common libsource-highlight4v5 libspa-0.2-modules
  libstartup-notification0 libteamdctl0 libvncserver1 libwebkit2gtk-4.0-37 libwhoopsie-preferences0 libwhoopsie0
  libwinpr2-2 libwnck-3-0 libwnck-3-common libwoff1 libwpe-1.0-1 libwpebackend-fdo-1.0-1 libxatracker2 libxcb-res0
  libxcvt0 libxfont2 libxkbregistry0 libxklavier16 libxres1 libxvmc1 libyelp0 mobile-broadband-provider-info
  mutter-common network-manager network-manager-gnome network-manager-pptp pipewire pipewire-bin
  pipewire-media-session power-profiles-daemon pptp-linux pulseaudio-module-bluetooth python3-apport python3-aptdaemon
  python3-aptdaemon.gtk3widgets python3-cairo python3-click python3-colorama python3-cups python3-cupshelpers
  python3-dateutil python3-debconf python3-debian python3-defer python3-gi-cairo python3-ibus-1.0
  python3-macaroonbakery python3-nacl python3-problem-report python3-protobuf python3-pymacaroons python3-rfc3339
  python3-systemd python3-tz python3-xkit rygel sgml-data software-properties-gtk sound-theme-freedesktop
  switcheroo-control system-config-printer system-config-printer-common system-config-printer-udev
  ubuntu-advantage-desktop-daemon ubuntu-docs ubuntu-drivers-common ubuntu-release-upgrader-gtk ubuntu-session
  ubuntu-wallpapers ubuntu-wallpapers-jammy update-notifier update-notifier-common wamerican whoopsie
  whoopsie-preferences x11-xkb-utils xcvt xdg-dbus-proxy xdg-desktop-portal xdg-desktop-portal-gtk xfonts-base
  xfonts-encodings xfonts-utils xserver-common xserver-xephyr xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-libinput xserver-xorg-input-wacom xserver-xorg-legacy xserver-xorg-video-all
  xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-nouveau xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-vesa
  xserver-xorg-video-vmware xwayland yaru-theme-gnome-shell yelp yelp-xsl zenity zenity-common
Suggested packages:
  docbook docbook-dsssl docbook-xsl docbook-defguide evolution gdb-doc gdbserver orca libpam-fprintd libpam-sss
  libpam-pkcs11 gedit-plugins gnome-software | gnome-packagekit gnome-user-share realmd gstreamer1.0-pulseaudio
  libcanberra-gtk-module usbguard gir1.2-malcontent-0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gnome-backgrounds gnome-shell-extension-prefs chrome-gnome-shell ibus-clutter ibus-doc libfont-freetype-perl
  libcanberra-gtk0 libenchant-2-voikko freerdp2-x11 libxml-libxml-perl gvfs libgtk-4-media-gstreamer
  | libgtk-4-media-ffmpeg gstreamer1.0-alsa avahi-autoipd libteam-utils network-manager-openconnect-gnome
  network-manager-openvpn-gnome network-manager-vpnc-gnome network-manager-pptp-gnome python-nacl-doc rygel-playbin
  rygel-preferences rygel-ruih rygel-tracker tumbler perlsgml w3-recs opensp libxml2-utils gnome-software python3-smbc
  python3-aptdaemon.pkcompat ubuntu-wallpapers-karmic ubuntu-wallpapers-lucid ubuntu-wallpapers-maverick
  ubuntu-wallpapers-natty ubuntu-wallpapers-oneiric ubuntu-wallpapers-precise ubuntu-wallpapers-quantal
  ubuntu-wallpapers-raring ubuntu-wallpapers-saucy ubuntu-wallpapers-trusty ubuntu-wallpapers-utopic
  ubuntu-wallpapers-vivid ubuntu-wallpapers-wily ubuntu-wallpapers-xenial ubuntu-wallpapers-yakkety
  ubuntu-wallpapers-zesty ubuntu-wallpapers-artful ubuntu-wallpapers-bionic ubuntu-wallpapers-cosmic
  ubuntu-wallpapers-disco ubuntu-wallpapers-eoan ubuntu-wallpapers-focal ubuntu-wallpapers-groovy
  ubuntu-wallpapers-hirsute ubuntu-wallpapers-impish gir1.2-dbusmenu-glib-0.4 gir1.2-unity-5.0 evince
  xdg-desktop-portal-gnome xfonts-100dpi | xfonts-75dpi xfonts-scalable xinput firmware-amd-graphics
  xserver-xorg-video-r128 xserver-xorg-video-mach64 firmware-misc-nonfree
The following NEW packages will be installed:
  apg apport apport-gtk aptdaemon aptdaemon-data bluez bolt bubblewrap cheese-common cracklib-runtime cups-pk-helper
  dconf-cli dns-root-data dnsmasq-base docbook-xml enchant-2 evolution-data-server evolution-data-server-common gdb
  gdm3 gedit gedit-common gir1.2-accountsservice-1.0 gir1.2-adw-1 gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-freedesktop
  gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdesktopenums-3.0 gir1.2-gdkpixbuf-2.0 gir1.2-gdm-1.0 gir1.2-geoclue-2.0
  gir1.2-gnomebluetooth-3.0 gir1.2-gnomedesktop-3.0 gir1.2-goa-1.0 gir1.2-graphene-1.0 gir1.2-gstreamer-1.0
  gir1.2-gtk-3.0 gir1.2-gtk-4.0 gir1.2-gtksource-4 gir1.2-gweather-3.0 gir1.2-handy-1 gir1.2-harfbuzz-0.0
  gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-4.0 gir1.2-json-1.0 gir1.2-mutter-10 gir1.2-nm-1.0 gir1.2-nma-1.0
  gir1.2-notify-0.7 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-polkit-1.0 gir1.2-rsvg-2.0 gir1.2-secret-1 gir1.2-snapd-1
  gir1.2-soup-2.4 gir1.2-upowerglib-1.0 gir1.2-vte-2.91 gir1.2-webkit2-4.0 gir1.2-wnck-3.0 gkbd-capplet
  gnome-bluetooth-3-common gnome-bluetooth-common gnome-control-center gnome-control-center-data
  gnome-control-center-faces gnome-desktop3-data gnome-keyring gnome-menus gnome-online-accounts gnome-remote-desktop
  gnome-session-bin gnome-session-common gnome-settings-daemon gnome-settings-daemon-common gnome-shell
  gnome-shell-common gnome-startup-applications gnome-user-docs gstreamer1.0-clutter-3.0 gstreamer1.0-pipewire ibus
  ibus-data ibus-gtk ibus-gtk3 ibus-gtk4 im-config language-selector-common language-selector-gnome libadwaita-1-0
  libayatana-appindicator3-1 libayatana-ido3-0.4-0 libayatana-indicator3-7 libbabeltrace1 libbluetooth3
  libboost-regex1.74.0 libc6-dbg libcairo-gobject-perl libcairo-perl libcairo-script-interpreter2 libcamel-1.2-63
  libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcheese-gtk25 libcheese8
  libclutter-1.0-0 libclutter-1.0-common libclutter-gst-3.0-0 libclutter-gtk-1.0-0 libcogl-common libcogl-pango20
  libcogl-path20 libcogl20 libcolord-gtk1 libcrack2 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdebuginfod-common
  libdebuginfod1 libebackend-1.2-10 libebook-1.2-20 libebook-contacts-1.2-3 libecal-2.0-1 libedata-book-1.2-26
  libedata-cal-2.0-1 libedataserver-1.2-26 libedataserverui-1.2-3 libenchant-2-2 libextutils-depends-perl
  libfreerdp-client2-2 libfreerdp-server2-2 libfreerdp2-2 libgdata-common libgdata22 libgdm1 libgee-0.8-2
  libgeoclue-2-0 libgeocode-glib0 libgjs0g libglib-object-introspection-perl libglib-perl libgnome-autoar-0-0
  libgnome-bluetooth-3.0-13 libgnome-bluetooth13 libgnome-desktop-3-19 libgnomekbd-common libgnomekbd8 libgoa-1.0-0b
  libgoa-1.0-common libgoa-backend-1.0-1 libgsound0 libgspell-1-2 libgspell-1-common libgtk-4-1 libgtk-4-bin
  libgtk-4-common libgtk3-perl libgtksourceview-4-0 libgtksourceview-4-common libgtop-2.0-11 libgtop2-common
  libgupnp-av-1.0-3 libgupnp-dlna-2.0-4 libgweather-3-16 libgweather-common libhandy-1-0 libhyphen0 libibus-1.0-5
  libical3 libipt2 libjavascriptcoregtk-4.0-18 libmanette-0.2-0 libmediaart-2.0-0 libmozjs-91-0 libmutter-10-0 libndp0
  libnm0 libnma-common libnma0 libpam-gnome-keyring libpeas-1.0-0 libpeas-common libphonenumber8 libpipewire-0.3-0
  libpipewire-0.3-common libpipewire-0.3-modules libprotobuf23 libpulse-mainloop-glib0 libpwquality-common
  libpwquality1 librest-0.7-0 librygel-core-2.6-2 librygel-db-2.6-2 librygel-renderer-2.6-2 librygel-server-2.6-2
  libsmbclient libsoup-gnome2.4-1 libsource-highlight-common libsource-highlight4v5 libspa-0.2-modules
  libstartup-notification0 libteamdctl0 libvncserver1 libwebkit2gtk-4.0-37 libwhoopsie-preferences0 libwhoopsie0
  libwinpr2-2 libwnck-3-0 libwnck-3-common libwoff1 libwpe-1.0-1 libwpebackend-fdo-1.0-1 libxatracker2 libxcb-res0
  libxcvt0 libxfont2 libxkbregistry0 libxklavier16 libxres1 libxvmc1 libyelp0 mobile-broadband-provider-info
  mutter-common network-manager network-manager-gnome network-manager-pptp pipewire pipewire-bin
  pipewire-media-session power-profiles-daemon pptp-linux pulseaudio-module-bluetooth python3-apport python3-aptdaemon
  python3-aptdaemon.gtk3widgets python3-cairo python3-click python3-colorama python3-cups python3-cupshelpers
  python3-dateutil python3-debconf python3-debian python3-defer python3-gi-cairo python3-ibus-1.0
  python3-macaroonbakery python3-nacl python3-problem-report python3-protobuf python3-pymacaroons python3-rfc3339
  python3-systemd python3-tz python3-xkit rygel sgml-data software-properties-gtk sound-theme-freedesktop
  switcheroo-control system-config-printer system-config-printer-common system-config-printer-udev
  ubuntu-advantage-desktop-daemon ubuntu-docs ubuntu-drivers-common ubuntu-release-upgrader-gtk ubuntu-session
  ubuntu-wallpapers ubuntu-wallpapers-jammy update-manager update-notifier update-notifier-common wamerican whoopsie
  whoopsie-preferences x11-xkb-utils xcvt xdg-dbus-proxy xdg-desktop-portal xdg-desktop-portal-gtk xfonts-base
  xfonts-encodings xfonts-utils xserver-common xserver-xephyr xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-libinput xserver-xorg-input-wacom xserver-xorg-legacy xserver-xorg-video-all
  xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-nouveau xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-vesa
  xserver-xorg-video-vmware xwayland yaru-theme-gnome-shell yelp yelp-xsl zenity zenity-common
0 upgraded, 312 newly installed, 0 to remove and 0 not upgraded.
Need to get 143 MB of archives.
After this operation, 453 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```

I pressed n because I think it wants to install the desktop. It that right? Or will it install what it says are updates when booting up?

Thank you.

-Raymond Day

---

### Post by MAFoElffen on 2023-11-10
No. Do not do that!!! 

update-manager is a "GUI" application. That is why it would pull in a desktop and graphics engine.

On my servers, if I want something else, a little more, then I'll install aptitude. That is text console based, and has been around forever.

Do this to run the motd manually from a terminal:
```

sudo run-parts /etc/update-motd.d/

```
That will run the scripts to build the Message Of the Day (motd)... and look for any errors in the output...

There was a bug sometime back when people would see this:
> 
/etc/update-motd.d//90-updates-available: 7: /usr/share/update-notifier/notify-updates-outdated: not found run-parts: /etc/update-motd.d//90-updates-available exited with return code 127
That leads the diagnostic trail to this:
```

apt list update-notifier* --installed

```
The output from that should show both 'update-notifier' and 'update-notifier-common' as installed... With that old bug, from back in Server 18.04 LTS, sometimes the package 'update-notifier-common' was missing...

If it is, then do
```

sudo apt install -y update-notifier-common

```
If it returns another error from those packages in the above output, then do
```

sudo apt install --reinstall -y update-notifier update-notifier-common

```
Then retest...

---

### Post by Raymond Day on 2023-11-13
Thank you that worked I rebooted and it don't say they is any updates now.

I log on it and then looked at the LCD and looks like it install the Desktop now.

-Raymond Day

---

