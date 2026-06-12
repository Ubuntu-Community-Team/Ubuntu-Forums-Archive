---
title: "179 broken packages?"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by Robotnic on 2010-05-21
Hi all, 

I'm having massive problems with Synaptic Package Manager on Karmic. 

I attempted to open it only for it to close again almost instantly with no error, I had the same problem with Software Center. Terminal posted a segmentation error and I found a solution here [http://ubuntuforums.org/showthread.php?t=1333230. ]("http://ubuntuforums.org/showthread.php?t=1333230")

The error was the same so i followed the advice in the third post and managed to keep  Synaptic open where it informed me that I had 179 broken packages! I filtered these then selected fix broken packages and it told me they were fixed successfully, then Synaptic shut again and keeps shutting if I try to use the search box. It informs me that there are still 179 broken packages. 

I then realised that Update manager hadn't run for a few weeks and there was a red circle with a white bar. Hovering over the symbol tells me that there are broken packages.
Typing sudo apt-get install into terminal returned this error-

nic@nic-pc:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  acpi-support: Depends: lsb-base (>= 1.3-9ubuntu3) but 1.2.0.20090927-2ubuntu2 is installed
  acpid: Depends: lsb-base (>= 3.2-14) but 1.2.0.20090927-2ubuntu2 is installed
  alsa-utils: Depends: lsb-base (>= 3.0-9) but 1.2.0.20090927-2ubuntu2 is installed
  amor: Depends: libqtgui4 (>= 4.5.1) but it is not installed
  anacron: Depends: lsb-base (>= 3.0-10) but 1.2.0.20090927-2ubuntu2 is installed
  apport: Depends: lsb-base (>= 3.0-6) but 1.2.0.20090927-2ubuntu2 is installed
  apport-gtk: Depends: procps but it is not installed
  apt-transport-https: Depends: libcurl3-gnutls (>= 7.16.2-1) but it is not installed
  at: Depends: lsb-base (>= 3.2-14) but 1.2.0.20090927-2ubuntu2 is installed
  avahi-daemon: Depends: lsb-base (>= 3.0-6) but 1.2.0.20090927-2ubuntu2 is installed
  bind9-host: Depends: libgssapi-krb5-2 (>= 1.6.dfsg.2) but it is not installed
  brltty: Depends: lsb-base (>= 3.2-14) but 1.2.0.20090927-2ubuntu2 is installed
  compiz-fusion-plugins-main: Depends: libjpeg62 but it is not installed
  compiz-gnome: Depends: libgnome-desktop-2-11 (>= 1:2.27.3) but it is not installed
  console-setup: Conflicts: lsb-base (< 3.0-6) but 1.2.0.20090927-2ubuntu2 is installed
  cpp: Depends: cpp-4.4 (>= 4.4.1-1) but it is not installed
  cron: Depends: lsb-base (>= 3.2-12ubuntu4) but 1.2.0.20090927-2ubuntu2 is installed
  cups: Depends: libgssapi-krb5-2 (>= 1.6.dfsg.2) but it is not installed
        Depends: procps but it is not installed
        Depends: lsb-base (>= 3) but 1.2.0.20090927-2ubuntu2 is installed
  cups-driver-gutenprint: Depends: libgssapi-krb5-2 (>= 1.6.dfsg.2) but it is not installed
  dbus: Depends: lsb-base (>= 3.2-14) but 1.2.0.20090927-2ubuntu2 is installed
  dcraw: Depends: libjpeg62 but it is not installed
  electricsheep: Depends: libjpeg62 but it is not installed
  eog: Depends: libgnome-desktop-2-11 (>= 1:2.27.3) but it is not installed
       Depends: libjpeg62 but it is not installed
  erlang-base: Depends: procps but it is not installed
  evince: Depends: libjpeg62 but it is not installed
  evolution: Depends: libgnome-desktop-2-11 (>= 1:2.27.3) but it is not installed
  evolution-data-server: Depends: libgssapi-krb5-2 (>= 1.6.dfsg.2) but it is not installed
  evolution-plugins: Depends: libgnome-desktop-2-11 (>= 1:2.27.3) but it is not installed
  f-spot: Depends: libjpeg62 but it is not installed
  firefox-3.5: Depends: fontconfig but it is not installed
  flashplugin-installer: Depends: fontconfig but it is not installed
  foo2zjs: Depends: mscompress but it is not installed
  gcc-4.4: Depends: cpp-4.4 (= 4.4.1-4ubuntu9) but it is not installed
  ghostscript-cups: Depends: libgssapi-krb5-2 (>= 1.6.dfsg.2) but it is not installed
  gimp: Depends: libjpeg62 but it is not installed
  gnome-applets: Depends: libgnome-desktop-2-11 (>= 1:2.27.3) but it is not installed
  gnome-control-center: Depends: libgnome-desktop-2-11 (>= 1:2.27.3) but it is not installed
                        Depends: gnome-settings-daemon (>= 2.24) but it is not installed
  gnome-do: Depends: procps but it is not installed
            Recommends: gnome-do-plugins but it is not installed
  gnome-games: Depends: gtali but it is not installed
  gnome-nettool: Depends: dnsutils but it is not installed
  gnome-panel: Depends: libgnome-desktop-2-11 (>= 1:2.27.3) but it is not installed
  gnome-screensaver: Depends: libgnome-desktop-2-11 (>= 1:2.27.3) but it is not installed
  gnome-session: Depends: gnome-settings-daemon (>= 2.26) but it is not installed
  gnupg: Depends: libcurl3-gnutls (>= 7.16.2-1) but it is not installed
  grub-common: Depends: lsb-base (>= 3.0-6) but 1.2.0.20090927-2ubuntu2 is installed
  gstreamer0.10-plugins-good: Depends: libjpeg62 but it is not installed
                              Depends: libsoup-gnome2.4-1 (>= 2.27.92) but it is not installed
                              Depends: libspeex1 (>= 1.2~beta3-1) but it is not installed
  gvfs-backends: Depends: libsoup-gnome2.4-1 (>= 2.27.92) but it is not installed
  hal: Depends: lsb-base (>= 3.2-14) but 1.2.0.20090927-2ubuntu2 is installed
  hddtemp: Depends: lsb-base (>= 3.0-3) but 1.2.0.20090927-2ubuntu2 is installed
  holdingnuts: Depends: libqtgui4 (>= 4.5.1) but it is not installed
  hpijs: Depends: libjpeg62 but it is not installed
  hplip: Depends: lsb-base (>= 3) but 1.2.0.20090927-2ubuntu2 is installed
  ia32-libs: Depends: lib32v4l-0 but it is not installed
  ibus: Depends: python-ibus (= 1.2.0.20090927-2ubuntu2) but it is not installed
        Recommends: ibus-gtk but it is not installed or
                    ibus-qt4 but it is not installed
  ifupdown: Depends: lsb-base (>= 1.3-9ubuntu3) but 1.2.0.20090927-2ubuntu2 is installed
  initscripts: Depends: lsb-base (>= 3.2-14) but 1.2.0.20090927-2ubuntu2 is installed
  kbd: Depends: lsb-base (>= 3.0-10) but 1.2.0.20090927-2ubuntu2 is installed
  kde-window-manager: Depends: libqtgui4 (>= 4.5.1) but it is not installed
  kdebase-runtime: Depends: libjpeg62 but it is not installed
                   Depends: libqtgui4 (>= 4.5.1) but it is not installed
  kdebase-runtime-bin-kde4: Depends: libqtgui4 (>= 4.5.1) but it is not installed
  kdebase-workspace-libs4+5: Depends: libqtgui4 (>= 4.5.1) but it is not installed
  kdelibs-bin: Depends: libqtgui4 (>= 4.5.1) but it is not installed
  kdelibs4c2a: Depends: libgssapi-krb5-2 (>= 1.7dfsg~beta1) but it is not installed
               Depends: libjpeg62 but it is not installed
  kdelibs5: Depends: libgssapi-krb5-2 (>= 1.7dfsg~beta1) but it is not installed
            Depends: libjpeg62 but it is not installed
            Depends: libqtgui4 (>= 4.5.1) but it is not installed
  kerneloops-daemon: Depends: libcurl3-gnutls (>= 7.16.2-1) but it is not installed
  khelpcenter4: Depends: libqtgui4 (>= 4.5.1) but it is not installed
  ktouch: Depends: libqtgui4 (>= 4.5.1) but it is not installed
  language-pack-en-base: Depends: language-pack-en (>= 1:9.10+20091022) but it is not installed
  laptop-mode-tools: Depends: lsb-base (>= 3.0-10) but 1.2.0.20090927-2ubuntu2 is installed
  libart2-ruby1.8: Depends: libjpeg62 but it is not installed
  libavahi-qt3-1: Depends: libjpeg62 but it is not installed
  libavcodec52: Depends: libspeex1 (>= 1.2~beta3-1) but it is not installed
  libcamel1.2-14: Depends: libgssapi-krb5-2 (>= 1.7dfsg~beta1) but it is not installed
  libcouchdb-glib-1.0-1: Depends: libsoup-gnome2.4-1 (>= 2.27.92) but it is not installed
  libcups2: Depends: libgssapi-krb5-2 (>= 1.7dfsg~beta1) but it is not installed
  libcupsimage2: Depends: libjpeg62 but it is not installed
  libcurl3: Depends: libgssapi-krb5-2 (>= 1.7dfsg~beta1) but it is not installed
  libdjvulibre21: Depends: libjpeg62 but it is not installed
  libdns53: Depends: libgeoip1 (>= 1.4.6.dfsg) but it is not installed
            Depends: libgssapi-krb5-2 (>= 1.7dfsg~beta1) but it is not installed
  libebook1.2-9: Depends: libgssapi-krb5-2 (>= 1.6.dfsg.2) but it is not installed
  libedata-book1.2-2: Depends: libgssapi-krb5-2 (>= 1.6.dfsg.2) but it is not installed
  libedataserverui1.2-8: Depends: libgssapi-krb5-2 (>= 1.6.dfsg.2) but it is not installed
  libexchange-storage1.2-3: Depends: libgssapi-krb5-2 (>= 1.6.dfsg.2) but it is not installed
  libgd2-xpm: Depends: libjpeg62 but it is not installed
  libgdata5: Depends: libsoup-gnome2.4-1 (>= 2.27.2) but it is not installed
  libgdiplus: Depends: libjpeg62 but it is not installed
  libgegl-0.0-0: Depends: libjpeg62 but it is not installed
  libgnome-window-settings1: Depends: libgnome-desktop-2-11 (>= 1:2.27.3) but it is not installed
  libgnomedesktop2.20-cil: Depends: libgnome-desktop-2-11 (>= 1:2.27.3) but it is not installed
  libgnomevfs2-extra: Depends: libgssapi-krb5-2 (>= 1.7dfsg~beta1) but it is not installed
  libgphoto2-2: Depends: libjpeg62 but it is not installed
  libgraphviz4: Depends: libjpeg62 but it is not installed
  libgs8: Depends: libgssapi-krb5-2 (>= 1.6.dfsg.2) but it is not installed
  libgstfarsight0.10-0: Depends: gstreamer0.10-nice but it is not installed
  libgtk2.0-0: Depends: libgssapi-krb5-2 (>= 1.6.dfsg.2) but it is not installed
               Depends: libjpeg62 but it is not installed
  libgweather1: Depends: libsoup-gnome2.4-1 (>= 2.27.92) but it is not installed
  libjasper1: Depends: libjpeg62 but it is not installed
  libjpeg-progs: Depends: libjpeg62 but it is not installed
  libkdecorations4: Depends: libqtgui4 (>= 4.5.1) but it is not installed
  libknotificationitem1: Depends: libqtgui4 (>= 4.5.1) but it is not installed
  libkwineffects1: Depends: libqtgui4 (>= 4.5.1) but it is not installed
  libm17n-0: Depends: libjpeg62 but it is not installed
  libmagickcore2: Depends: libjpeg62 but it is not installed
  libmagickwand2: Depends: libjpeg62 but it is not installed
  libmjpegtools-1.9: Depends: libjpeg62 but it is not installed
  libmng1: Depends: libjpeg62 but it is not installed
  libneon27-gnutls: Depends: libgssapi-krb5-2 (>= 1.7dfsg~beta1) but it is not installed
  libpango1.0-common: Depends: fontconfig (>= 2.1.91) but it is not installed
  libplasma3: Depends: libqtgui4 (>= 4.5.1) but it is not installed
  libpoppler-glib4: Depends: libjpeg62 but it is not installed
  libpoppler5: Depends: libjpeg62 but it is not installed
  libpq5: Depends: libgssapi-krb5-2 (>= 1.7dfsg~beta1) but it is not installed
  libqt3-mt: Depends: libjpeg62 but it is not installed
             Depends: fontconfig but it is not installed
  libqt4-designer: Depends: libqtgui4 (= 4.5.3really4.5.2-0ubuntu1) but it is not installed
  libqt4-help: Depends: libqtgui4 (= 4.5.3really4.5.2-0ubuntu1) but it is not installed
  libqt4-opengl: Depends: libqtgui4 (= 4.5.3really4.5.2-0ubuntu1) but it is not installed
  libqt4-phonon: Depends: libqtgui4 (= 4.5.3really4.5.2-0ubuntu1) but it is not installed
  libqt4-qt3support: Depends: libqtgui4 (= 4.5.3really4.5.2-0ubuntu1) but it is not installed
  libqt4-scripttools: Depends: libqtgui4 (= 4.5.3really4.5.2-0ubuntu1) but it is not installed
  libqt4-svg: Depends: libqtgui4 (= 4.5.3really4.5.2-0ubuntu1) but it is not installed
  libqt4-webkit: Depends: libqtgui4 (= 4.5.3really4.5.2-0ubuntu1) but it is not installed
  libquicktime1: Depends: libjpeg62 but it is not installed
  libraptor1: Depends: libcurl3-gnutls (>= 7.16.2-1) but it is not installed
  libsane: Depends: libjpeg62 but it is not installed
  libsdl-image1.2: Depends: libjpeg62 but it is not installed
  libshout3: Depends: libspeex1 (>= 1.2~beta3-1) but it is not installed
  libsmbclient: Depends: libgssapi-krb5-2 (>= 1.7dfsg~beta1) but it is not installed
  libtiff4: Depends: libjpeg62 but it is not installed
  libwebkit-1.0-2: Depends: libjpeg62 but it is not installed
  libwmf0.2-7: Depends: libjpeg62 but it is not installed
  libwxgtk2.6-0: Depends: libjpeg62 but it is not installed
  libxine1-misc-plugins: Depends: libjpeg62 but it is not installed
                         Depends: libspeex1 (>= 1.2~beta3-1) but it is not installed
  nautilus: Depends: libgnome-desktop-2-11 (>= 1:2.27.3) but it is not installed
  netbase: Depends: lsb-base (>= 3.0-6) but 1.2.0.20090927-2ubuntu2 is installed
  network-manager: Depends: lsb-base (>= 3.2-14) but 1.2.0.20090927-2ubuntu2 is installed
                   Depends: wpasupplicant (>= 0.6.1~) but it is not installed
  nspluginwrapper: Depends: libcurl3-gnutls (>= 7.16.2-1) but it is not installed
  openjdk-6-jre: Depends: libjpeg62 but it is not installed
  openjdk-6-jre-headless: Depends: libjpeg62 but it is not installed
  openoffice.org-common: Depends: openoffice.org-style-default or
                                  openoffice.org-style
  openoffice.org-core: Depends: libcurl3-gnutls (>= 7.16.2-1) but it is not installed
                       Depends: libjpeg62 but it is not installed
                       Depends: fontconfig but it is not installed
  openoffice.org-emailmerge: PreDepends: procps but it is not installed
  openssh-client: Depends: libgssapi-krb5-2 (>= 1.7dfsg~beta1) but it is not installed
  pcmciautils: Depends: lsb-base (>= 3.0-6) but 1.2.0.20090927-2ubuntu2 is installed
  phonon-backend-xine: Depends: libqtgui4 (>= 4.5.1) but it is not installed
  pokerth: Depends: libcurl3-gnutls (>= 7.16.2-1) but it is not installed
           Depends: libqtgui4 (>= 4.5.1) but it is not installed
  poppler-utils: Depends: libjpeg62 but it is not installed
  ppp: Depends: procps but it is not installed
  pppconfig: Depends: lsb-base (>= 1.3-9ubuntu3) but 1.2.0.20090927-2ubuntu2 is installed
  pulseaudio: Depends: lsb-base (>= 3) but 1.2.0.20090927-2ubuntu2 is installed
  pxljr: Depends: libjpeg62 but it is not installed
  python: Depends: python-minimal (= 2.6.4-0ubuntu1) but it is not installed
  python-gda: Depends: libgda-4.0-4 but it is not installed
  python-imaging: Depends: libjpeg62 but it is not installed
  python-pygame: Depends: libjpeg62 but it is not installed
  python-qt4: Depends: libqtgui4 (>= 4.5.1) but it is not installed
  racer: Depends: libjpeg62 but it is not installed
  rhino: Depends: libjline-java but it is not installed
  rhythmbox: Depends: libsoup-gnome2.4-1 (>= 2.27.92) but it is not installed
  rsync: Depends: lsb-base (>= 3.2-14) but 1.2.0.20090927-2ubuntu2 is installed
  rsyslog: Depends: lsb-base (>= 3.2-14) but 1.2.0.20090927-2ubuntu2 is installed
  samba-common-bin: Depends: libgssapi-krb5-2 (>= 1.7dfsg~beta1) but it is not installed
  smbclient: Depends: libgssapi-krb5-2 (>= 1.7dfsg~beta1) but it is not installed
  speech-dispatcher: Depends: lsb-base (>= 3.0-10) but 1.2.0.20090927-2ubuntu2 is installed
  sunbird: Depends: fontconfig but it is not installed
           Depends: libjpeg62 but it is not installed
  tomboy: Depends: libgnomepanel2.24-cil (>= 2.24.0) but it is not installed
  transmission-gtk: Depends: libcurl3-gnutls (>= 7.16.2-1) but it is not installed
  ubufox: Depends: apturl (>= 0.1.2ubuntu1) but it is not installed or
                   apturl-kde but it is not installed
  ubuntu-desktop: Depends: gnome-themes-selected but it is not installed
                  Depends: metacity but it is not installed
                  Depends: sreadahead but it is not installed
                  Depends: wpasupplicant but it is not installed
                  Recommends: compiz but it is not installed
                  Recommends: ibus-gtk but it is not installed
                  Recommends: openoffice.org-gnome but it is not installed
                  Recommends: openoffice.org-help-en-us but it is not installed
                  Recommends: openoffice.org-style-human but it is not installed
  ubuntu-minimal: Depends: procps but it is not installed
  ubuntu-standard: Depends: dnsutils but it is not installed
  udev: Depends: procps but it is not installed
  util-linux: Depends: lsb-base (>= 3.0-6) but 1.2.0.20090927-2ubuntu2 is installed
  vino: Depends: libjpeg62 but it is not installed
  winbind: Depends: libgssapi-krb5-2 (>= 1.7dfsg~beta1) but it is not installed
           Depends: lsb-base (>= 3.0-6) but 1.2.0.20090927-2ubuntu2 is installed
  wine: Depends: procps but it is not installed
        Depends: binfmt-support (>= 1.1.2) but it is not installed
  x11-common: Depends: lsb-base (>= 1.3-9ubuntu2) but 1.2.0.20090927-2ubuntu2 is installed
  xloadimage: Depends: libjpeg62 but it is not installed
  xsane: Depends: libjpeg62 but it is not installed
  xscreensaver-data: Depends: libjpeg62 but it is not installed
E: Unmet dependencies. Try using -f.
nic@nic-pc:~$ 



Typing sudo apt-get -f install returned this output



nic@nic-pc:~$ sudo apt-get -f install
[sudo] password for nic: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  libavahi-qt3-1 kdelibs4c2a liblualib50 libgdata1.4-cil kdelibs-data liblua50
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apturl binfmt-support cpp-4.4 dnsutils fontconfig gnome-settings-daemon
  gnome-themes-selected gstreamer0.10-nice gtali language-pack-en lib32v4l-0
  libcurl3-gnutls libgda-4.0-4 libgeoip1 libgnome-desktop-2-11
  libgnomepanel2.24-cil libgssapi-krb5-2 libjline-java libjpeg62 libkrb5-3
  libkrb5support0 libqtgui4 libsoup-gnome2.4-1 libspeex1 lsb-base metacity
  mscompress openoffice.org-style-galaxy procps python-ibus python-minimal
  sreadahead wpasupplicant
Suggested packages:
  gcc-4.4-locales rblcheck gnome-themes-extras libgda-4.0-bin libgda-4.0-mysql
  libgda-4.0-postgres geoip-bin monodoc-gtk2.0-manual krb5-doc krb5-user
  libjline-java-doc qt4-qtconfig speex wpagui libengine-pkcs11-openssl
The following NEW packages will be installed
  apturl binfmt-support cpp-4.4 dnsutils fontconfig gnome-settings-daemon
  gnome-themes-selected gstreamer0.10-nice gtali language-pack-en lib32v4l-0
  libcurl3-gnutls libgda-4.0-4 libgeoip1 libgnome-desktop-2-11
  libgnomepanel2.24-cil libgssapi-krb5-2 libjline-java libjpeg62 libqtgui4
  libsoup-gnome2.4-1 libspeex1 metacity mscompress openoffice.org-style-galaxy
  procps python-ibus python-minimal sreadahead wpasupplicant
The following packages will be upgraded:
  libkrb5-3 libkrb5support0 lsb-base
3 upgraded, 30 newly installed, 0 to remove and 10 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
nic@nic-pc:~$ 



I don't know what to do next and have not managed to find any info on broken packages except where there are just 1 or 2 broken. Any help would be appreciated as I am no expert!

---

### Post by bapoumba on 2010-05-21
This:
```
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

```
Only one package manager or front end can run at any given time.
Please close synaptic and try again.

If it does not work, please try:
```
sudo rm /var/cache/apt/archives/lock
```
and run
```
sudo apt-get -f install
```

---

### Post by Robotnic on 2010-06-04
Hi bapoumba

Thanks for your reply. Still no joy...

> Only one package manager or front end can run at any given time.
Please close synaptic and try again.Synaptic wasn't open at the time

> If it does not work, please try:
     Code:
     sudo rm /var/cache/apt/archives/lock 
and run
     Code:
     sudo apt-get -f install 
This is the output from that 

nic@nic-pc:~$ sudo rm /var/cache/apt/archives/lock
nic@nic-pc:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  libavahi-qt3-1 kdelibs4c2a liblualib50 libgdata1.4-cil kdelibs-data liblua50
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apturl binfmt-support cpp-4.4 dnsutils fontconfig gnome-settings-daemon
  gnome-themes-selected gstreamer0.10-nice gtali language-pack-en lib32v4l-0
  libcurl3-gnutls libgda-4.0-4 libgeoip1 libgnome-desktop-2-11
  libgnomepanel2.24-cil libgssapi-krb5-2 libjline-java libjpeg62 libkrb5-3
  libkrb5support0 libqtgui4 libsoup-gnome2.4-1 libspeex1 lsb-base metacity
  mscompress openoffice.org-style-galaxy procps python-ibus python-minimal
  sreadahead wpasupplicant
Suggested packages:
  gcc-4.4-locales rblcheck gnome-themes-extras libgda-4.0-bin libgda-4.0-mysql
  libgda-4.0-postgres geoip-bin monodoc-gtk2.0-manual krb5-doc krb5-user
  libjline-java-doc qt4-qtconfig speex wpagui libengine-pkcs11-openssl
The following NEW packages will be installed
  apturl binfmt-support cpp-4.4 dnsutils fontconfig gnome-settings-daemon
  gnome-themes-selected gstreamer0.10-nice gtali language-pack-en lib32v4l-0
  libcurl3-gnutls libgda-4.0-4 libgeoip1 libgnome-desktop-2-11
  libgnomepanel2.24-cil libgssapi-krb5-2 libjline-java libjpeg62 libqtgui4
  libsoup-gnome2.4-1 libspeex1 metacity mscompress openoffice.org-style-galaxy
  procps python-ibus python-minimal sreadahead wpasupplicant
The following packages will be upgraded:
  libkrb5-3 libkrb5support0 lsb-base
3 upgraded, 30 newly installed, 0 to remove and 16 not upgraded.
Need to get 0B/16.0MB of archives.
After this operation, 42.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extract templates from packages: 100%
dpkg: parse error, in file '/var/lib/dpkg/status' near line 3444 package 'lsb-base':
 `Depends' field, syntax error after reference to package `r'
E: Sub-process /usr/bin/dpkg returned an error code (2)
nic@nic-pc:~$


I'm getting the distinct impression that things are pretty messed up!

Perhaps upgrading to 10.04 LTS is the answer?

My system is a dual boot with XP and both OS's have found file corruptions that needed fixing recently on startup. Perhaps a fresh install would be better yet?

Any ideas anyone? :confused:

---

