---
title: "apt trouble"
date: 2015-07-20
forum: Installation &amp; Upgrades
---

### Post by painbrain2004 on 2015-07-20
hi everyone,

everytime i use apt-get to install a program this is my output:
```
matteo@matteo-dell:/var/lib/dpkg$ sudo apt-get install htop Lettura elenco dei pacchetti... FattoGenerazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
htop è già alla versione più recente.
È utile eseguire "apt-get -f install" per correggere questi problemi:
I seguenti pacchetti hanno dipendenze non soddisfatte:
 openssh-client : Dipende: libgssapi-krb5-2 (>= 1.12.1+dfsg-2) ma la versione 1.12+dfsg-2ubuntu5.1 sta per essere installata
E: Dipendenze non soddisfatte. Provare "apt-get -f install" senza pacchetti (o specificare una soluzione).
matteo@matteo-dell:/var/lib/dpkg$ 

```

and with -f install
```
matteo@matteo-dell:/var/lib/dpkg$ sudo apt-get -f install Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Correzione delle dipendenze... non riuscita.
I seguenti pacchetti hanno dipendenze non soddisfatte:
 openssh-client : Dipende: libgssapi-krb5-2 (>= 1.12.1+dfsg-2) ma la versione 1.12+dfsg-2ubuntu5.1 è installata
E: Errore, pkgProblemResolver::Resolve ha generato delle interruzioni. Questo potrebbe essere causato da pacchetti bloccati.
E: Impossibile correggere le dipendenze
matteo@matteo-dell:/var/lib/dpkg$ 

```

someone can help me? :(

---

### Post by Bashing-om on 2015-07-20
painbrain2004; Hi ! Welcome to the forum.

Most of us here communicate in English. 
I find it difficult and un-reliable to attempt to interpret your results.
Ya mind re-running them as English ?

[INDENT][INDENT]we see then what we can do
[/INDENT][/INDENT]

---

### Post by Vladlenin5000 on 2015-07-20
It's just Italian... I can translate anything ;-)

The main issue shown is the package *openssh-client* depending on*libgssapi-krb5-2* (>= 1.12.1+dfsg-2) and complaining about it.

---

### Post by Bashing-om on 2015-07-20
@Vladlenin5000; Hello again;

As my respect for your abilities ever increases :)

so:
@painbrain2004; What results:
```

sudo apt-get install --reinstall libgssapi-krb5-2

```
And we see what it takes
[INDENT][INDENT]to make the package manager happy
[/INDENT][/INDENT]

---

### Post by painbrain2004 on 2015-07-21
thx everyone, but [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install --reinstall libgssapi-krb5-2 give this error :(
```
[/FONT][/COLOR]matteo@matteo-dell:~$ sudo apt-get install --reinstall libgssapi-krb5-2Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
La reinstallazione di libgssapi-krb5-2 non è possibile, non può essere scaricato.
È utile eseguire "apt-get -f install" per correggere questi problemi:
I seguenti pacchetti hanno dipendenze non soddisfatte:
 openssh-client : Dipende: libgssapi-krb5-2 (>= 1.12.1+dfsg-2) ma la versione 1.12+dfsg-2ubuntu5.1 sta per essere installata
E: Dipendenze non soddisfatte. Provare "apt-get -f install" senza pacchetti (o specificare una soluzione).
matteo@matteo-dell:~$ 
```
"non può essere scaricato" means "it can not be downloaded"
why?

---

### Post by Bashing-om on 2015-07-21
painbrain2004; Hummm ..

Not at all an expected result.
What is the install situation ?
Please post back the output of :
```

apt-cache policy libgssapi-krb5-2

```

and let's see what tale is told.

[INDENT][INDENT]what does it take to keep
[INDENT][INDENT][INDENT]the package manager satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by painbrain2004 on 2015-07-21
i did
```
[COLOR=#555555][FONT=Monaco]sudo dpkg -r --force-depends libgssapi-krb5-2[/FONT][/COLOR]
```
and then
```
sudo apt-get -f install
```

....
apt remove ALL ubuntu-desktop and his dependances :(
i had to format...

anyways, now is ok :)

thanx everyone

---

### Post by painbrain2004 on 2015-07-21
this is the steps:
```
[COLOR=#555555][FONT=Monaco]matteo@matteo-dell:~$ sudo dpkg -r --force-depends libgssapi-krb5-2[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]dpkg: libgssapi-krb5-2:i386: problemi con le dipendenze, ma viene rimosso comunque:[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco] libdns100 dipende da libgssapi-krb5-2 (>= 1.10+dfsg~).[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco] cups-daemon dipende da libgssapi-krb5-2 (>= 1.10+dfsg~).[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco] libcurl3:i386 dipende da libgssapi-krb5-2 (>= 1.10+dfsg~).[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco] libcamel-1.2-45 dipende da libgssapi-krb5-2 (>= 1.10+dfsg~).[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco] libcups2:i386 dipende da libgssapi-krb5-2 (>= 1.10+dfsg~).[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco] libneon27-gnutls dipende da libgssapi-krb5-2 (>= 1.10+dfsg~).[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco] libcurl3-gnutls:i386 dipende da libgssapi-krb5-2 (>= 1.10+dfsg~).[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco](Lettura del database... 153823 file e directory attualmente installati.)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Rimozione di libgssapi-krb5-2:i386 (1.12+dfsg-2ubuntu5.1)...[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Elaborazione dei trigger per libc-bin (2.19-0ubuntu6.5)...[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]matteo@matteo-dell:~$ sudo apt-get install -f[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Lettura elenco dei pacchetti... Fatto[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Generazione albero delle dipendenze       [/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Lettura informazioni sullo stato... Fatto[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Correzione delle dipendenze... Fatto[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]I seguenti pacchetti sono stati installati automaticamente e non sono più richiesti:[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  app-install-data apport apport-symptoms apt-xapian-index apturl-common[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  argyll dc duplicity empathy-common gedit-common geoclue-ubuntu-geoip[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gimp-data gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gnomekeyring-1.0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gir1.2-goa-1.0 gir1.2-gtop-2.0 gir1.2-gudev-1.0 gir1.2-rest-0.7[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gir1.2-secret-1 gir1.2-tracker-0.16 gir1.2-udisks-2.0 gir1.2-unity-5.0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gir1.2-zpj-0.0 gsettings-ubuntu-schemas gstreamer1.0-nice guile-2.0-libs[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  indicator-messages indicator-power indicator-session indicator-sound[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  intel-gpu-tools libaccounts-qt5-1 libamd2.3.1 libatkmm-1.6-1[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libavahi-gobject0 libbabl-0.1-0 libblas3 libboost-system1.54.0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libcairomm-1.0-1 libcamd2.3.1 libccolamd2.8.0 libcdr-0.0-0 libcholmod2.1.2[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libcrypt-passwdmd5-perl libdmapsharing-3.0-2 libexiv2-12 libfarstream-0.2-2[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libgc1c2 libgee2 libgegl-0.2-0 libgexiv2-2 libgfortran3 libgif4[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libglibmm-2.4-1c2a libgpod-common libgpod4 libgrilo-0.2-1 libgsf-1-114[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libgsf-1-common libgupnp-av-1.0-2 libicc2 libimdi0 libiptcdata0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libjavascriptcoregtk-1.0-0 liblapack3 liblightdm-gobject-1-0 liblua5.2-0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libmediaart-1.0-0 libminiupnpc8 libmng2 libmspub-0.0-0 libnatpmp1 libopencc1[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  liborcus-0.6-0 libpangomm-1.4-1 libpyzy-1.0-0 libqt5core5a libqt5dbus5[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libqt5network5 libqt5positioning5 libqt5qml5 libqt5sensors5 libqt5sql5[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libqt5sql5-sqlite libqt5test5 libqt5xml5 libraw9 libreoffice-l10n-it[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  librsync1 libsgutils2-2 libsigc++-2.0-0c2a libsignon-extension1[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libsignon-plugins-common1 libsignon-qt5-1 libtelepathy-farstream3[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libtracker-extract-0.16-0 libtracker-miner-0.16-0 libtracker-sparql-0.16-0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libumfpack5.6.2 liburl-dispatcher1 libvisio-0.0-0 libwebkitgtk-1.0-common[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libwhoopsie0 libxcb-randr0 libxcb-render-util0 libxcb-xkb1 libzapojit-0.0-0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  media-player-info mscompress oneconf-common printer-driver-foo2zjs-common[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  python-boto python-cloudfiles python-debtagshw python-dirspec[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  python-httplib2 python-lockfile python-lxml python-oauthlib python-oneconf[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  python-openssl python-pam python-piston-mini-client python-serial[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  python-twisted-bin python-twisted-core python-twisted-web[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  python-zope.interface python3-apport python3-cairo python3-chardet[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  python3-crypto python3-debian python3-gi-cairo python3-httplib2 python3-mako[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  python3-markupsafe python3-oauthlib python3-oneconf[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  python3-piston-mini-client python3-problem-report python3-six rhythmbox-data[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  shotwell-common signon-keyring-extension signond[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  software-center-aptdaemon-plugins syslinux syslinux-common syslinux-legacy[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  tcl telepathy-gabble telepathy-logger tk tracker tracker-extract[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  tracker-miner-fs tracker-utils transmission-common ubuntu-drivers-common[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  unattended-upgrades usb-creator-common[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Usare "apt-get autoremove" per rimuoverli.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]I seguenti pacchetti saranno inoltre installati:[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  foomatic-filters lightdm[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Pacchetti raccomandati:[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  unity-greeter lightdm-greeter lightdm-kde-greeter[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]I seguenti pacchetti saranno RIMOSSI:[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  aisleriot apport-gtk apt-transport-https apturl avahi-daemon avahi-utils[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  baobab bind9-host bluez-cups brasero brasero-cdrkit cheese cups cups-browsed[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  cups-bsd cups-client cups-core-drivers cups-daemon cups-filters[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  cups-filters-core-drivers cups-pk-helper cups-ppdc dconf-editor deja-dup[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  deja-dup-backend-cloudfiles deja-dup-backend-gvfs deja-dup-backend-s3[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  dnsutils empathy eog evince evolution evolution-data-server[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  evolution-data-server-online-accounts evolution-indicator evolution-plugins[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  file-roller firefox flashplugin-installer gcr gdm gedit ghostscript[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  ghostscript-x gimp gir1.2-appindicator3-0.1 gir1.2-caribou-1.0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-evince-3.0 gir1.2-gcr-3[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gir1.2-gdata-0.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-gnomebluetooth-1.0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gir1.2-gnomedesktop-3.0 gir1.2-gtk-3.0 gir1.2-gtkclutter-1.0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gir1.2-gtksource-3.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0 gir1.2-peas-1.0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gir1.2-rb-3.0 gir1.2-totem-1.0 gir1.2-vte-2.90 gir1.2-webkit-3.0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gir1.2-wnck-3.0 gjs gkbd-capplet gnome-bluetooth gnome-calculator[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gnome-color-manager gnome-contacts gnome-control-center gnome-disk-utility[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gnome-documents gnome-font-viewer gnome-icon-theme gnome-icon-theme-extras[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gnome-icon-theme-full gnome-icon-theme-symbolic gnome-keyring gnome-mahjongg[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gnome-mines gnome-online-accounts gnome-online-miners gnome-orca[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gnome-screenshot gnome-session gnome-session-bin gnome-session-canberra[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gnome-settings-daemon gnome-shell gnome-shell-extensions gnome-sudoku[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gnome-sushi gnome-system-log gnome-system-monitor gnome-terminal[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gnome-themes-standard gnome-tweak-tool gnome-user-guide gnome-user-share[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  google-chrome-stable grilo-plugins-0.2 gstreamer0.10-plugins-bad[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gstreamer1.0-clutter gstreamer1.0-plugins-bad gtk2-engines-pixbuf gucharmap[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  gvfs-backends gvfs-backends-goa hplip humanity-icon-theme ibus ibus-gtk[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  ibus-gtk3 ibus-pinyin ibus-table indicator-application kerneloops-daemon[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libappindicator1 libappindicator3-1 libbind9-90 libbrasero-media3-1[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libcamel-1.2-45 libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libcanberra-gtk3-module libcaribou0 libcheese-gtk23 libcheese7[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libclutter-1.0-0 libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcmis-0.4-4[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libcolord-gtk1 libcups2 libcupscgi1 libcupsfilters1 libcupsimage2[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libcupsmime1 libcupsppdc1 libcurl3 libcurl3-gnutls libdns100[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libedata-book-1.2-20 libedata-cal-1.2-23 libedataserver-1.2-18[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libevdocument3-4 libevolution libevview3-3 libfolks-eds25 libgail-3-0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libgail-common libgail18 libgcr-ui-3-1 libgdata13 libgdm1 libgimp2.0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libgjs0e libgnome-bluetooth11 libgnome-control-center1 libgnome-desktop-3-7[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libgnomekbd8 libgoa-backend-1.0-1 libgrip0 libgs9 libgtk-3-0 libgtk-3-bin[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libgtk2.0-0 libgtk2.0-bin libgtkglext1 libgtkhtml-4.0-0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkmm-2.4-1c2a[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libgtkmm-3.0-1 libgtksourceview-3.0-1 libgucharmap-2-90-7 libgweather-3-6[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libido3-0.1-0 libindicator3-7 libindicator7 libisccfg90 libmusicbrainz5-0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libmutter0c libnautilus-extension1a libneon27-gnutls libnm-gtk0 libnss-mdns[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  liboauth0 libopencv-contrib2.4 libopencv-highgui2.4 libopencv-legacy2.4[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libopencv-objdetect2.4 libpeas-1.0-0 libraptor2-0 librasqal3 librdf0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libreoffice-help-en-us libreoffice-help-it libreoffice-impress[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libreoffice-math libreoffice-ogltrans libreoffice-pdfimport[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libreoffice-presentation-minimizer libreoffice-writer librhythmbox-core8[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libsane-hpaio libslv2-9 libsmbclient libspectre1 libtotem0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libunity-control-center1 libvte-2.90-9 libwebkitgtk-1.0-0 libwebkitgtk-3.0-0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  libwnck-3-0 libyelp0 mcp-account-manager-goa mousetweaks mutter mythes-en-us[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  mythes-it nautilus nautilus-sendto nautilus-sendto-empathy nautilus-share[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  network-manager-gnome network-manager-pptp-gnome notification-daemon[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  nvidia-settings onboard onboard-data oneconf openssh-client parcellite[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  policykit-1-gnome printer-driver-c2esp printer-driver-foo2zjs[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  printer-driver-gutenprint printer-driver-hpcups printer-driver-pnm2ppa[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  printer-driver-sag-gdi printer-driver-splix python-aptdaemon.gtk3widgets[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  python-cups python-gnomekeyring python-gtk2 python-ibus python-notify[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  python-samba python-smbc python-ubuntu-sso-client[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  python3-aptdaemon.gtk3widgets python3-pyatspi python3-pycurl[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  python3-software-properties python3-uno rhythmbox rhythmbox-mozilla[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  rhythmbox-plugin-zeitgeist rhythmbox-plugins samba-common-bin samba-libs[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  screen-resolution-extra seahorse sessioninstaller shotwell simple-scan[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  smbclient software-center software-properties-common software-properties-gtk[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  ssh-askpass-gnome system-config-printer-common system-config-printer-gnome[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  system-config-printer-udev telepathy-salut totem totem-plugins[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  transmission-gtk ubuntu-gnome-default-settings ubuntu-gnome-desktop[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  ubuntu-release-upgrader-gtk ubuntu-sso-client ubuntu-standard unoconv[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  update-manager update-notifier usb-creator-gtk vino whoopsie[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  xdg-user-dirs-gtk xdiagnose yelp zeitgeist zeitgeist-datahub zenity[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]I seguenti pacchetti NUOVI saranno installati:[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  foomatic-filters lightdm[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]0 aggiornati, 2 installati, 317 da rimuovere e 0 non aggiornati.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]1 non completamente installati o rimossi.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]È necessario scaricare 196 kB di archivi.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Dopo quest'operazione, verranno liberati 975 MB di spazio su disco.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Continuare? [S/n] n[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Interrotto.[/FONT][/COLOR]
```
first time i digit "n"
second time i press "enter" :O

---

### Post by Bashing-om on 2015-07-21
painbrain2004; Yuk;

Regretful the avenue led to a (RE-)install.

However, the final result ->
all's well that ends well .

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just jeep on keep'n on
[/INDENT][/INDENT]

---

