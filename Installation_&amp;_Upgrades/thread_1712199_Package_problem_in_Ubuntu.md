---
title: "Package problem in Ubuntu"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by Jamie_me on 2011-03-22
Hey guys,
I am having a problem of installing the g++ package for ubuntu 10.10 . 
I keep trying but nothing is working.. I have even reinstalled ubuntu several times.

I am using it in virtual box, t first it was working fine..then some sort of error occurred ,and my ubuntu got corrupted so had to reinstall ubuntu.Afterwards,its just giving me that broken package error.


PS: I know this topic has been discussed in many times,and i even tried implementing the the solutions,but its not working... Please help me.

---

### Post by Dutch70 on 2011-03-22
Hi and welcome to UF

 Try going to Synaptic Package Manager, click "edit" in the menu and select "fix broken packages"

---

### Post by sikander3786 on 2011-03-22
Welcome to the forums :-)

We will also need to see the complete outputs of these commands from Applications > Accessories > Terminal:

```
sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by Jamie_me on 2011-03-22
The output that I'm getting after 
```
sudo apt-get install g++ 
```
is 

libnm-glib2 is already the newest version.
network-manager is already the newest version.
language-pack-gnome-en is already the newest version.
gnome-screensaver is already the newest version.
gnome-system-tools is already the newest version.
libgucharmap7 is already the newest version.
libtag1c2a is already the newest version.
xscreensaver-gl is already the newest version.
libgphoto2-2 is already the newest version.
libutouch-grail1 is already the newest version.
python-imaging is already the newest version.
libgtksourceview2.0-common is already the newest version.
libgupnp-1.0-3 is already the newest version.
bogofilter-bdb is already the newest version.
gconf2 is already the newest version.
guile-1.8-libs is already the newest version.
gcc-4.5-base is already the newest version.
python-pygoocanvas is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
libdbusmenu-gtk1 is already the newest version.
libgnome-vfs2.0-cil is already the newest version.
fglrx-modaliases is already the newest version.
libgnome-keyring0 is already the newest version.
gnome-mag is already the newest version.
xserver-xorg-input-all is already the newest version.
network-manager-pptp-gnome is already the newest version.
fontconfig-config is already the newest version.
libgnome2-0 is already the newest version.
xserver-xorg-input-mouse is already the newest version.
light-themes is already the newest version.
libgtk2.0-bin is already the newest version.
gnome-applets is already the newest version.
libntfs-3g79 is already the newest version.
xserver-xorg-video-nv is already the newest version.
libcouchdb-glib-1.0-2 is already the newest version.
libglib2.0-cil is already the newest version.
language-selector-common is already the newest version.
ghostscript-cups is already the newest version.
compizconfig-backend-gconf is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
libpng12-0 is already the newest version.
erlang-syntax-tools is already the newest version.
xserver-xorg-video-geode is already the newest version.
gnome-about is already the newest version.
gwibber-service is already the newest version.
compiz-gnome is already the newest version.
libgee2 is already the newest version.
libxml-twig-perl is already the newest version.
update-manager is already the newest version.
libgnome-mag2 is already the newest version.
computer-janitor-gtk is already the newest version.
rhythmbox-plugin-cdrecorder is already the newest version.
gstreamer0.10-x is already the newest version.
rsyslog is already the newest version.
powermgmt-base is already the newest version.
network-manager-gnome is already the newest version.
libvisual-0.4-plugins is already the newest version.
xserver-xorg-video-i740 is already the newest version.
libtelepathy-farsight0 is already the newest version.
iputils-arping is already the newest version.
libhtml-tagset-perl is already the newest version.
pulseaudio is already the newest version.
gvfs-fuse is already the newest version.
xorg-docs-core is already the newest version.
libgnome-bluetooth8 is already the newest version.
xserver-xorg-video-ati is already the newest version.
xserver-xorg-video-siliconmotion is already the newest version.
gstreamer0.10-alsa is already the newest version.
python-gconf is already the newest version.
erlang-crypto is already the newest version.
gstreamer0.10-tools is already the newest version.
libgphoto2-port0 is already the newest version.
libglib2.0-0 is already the newest version.
libgdata7 is already the newest version.
python-configglue is already the newest version.
gnome-session-bin is already the newest version.
libgomp1 is already the newest version.
xserver-xorg-video-tseng is already the newest version.
usb-creator-gtk is already the newest version.
software-properties-gtk is already the newest version.
gcc-4.4-base is already the newest version.
libgnome-media0 is already the newest version.
liblaunchpad-integration1 is already the newest version.
gconf-defaults-service is already the newest version.
gnome-power-manager is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 abrowser-branding : Conflicts: firefox-branding
 asterisk-dbg : Depends: asterisk (= 1:1.6.2.7-1ubuntu1.1) but it is not going to be installed
 broffice.org : Depends: openoffice.org-l10n-pt-br but it is not installable
                Depends: openoffice.org-help-pt-br but it is not installable
                Depends: myspell-pt-br but it is not installable
 cgiirc : Depends: apache but it is not installable or
                   httpd-cgi
 chromium-codecs-ffmpeg : Conflicts: chromium-codecs-ffmpeg-extra but 10.0.648.133~r77742-0ubuntu0.10.10.1 is to be installed
                          Conflicts: chromium-codecs-ffmpeg-nonfree
 chromium-codecs-ffmpeg-dbg : Conflicts: chromium-codecs-ffmpeg-extra-dbg but 10.0.648.133~r77742-0ubuntu0.10.10.1 is to be installed
                              Conflicts: chromium-codecs-ffmpeg-nonfree-dbg
 chromium-codecs-ffmpeg-extra : Conflicts: chromium-codecs-ffmpeg but 10.0.648.133~r77742-0ubuntu0.10.10.1 is to be installed
 chromium-codecs-ffmpeg-extra-dbg : Conflicts: chromium-codecs-ffmpeg-dbg but 10.0.648.133~r77742-0ubuntu0.10.10.1 is to be installed
 clamav-dbg : Depends: libclamav6 but it is not going to be installed
              Depends: clamav (= 0.96.5+dfsg-1ubuntu1.10.10.2) but it is not going to be installed
 cli-uno-bridge : Depends: libmono0 (>= 2.6.7) but it is not installable
 dpkg-dev : Depends: patch but it is not installable
            Recommends: build-essential but it is not installable
            Recommends: fakeroot but it is not installable
            Recommends: libalgorithm-merge-perl but it is not installable
 eucalyptus-gl : Depends: libaxis2c0 but it is not installable
                 Depends: librampart0 but it is not installable
                 Depends: eucalyptus-common but it is not going to be installed
 evince-dbg : Depends: evince (= 2.32.0-0ubuntu1.1) but it is not going to be installed
 exim4-daemon-heavy-dbg : Depends: exim4-daemon-heavy but it is not going to be installed
 firefox-branding : Conflicts: abrowser-branding
 gir1.0-evince-2.32 : Depends: gir1.0-atk-1.0 but it is not installable
                      Depends: gir1.0-freedesktop but it is not installable
                      Depends: gir1.0-gdkpixbuf-2.0 but it is not installable
                      Depends: gir1.0-gtk-2.0 but it is not installable
 gir1.0-pango-1.0 : Depends: gir1.0-freedesktop but it is not installable
 git : Depends: liberror-perl but it is not installable
       Recommends: patch but it is not installable
 git-arch : Depends: tla but it is not installable
 git-cvs : Depends: cvsps (> 2.1-0) but it is not installable
           Depends: libdbd-sqlite3-perl but it is not installable
 git-daemon-run : Depends: runit (>= 1.8.0-2) but it is not installable
 git-gui : Depends: tk (>= 8.4) but it is not installable
 git-svn : Depends: libsvn-perl but it is not going to be installed or
                    libsvn-core-perl but it is not installable
 gitk : Depends: tk (>= 8.4) but it is not installable
 gitolite : Depends: openssh-server but it is not installable or
                     ssh-server but it is not installable
 hplip-gui : Depends: python-qt4 but it is not installable
             Depends: python-qt4-dbus but it is not installable
             Depends: python-reportlab but it is not installable
 icedtea6-plugin : Depends: openjdk-6-jre (= 6b20-1.9.7-0ubuntu1) but it is not going to be installed
 kdelibs-dbg : Depends: kdelibs4c2a (= 4:3.5.10.dfsg.1-3ubuntu2.10.10.1) but it is not going to be installed
               Depends: qt-x11-free-dbg but it is not installable
 libapache2-mod-fcgid : Depends: apache2.2-common but it is not going to be installed
 libaprutil1-dbd-pgsql : Depends: libaprutil1 (= 1.3.9+dfsg-3ubuntu0.10.10.1) but it is not going to be installed
 libaprutil1-dbg : Depends: libaprutil1 (= 1.3.9+dfsg-3ubuntu0.10.10.1) but it is not going to be installed
 libavahi-glib-dev : Depends: libglib2.0-dev but it is not installable
 libavahi-gobject-dev : Depends: libglib2.0-dev but it is not installable
 libcupscgi1-dev : Depends: libcups2-dev (= 1.4.4-6ubuntu2.3) but it is not going to be installed
 libcupsimage2-dev : Depends: libcups2-dev (= 1.4.4-6ubuntu2.3) but it is not going to be installed
                     Depends: libpng-dev but it is not installable
                     Depends: libtiff4-dev but it is not going to be installed
                     Depends: libjpeg8-dev but it is not installable or
                              libjpeg-dev but it is not installable
                     Depends: zlib1g-dev but it is not installable
 libecpg-dev : Depends: libpq-dev but it is not going to be installed
 libmagickcore-dev : Depends: libbz2-dev but it is not installable
                     Depends: libdjvulibre-dev but it is not installable
                     Depends: libexif-dev but it is not installable
                     Depends: libfreetype6-dev but it is not going to be installed
                     Depends: libgraphviz-dev but it is not installable
                     Depends: libjasper-dev but it is not installable
                     Depends: libjpeg-dev but it is not installable
                     Depends: liblqr-1-0-dev but it is not installable
                     Depends: libltdl-dev but it is not installable
                     Depends: libopenexr-dev but it is not installable
                     Depends: libpng-dev but it is not installable
                     Depends: librsvg2-dev but it is not installable
                     Depends: libtiff-dev
                     Depends: libwmf-dev but it is not installable
                     Depends: libx11-dev but it is not installable
                     Depends: libxext-dev but it is not installable
                     Depends: libxt-dev but it is not installable
                     Depends: zlib1g-dev but it is not installable
 libmagickcore3-extra : Depends: libcdt4 but it is not installable
                        Depends: libgraph4 but it is not installable
                        Depends: libgvc5 but it is not installable
                        Depends: libilmbase6 (>= 1.0.1) but it is not installable
                        Depends: libopenexr6 (>= 1.6.1) but it is not installable
 libopensc2-dbg : Depends: libopensc2 (= 0.11.13-1ubuntu2.1) but it is not going to be installed
 libpango1.0-dev : Depends: libglib2.0-dev (>= 2.12.0) but it is not installable
                   Depends: libfreetype6-dev (>= 2.1.3) but it is not going to be installed
                   Depends: libx11-dev but it is not installable
                   Depends: libxrender-dev but it is not installable
                   Depends: libxft-dev but it is not installable
                   Depends: libfontconfig1-dev (>= 2.1.91) but it is not installable
                   Depends: libcairo2-dev (>= 1.8.2-2) but it is not installable
                   Recommends: debhelper but it is not installable
 libpoppler-glib-dev : Depends: libpoppler-dev (= 0.14.3-0ubuntu1.1) but it is not going to be installed
                       Depends: libglib2.0-dev (>= 2.12) but it is not installable
                       Depends: libcairo2-dev (>= 1.8.4) but it is not installable
 libtiff-opengl : Depends: freeglut3 but it is not installable
 linux-backports-modules-compat-wireless-2.6.36-2.6.35-25-generic : Conflicts: linux-backports-modules-compat-wireless-2.6.37-2.6.35-25-generic but 2.6.35-25.16 is to be installed
 linux-backports-modules-compat-wireless-2.6.36-2.6.35-25-generic-pae : Conflicts: linux-backports-modules-compat-wireless-2.6.37-2.6.35-25-generic-pae but 2.6.35-25.16 is to be installed
 linux-backports-modules-compat-wireless-2.6.36-2.6.35-27-generic : Conflicts: linux-backports-modules-compat-wireless-2.6.37-2.6.35-27-generic but 2.6.35-27.18 is to be installed
 linux-backports-modules-compat-wireless-2.6.36-2.6.35-27-generic-pae : Conflicts: linux-backports-modules-compat-wireless-2.6.37-2.6.35-27-generic-pae but 2.6.35-27.18 is to be installed
 linux-backports-modules-compat-wireless-2.6.36-2.6.35-28-generic : Conflicts: linux-backports-modules-compat-wireless-2.6.37-2.6.35-28-generic but 2.6.35-28.19 is to be installed
 linux-backports-modules-compat-wireless-2.6.36-2.6.35-28-generic-pae : Conflicts: linux-backports-modules-compat-wireless-2.6.37-2.6.35-28-generic-pae but 2.6.35-28.19 is to be installed
 linux-backports-modules-compat-wireless-2.6.37-2.6.35-25-generic : Conflicts: linux-backports-modules-compat-wireless-2.6.36-2.6.35-25-generic but 2.6.35-25.16 is to be installed
 linux-backports-modules-compat-wireless-2.6.37-2.6.35-25-generic-pae : Conflicts: linux-backports-modules-compat-wireless-2.6.36-2.6.35-25-generic-pae but 2.6.35-25.16 is to be installed
 linux-backports-modules-compat-wireless-2.6.37-2.6.35-27-generic : Conflicts: linux-backports-modules-compat-wireless-2.6.36-2.6.35-27-generic but 2.6.35-27.18 is to be installed
 linux-backports-modules-compat-wireless-2.6.37-2.6.35-27-generic-pae : Conflicts: linux-backports-modules-compat-wireless-2.6.36-2.6.35-27-generic-pae but 2.6.35-27.18 is to be installed
 linux-backports-modules-compat-wireless-2.6.37-2.6.35-28-generic : Conflicts: linux-backports-modules-compat-wireless-2.6.36-2.6.35-28-generic but 2.6.35-28.19 is to be installed
 linux-backports-modules-compat-wireless-2.6.37-2.6.35-28-generic-pae : Conflicts: linux-backports-modules-compat-wireless-2.6.36-2.6.35-28-generic-pae but 2.6.35-28.19 is to be installed
 mozilla-plugin-vlc : Depends: vlc but it is not going to be installed
                      Depends: vlc-nox (= 1.1.4-1ubuntu1.4) but it is not going to be installed
 mumble-dbg : Depends: mumble (= 1.2.2-4ubuntu0.1) but it is not going to be installed or
                       mumble-server (= 1.2.2-4ubuntu0.1) but it is not going to be installed
 openjdk-6-dbg : Depends: openjdk-6-jre-headless (= 6b20-1.9.7-0ubuntu1) but it is not going to be installed
                 Recommends: openjdk-6-jre (= 6b20-1.9.7-0ubuntu1) but it is not going to be installed
 openoffice.org : Depends: ttf-dejavu but it is not installable
                  Depends: ttf-sil-gentium-basic but it is not installable
 openoffice.org-base : Depends: default-jre but it is not installable or
                                gcj-jre but it is not installable or
                                java-gcj-compat but it is not installable or
                                openjdk-6-jre but it is not going to be installed or
                                sun-java5-jre but it is not installable or
                                sun-java6-jre but it is not installable or
                                java5-runtime or
                                jre but it is not installable
                       Depends: libhsqldb-java (> 1.8.0.10) but it is not installable
                       Depends: libhsqldb-java (< 1.8.1~) but it is not installable
 openoffice.org-dev : Depends: libstlport4.6-dev (>= 4.6.2-3) but it is not installable
                      Recommends: dmake but it is not installable
                      Recommends: g++ but it is not installable
                      Recommends: default-jre but it is not installable or
                                  gcj-jre but it is not installable or
                                  java-gcj-compat but it is not installable or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java5-jre but it is not installable or
                                  sun-java6-jre but it is not installable or
                                  java5-runtime or
                                  jre but it is not installable
 openoffice.org-filter-mobiledev : Depends: default-jre but it is not installable or
                                            gcj-jre but it is not installable or
                                            java-gcj-compat but it is not installable or
                                            openjdk-6-jre but it is not going to be installed or
                                            sun-java5-jre but it is not installable or
                                            sun-java6-jre but it is not installable or
                                            java5-runtime or
                                            jre but it is not installable
 openoffice.org-gcj : Depends: libgcj-bc (>= 4.4.4-1) but it is not installable
                      Depends: java-gcj-compat but it is not installable
                      Depends: libgcj-common (>= 1:4.1.1-14) but it is not installable
                      Depends: libhsqldb-java-gcj but it is not installable
                      Depends: bsh-gcj but it is not installable
 openoffice.org-java-common : Depends: default-jre but it is not installable or
                                       gcj-jre but it is not installable or
                                       java-gcj-compat but it is not installable or
                                       openjdk-6-jre but it is not going to be installed or
                                       sun-java5-jre but it is not installable or
                                       sun-java6-jre but it is not installable or
                                       java5-runtime or
                                       jre but it is not installable
 openoffice.org-kde : Depends: kdebase-runtime but it is not installable
                      Depends: libkdecore5 (>= 4:4.3.4) but it is not installable
                      Depends: libkdeui5 (>= 4:4.3.4) but it is not installable
                      Depends: libkfile4 (>= 4:4.5.1) but it is not installable
                      Depends: libkio5 (>= 4:4.5.1) but it is not installable
                      Depends: libqtcore4 (>= 4:4.7.0~beta1) but it is not installable
                      Depends: libqtgui4 (>= 4:4.5.3) but it is not installable
 openoffice.org-l10n-in : Depends: openoffice.org-l10n-as but it is not installable
                          Depends: openoffice.org-l10n-bn but it is not installable
                          Depends: openoffice.org-l10n-gu but it is not installable
                          Depends: openoffice.org-l10n-hi-in but it is not installable
                          Depends: openoffice.org-l10n-ml but it is not installable
                          Depends: openoffice.org-l10n-mr but it is not installable
                          Depends: openoffice.org-l10n-or but it is not installable
                          Depends: openoffice.org-l10n-pa-in but it is not installable
                          Depends: openoffice.org-l10n-ta but it is not installable
                          Depends: openoffice.org-l10n-te but it is not installable
                          Recommends: ttf-indic-fonts but it is not installable
 openoffice.org-l10n-za : Depends: openoffice.org-l10n-af but it is not installable
                          Depends: openoffice.org-l10n-en-za but it is not installable
                          Depends: openoffice.org-l10n-nr but it is not installable
                          Depends: openoffice.org-l10n-ns but it is not installable
                          Depends: openoffice.org-l10n-ss but it is not installable
                          Depends: openoffice.org-l10n-st but it is not installable
                          Depends: openoffice.org-l10n-tn but it is not installable
                          Depends: openoffice.org-l10n-ts but it is not installable
                          Depends: openoffice.org-l10n-ve but it is not installable
                          Depends: openoffice.org-l10n-xh but it is not installable
                          Depends: openoffice.org-l10n-zu but it is not installable
 openoffice.org-mysql-connector : Depends: libmysqlcppconn4 (>= 1.1.0~r791) but it is not installable
 openoffice.org-officebean : Depends: default-jre but it is not installable or
                                      gcj-jre but it is not installable or
                                      java-gcj-compat (>= 1.0.77-4) but it is not installable or
                                      openjdk-6-jre but it is not going to be installed or
                                      sun-java5-jre but it is not installable or
                                      sun-java6-jre but it is not installable or
                                      java5-runtime or
                                      jre but it is not installable
 openoffice.org-report-builder : Depends: libbase-java-openoffice.org but it is not installable
                                 Depends: libsac-java but it is not installable
                                 Depends: libxml-java-openoffice.org but it is not installable
                                 Depends: libflute-java-openoffice.org but it is not installable
                                 Depends: libpentaho-reporting-flow-engine-java-openoffice.org but it is not installable
                                 Depends: liblayout-java-openoffice.org but it is not installable
                                 Depends: libloader-java-openoffice.org but it is not installable
                                 Depends: libformula-java-openoffice.org but it is not installable
                                 Depends: librepository-java-openoffice.org but it is not installable
                                 Depends: libfonts-java-openoffice.org but it is not installable
                                 Depends: libserializer-java-openoffice.org but it is not installable
                                 Depends: libcommons-logging-java but it is not installable
                                 PreDepends: default-jre but it is not installable or
                                             gcj-jre but it is not installable or
                                             java-gcj-compat but it is not installable or
                                             openjdk-6-jre but it is not going to be installed or
                                             sun-java5-jre but it is not installable or
                                             sun-java6-jre but it is not installable or
                                             java5-runtime or
                                             jre but it is not installable
 openoffice.org-wiki-publisher : Depends: libcommons-codec-java but it is not installable
                                 Depends: libcommons-httpclient-java but it is not installable
                                 Depends: libcommons-lang-java but it is not installable
                                 Depends: libcommons-logging-java but it is not installable
                                 PreDepends: default-jre but it is not installable or
                                             gcj-jre but it is not installable or
                                             java-gcj-compat but it is not installable or
                                             openjdk-6-jre but it is not going to be installed or
                                             sun-java5-jre but it is not installable or
                                             sun-java6-jre but it is not installable or
                                             java5-runtime or
                                             jre but it is not installable
 pidgin-dev : Depends: libpurple-dev but it is not going to be installed
              Depends: libgtk2.0-dev but it is not installable
 postgresql-8.4 : Depends: postgresql-common (>= 109~) but it is not installable
 postgresql-client-8.4 : Depends: postgresql-client-common (>= 104~) but it is not installable
 postgresql-contrib-8.4 : Depends: libossp-uuid16 but it is not installable
                          Depends: postgresql-common (>= 109~) but it is not installable
 postgresql-pltcl-8.4 : Depends: tcl8.5 (>= 8.5.0) but it is not installable
 postgresql-server-dev-8.4 : Depends: libpq-dev (>= 8.4~) but it is not going to be installed
 python-libxml2-dbg : Depends: python-dbg but it is not installable
 python-subversion-dbg : Depends: python-subversion (= 1.6.12dfsg-1ubuntu1.1) but it is not going to be installed
                         Depends: python-dbg but it is not installable
                         Depends: libapr1 (>= 1.2.7) but it is not installable
                         Depends: libsvn1 (>= 1.6) but it is not going to be installed
 squid-cgi : Depends: apache2 or
                      httpd
 squid3-dbg : Depends: squid3 (= 3.1.6-1.1ubuntu1.1) but it is not going to be installed
 systemtap-grapher : Depends: systemtap (= 1.3-1ubuntu0.1) but it is not going to be installed
                     Depends: libglademm-2.4-1c2a (>= 2.6.0) but it is not installable
 tuxguitar : Depends: default-jre but it is not installable or
                      java2-runtime
             Depends: libitext-java but it is not installable
             Depends: libswt-gtk-3.5-java but it is not installable
             Depends: libswt-cairo-gtk-3.5-jni but it is not installable
             Depends: libswt-mozilla-gtk-3.5-jni but it is not installable
 tuxguitar-fluidsynth : Depends: libfluidsynth1 but it is not installable
                        Depends: fluidsynth but it is not installable
 tuxguitar-jack : Depends: libjack-dev but it is not installable
 tuxguitar-jsa : Depends: default-jre but it is not installable or
                          sun-java6-jre but it is not installable or
                          sun-java5-jre but it is not installable
 tuxguitar-oss : Depends: oss-compat but it is not installable
 vlc-dbg : Depends: vlc-nox (= 1.1.4-1ubuntu1.4) but it is not going to be installed
 vlc-plugin-fluidsynth : Depends: vlc-nox (= 1.1.4-1ubuntu1.4) but it is not going to be installed
                         Depends: libfluidsynth1 but it is not installable
 vlc-plugin-ggi : Depends: vlc-nox but it is not going to be installed
                  Depends: libggi2 (>= 1:2.2.2) but it is not installable
 vlc-plugin-jack : Depends: vlc-nox (= 1.1.4-1ubuntu1.4) but it is not going to be installed
 vlc-plugin-notify : Depends: vlc-nox (= 1.1.4-1ubuntu1.4) but it is not going to be installed
 vlc-plugin-pulse : Depends: vlc-nox (= 1.1.4-1ubuntu1.4) but it is not going to be installed
 vlc-plugin-sdl : Depends: vlc-nox but it is not going to be installed
 vlc-plugin-svg : Depends: vlc-nox (= 1.1.4-1ubuntu1.4) but it is not going to be installed
 vlc-plugin-svgalib : Depends: vlc-nox (= 1.1.4-1ubuntu1.4) but it is not going to be installed
                      Depends: libsvga1 but it is not installable
 vlc-plugin-zvbi : Depends: vlc-nox (= 1.1.4-1ubuntu1.4) but it is not going to be installed
                   Depends: libzvbi0 (>= 0.2.11) but it is not installable
 wireshark-dbg : Depends: wireshark-common (= 1.2.11-6build0.10.10.1) but it is not going to be installed or
                          wireshark (= 1.2.11-6build0.10.10.1) but it is not going to be installed or
                          tshark (= 1.2.11-6build0.10.10.1) but it is not going to be installed
E: Broken packages

---

### Post by Jamie_me on 2011-03-22
```
sudo apt-get install -f
```
The is the output for this code,

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shamoon@shamoon-VirtualBox:~$ ^C
shamoon@shamoon-VirtualBox:~$ 


for ```
sudo dpkg --configure -a
```
nothing happens,

---

### Post by Dutch70 on 2011-03-22
Make sure you're up to date...
```
sudo apt-get update && sudo apt-get upgrade
```

Then try the install again.

---

### Post by Jamie_me on 2011-03-23
```
sudo apt-get update && sudo apt-get upgrade
```

for this code,the output is coming as..

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

---

### Post by Dutch70 on 2011-03-23
That usually happens when you have more than one instance of synaptic running. 
Close one of them, if you don't know what to close, just reboot.

---

### Post by Jamie_me on 2011-03-23
I rebooted but still I'm getting this output :(...................... 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

---

### Post by pl@yer on 2011-03-23
to see what PID has this open try
```

fuser /var/lib/apt/lists/lock

```
or 
```

lsof|grep /var/lib/apt/lists/lock

```

You probably have update manager or something else running in the background.

---

