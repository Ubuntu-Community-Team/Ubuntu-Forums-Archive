---
title: "Cannot upgrade 14.04 -&gt; 16.04 - broken packages"
date: 2017-01-14
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2017-01-14
I have been trying to upgrade from 14.04 to 16.04, but I have had a lot of dependency errors.  Here is what I get when I run ```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 blender : Depends: blender-data (= 2.69-4ubuntu2) but 2.76.b+dfsg0-3build1 is installed
 bogofilter-bdb : Depends: libgsl0ldbl (>= 1.9) but it is not installable
 digikam : Depends: libopencv-core2.4 but it is not installable
 enblend : Depends: libgsl0ldbl (>= 1.9) but it is not installable
 enfuse : Depends: libgsl0ldbl (>= 1.9) but it is not installable
 freerdp-x11 : Depends: libfreerdp1 (>= 1.0.1) but it is not installable
 frei0r-plugins : Depends: libopencv-core2.4 but it is not installable
                  Depends: libopencv-imgproc2.4 but it is not installable
                  Depends: libopencv-objdetect2.4 but it is not installable
 gdm : Depends: libgdm1 (= 3.10.0.1-0ubuntu3.2) but 3.18.3-0ubuntu2 is installed
       Depends: gir1.2-gdm-1.0 (= 3.10.0.1-0ubuntu3.2) but 3.18.3-0ubuntu2 is installed
 gir1.2-cogl-1.0 : Depends: libcogl15 (>= 1.15.8) but it is not installable
 gir1.2-freedesktop : Depends: gir1.2-glib-2.0 (= 1.40.0-1ubuntu0.2) but 1.46.0-3ubuntu1 is installed
 gnome-bluetooth : Depends: gir1.2-gnomebluetooth-1.0 (= 3.8.2.1-0ubuntu4.2) but 3.18.2-1ubuntu2 is installed
                   Depends: obexd-client but it is not installable
 gnome-commander : Depends: libtag1c2a (>= 1.5) but it is not installable
 gparted : Depends: libatkmm-1.6-1v5 (>= 2.24.0) but it is not installed
           Depends: libglibmm-2.4-1v5 (>= 2.46.0) but it is not installed
           Depends: libgtkmm-2.4-1v5 (>= 1:2.24.0) but it is not installed
           Depends: libpangomm-1.4-1v5 (>= 2.38.0) but it is not installed
           Depends: libsigc++-2.0-0v5 (>= 2.6.1) but it is not installed
 gstreamer0.10-plugins-good : Depends: libtag1c2a (>= 1.5) but it is not installable
 gstreamer1.0-clutter : Depends: libcogl15 (>= 1.15.8) but it is not installable
 gvfs : Depends: gvfs-libs (= 1.20.3-0ubuntu1.2) but 1.28.2-1ubuntu1~16.04.1 is installed
 gvfs:i386 : Depends: gvfs-libs:i386 (= 1.20.3-0ubuntu1.2) but 1.28.2-1ubuntu1~16.04.1 is installed
 gvfs-backends : Depends: gvfs-libs (= 1.20.3-0ubuntu1.2) but 1.28.2-1ubuntu1~16.04.1 is installed
 gvfs-daemons : Depends: gvfs-libs (= 1.20.3-0ubuntu1.2) but 1.28.2-1ubuntu1~16.04.1 is installed
 gvfs-libs : Depends: gvfs-common (= 1.28.2-1ubuntu1~16.04.1) but 1.20.3-0ubuntu1.2 is installed
 gvfs-libs:i386 : Depends: gvfs-common:i386 (= 1.28.2-1ubuntu1~16.04.1)
 indicator-datetime : Depends: libical1 (>= 1.0) but it is not installable
 inkscape : Depends: libgsl0ldbl (>= 1.9) but it is not installable
 kid3-core : Depends: libtag1c2a (>= 1.9.1) but it is not installable
 libalgorithm-diff-xs-perl : Depends: perlapi-5.18.1 but it is not installable
 libapparmor-perl : Depends: perlapi-5.18.2 but it is not installable
 libapt-pkg-perl : Depends: perlapi-5.18.1 but it is not installable
 libarchive12 : Depends: libnettle4 (>= 2.3) but it is not installable
 libarchive13 : Depends: libnettle4 (>= 2.3) but it is not installable
 libasync-interrupt-perl : Depends: perlapi-5.18.1 but it is not installable
 libbit-vector-perl : Depends: perlapi-5.18.1 but it is not installable
 libcairo-perl : Depends: perlapi-5.18.1 but it is not installable
 libclone-perl : Depends: perlapi-5.18.1 but it is not installable
 libclutter-gst-2.0-0 : Depends: libcogl15 (>= 1.15.8) but it is not installable
 libcogl-pango15 : Depends: libcogl15 (>= 1.15.8) but it is not installable
 libcommon-sense-perl : Depends: perl (< 5.18.3~) but 5.22.1-9 is installed
 libcompress-raw-lzma-perl : Depends: perlapi-5.18.1 but it is not installable
 libcups2-dev : Depends: libcups2 (= 1.7.2-0ubuntu1.7) but 2.1.3-4 is installed
 libcupscgi1 : Depends: libcups2 (= 1.7.2-0ubuntu1.7) but 2.1.3-4 is installed
 libcupsimage2 : Depends: libcups2 (= 1.7.2-0ubuntu1.7) but 2.1.3-4 is installed
 libcupsimage2:i386 : Depends: libcups2:i386 (= 1.7.2-0ubuntu1.7) but 2.1.3-4 is installed
 libcupsmime1 : Depends: libcups2 (= 1.7.2-0ubuntu1.7) but 2.1.3-4 is installed
 libcupsppdc1 : Depends: libcups2 (= 1.7.2-0ubuntu1.7) but 2.1.3-4 is installed
 libdate-calc-xs-perl : Depends: perlapi-5.18.1 but it is not installable
 libdatetime-perl : Depends: perlapi-5.18.1 but it is not installable
 libdbd-mysql-perl : Depends: perlapi-5.18.2 but it is not installable
 libdbi-perl : Depends: perlapi-5.18.1 but it is not installable
 libdevice-serialport-perl : Depends: perlapi-5.18.1 but it is not installable
 libecal-1.2-16 : Depends: libical1 (>= 1.0) but it is not installable
 libedata-cal-1.2-23 : Depends: libical1 (>= 1.0) but it is not installable
 libevent-perl : Depends: perlapi-5.18.1 but it is not installable
 libfile-fcntllock-perl : Depends: perlapi-5.18.1 but it is not installable
 libfontconfig1 : Depends: fontconfig-config (= 2.11.94-0ubuntu1.1) but 2.11.0-0ubuntu4.2 is installed
 libfontconfig1:i386 : Depends: fontconfig-config:i386 (= 2.11.94-0ubuntu1.1)
 libfreerdp-core1.1 : Depends: libfreerdp-codec1.1 (>= 1.1.0~beta1+git20130629) but it is not installed
                      Depends: libwinpr-sysinfo0.1 (>= 1.1.0~beta1+git20130629) but it is not installed
 libfreerdp-gdi1.1 : Depends: libfreerdp-codec1.1 (>= 1.1.0~beta1+git20130629) but it is not installed
 libfreerdp-plugins-standard : Depends: libwinpr-sysinfo0.1 (>= 1.1.0~beta1+git20130629) but it is not installed
 libgail-3-0 : Depends: libgtk-3-0 (= 3.10.8-0ubuntu1.6) but 3.18.9-1ubuntu3.1 is installed
 libglib-perl : Depends: perlapi-5.18.1 but it is not installable
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.40.2-0ubuntu1) but 2.48.1-1~ubuntu16.04.1 is installed
 libglib2.0-dev : Depends: libglib2.0-0 (= 2.40.2-0ubuntu1) but 2.48.1-1~ubuntu16.04.1 is installed
 libgnome2-canvas-perl : Depends: perlapi-5.18.1 but it is not installable
 libgnome2-perl : Depends: perlapi-5.18.1 but it is not installable
 libgnome2-vfs-perl : Depends: perlapi-5.18.1 but it is not installable
 libgnome2-wnck-perl : Depends: perlapi-5.18.1 but it is not installable
 libgnutls28 : Depends: libhogweed2 (>= 2.7) but it is not installable
               Depends: libnettle4 (>= 2.7) but it is not installable
 libgoo-canvas-perl : Depends: perlapi-5.18.1 but it is not installable
 libgtk-3-0-dbg : Depends: libgtk-3-0 (= 3.10.8-0ubuntu1.6) but 3.18.9-1ubuntu3.1 is installed
 libgtk-3-dev : Depends: libgtk-3-0 (= 3.10.8-0ubuntu1.6) but 3.18.9-1ubuntu3.1 is installed
                Depends: gir1.2-gtk-3.0 (= 3.10.8-0ubuntu1.6) but 3.18.9-1ubuntu3.1 is installed
 libgtk2-appindicator-perl : Depends: perlapi-5.18.1 but it is not installable
 libgtk2-gladexml-perl : Depends: perlapi-5.18.1 but it is not installable
 libgtk2-imageview-perl : Depends: perlapi-5.18.1 but it is not installable
 libgtk2-perl : Depends: perlapi-5.18.2 but it is not installable
 libgtk2-unique-perl : Depends: perlapi-5.18.1 but it is not installable
 libguard-perl : Depends: perlapi-5.18.1 but it is not installable
 libhtml-parser-perl : Depends: perlapi-5.18.1 but it is not installable
 libimage-imlib2-perl : Depends: perlapi-5.18.1 but it is not installable
 libio-pty-perl : Depends: perlapi-5.18.1 but it is not installable
 libjson-xs-perl : Depends: perlapi-5.18.1 but it is not installable
 libk3b6 : Depends: libtag1c2a (>= 1.5) but it is not installable
 libkface2 : Depends: libopencv-contrib2.4 but it is not installable
             Depends: libopencv-core2.4 but it is not installable
             Depends: libopencv-imgproc2.4 but it is not installable
             Depends: libopencv-objdetect2.4 but it is not installable
 libkfilemetadata4 : Depends: libtag1c2a (>= 1.5) but it is not installable
 liblist-moreutils-perl : Depends: perlapi-5.18.1 but it is not installable
 liblocale-gettext-perl : PreDepends: perlapi-5.18.1 but it is not installable
 libmusicbrainz-discid-perl : Depends: perlapi-5.18.1 but it is not installable
 libnet-dbus-perl : Depends: perlapi-5.18.1 but it is not installable
 libnet-dns-perl : Depends: perlapi-5.18.1 but it is not installable
 libnet-libidn-perl : Depends: perlapi-5.18.1 but it is not installable
 libnet-ssleay-perl : Depends: perlapi-5.18.2 but it is not installable
 libopencolorio1v5 : Depends: libtinyxml2.6.2v5 but it is not installed
 libopenimageio1.3 : Depends: libopencolorio1 but it is not installable
                     Depends: libopencv-highgui2.4 but it is not installable
 libpackage-stash-xs-perl : Depends: perlapi-5.18.1 but it is not installable
 libpango-perl : Depends: perlapi-5.18.1 but it is not installable
 libparams-classify-perl : Depends: perlapi-5.18.1 but it is not installable
 libparams-util-perl : Depends: perlapi-5.18.1 but it is not installable
 libparams-validate-perl : Depends: perlapi-5.18.1 but it is not installable
 libperl-dev : Depends: perl (= 5.18.2-2ubuntu1.1) but 5.22.1-9 is installed
 libperl5.18 : Depends: perl-base (= 5.18.2-2ubuntu1.1) but 5.22.1-9 is installed
 libperlio-gzip-perl : Depends: perlapi-5.18.1 but it is not installable
 libproc-processtable-perl : Depends: perlapi-5.18.1 but it is not installable
 libpurple0 : Depends: perlapi-5.18.2 but it is not installable
 libreoffice : Depends: libreoffice-java-common (>= 1:5.1.4~) but 1:4.2.8-0ubuntu4 is installed
 libreoffice-base : Depends: libreoffice-base-drivers (= 1:5.1.4-0ubuntu1) but 1:4.2.8-0ubuntu4 is installed
                    Recommends: libreoffice-java-common (>= 1:5.1.4~) but 1:4.2.8-0ubuntu4 is installed
 libreoffice-calc : Depends: libetonyek-0.1-1 but it is not installed
                    Depends: libmwaw-0.3-3 but it is not installed
                    Depends: libodfgen-0.1-1 but it is not installed
                    Depends: liborcus-0.10-0v5 (>= 0.9.2-4ubuntu2) but it is not installed
                    Depends: librevenge-0.0-0 but it is not installed
                    Depends: libwps-0.4-4 but it is not installed
 libreoffice-core : Depends: libclucene-contribs1v5 (>= 2.3.3.4) but it is not installed
                    Depends: libclucene-core1v5 (>= 2.3.3.4) but it is not installed
                    Depends: libcmis-0.5-5v5 but it is not installed
                    Depends: libeot0 but it is not installed
                    Depends: librevenge-0.0-0 but it is not installed
 libreoffice-draw : Depends: libcdr-0.1-1 but it is not installed
                    Depends: libfreehand-0.1-1 but it is not installed
                    Depends: libmspub-0.1-1 but it is not installed
                    Depends: libmwaw-0.3-3 but it is not installed
                    Depends: libodfgen-0.1-1 but it is not installed
                    Depends: libpagemaker-0.0-0 (>= 0.0) but it is not installed
                    Depends: librevenge-0.0-0 but it is not installed
                    Depends: libvisio-0.1-1 but it is not installed
                    Depends: libwpg-0.3-3 but it is not installed
 libreoffice-impress : Depends: libetonyek-0.1-1 but it is not installed
                       Depends: libmwaw-0.3-3 but it is not installed
                       Depends: libodfgen-0.1-1 but it is not installed
                       Depends: librevenge-0.0-0 but it is not installed
 libreoffice-writer : Depends: libabw-0.1-1v5 but it is not installed
                      Depends: libe-book-0.1-1 but it is not installed
                      Depends: libetonyek-0.1-1 but it is not installed
                      Depends: libmwaw-0.3-3 but it is not installed
                      Depends: libodfgen-0.1-1 but it is not installed
                      Depends: librevenge-0.0-0 but it is not installed
                      Depends: libwpd-0.10-10 but it is not installed
                      Depends: libwpg-0.3-3 but it is not installed
                      Depends: libwps-0.4-4 but it is not installed
 libsocket6-perl : Depends: perlapi-5.18.2 but it is not installable
 libsub-identify-perl : Depends: perlapi-5.18.1 but it is not installable
 libsub-name-perl : Depends: perlapi-5.18.1 but it is not installable
 libterm-readkey-perl : Depends: perlapi-5.18.1 but it is not installable
 libterm-readline-gnu-perl : Depends: perlapi-5.18.1 but it is not installable
 libtext-charwidth-perl : Depends: perlapi-5.18.1 but it is not installable
 libtext-csv-xs-perl : Depends: perlapi-5.18.1 but it is not installable
 libtext-iconv-perl : Depends: perlapi-5.18.1 but it is not installable
 libtext-soundex-perl : Depends: perlapi-5.18.1 but it is not installable
 libtotem0 : Depends: libcogl15 (>= 1.15.8) but it is not installable
 libuuid-perl : Depends: perlapi-5.18.1 but it is not installable
 libwinpr-sspi0.1 : Depends: libwinpr-sysinfo0.1 (>= 1.1.0~beta1+git20130629) but it is not installed
 libwinpr-utils0.1 : Depends: libwinpr-sysinfo0.1 (>= 1.1.0~beta1+git20130629) but it is not installed
 libxml-libxml-perl : Depends: perlapi-5.18.2 but it is not installable
 libxml-parser-perl : Depends: perlapi-5.18.1 but it is not installable
 mysql-workbench : Depends: libctemplate2 but it is not installable
                   Depends: libmysqlcppconn7 (>= 1.1.3) but it is not installable
                   Depends: libpcrecpp0 (>= 7.7) but it is not installable
 perlmagick : Depends: perlapi-5.18.2 but it is not installable
 pidgin : Depends: perlapi-5.18.2 but it is not installable
 python-gi-cairo : Depends: python-gi (= 3.12.0-1ubuntu1) but 3.20.0-0ubuntu1 is installed
 remmina-plugin-rdp : Depends: libfreerdp1 (>= 1.0~beta5) but it is not installable
 rhythmbox : Depends: python3 (< 3.5) but 3.5.1-3 is installed
             Depends: gir1.2-rb-3.0 (= 3.0.2-0ubuntu2) but 3.3-1ubuntu7 is installed
 rhythmbox-plugin-magnatune : Depends: rhythmbox (= 3.3-1ubuntu7) but 3.0.2-0ubuntu2 is installed
 rhythmbox-plugins : Depends: rhythmbox (= 3.3-1ubuntu7) but 3.0.2-0ubuntu2 is installed
 totem : Depends: libcogl15 (>= 1.15.8) but it is not installable
         Depends: totem-common (= 3.10.1-1ubuntu4) but 3.18.1-1ubuntu4 is installed
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not installable
                        Depends: libcheese7 (>= 3.0.1) but it is not installable
 unity-settings-daemon : Depends: gnome-settings-daemon-schemas (< 3.10) but 3.18.2-0ubuntu3.1 is installed
 vlc-nox : Depends: libebml4 but it is not installable
           Depends: libfreerdp1 (>= 1.0.1) but it is not installable
           Depends: libmatroska6 but it is not installable
           Depends: libsidplay2 but it is not installable
           Depends: libtag1c2a (>= 1.7) but it is not installable
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```How can I correct these errors.  I have used ppa-purge on all my PPAs  and ran the following commands before starting the upgrade process:```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo do-release-upgrade
```

---

### Post by cscj01 on 2017-01-15
Well, I removed every package that I had installed above and beyond what came with 14.04.  No luck.  I still have the following:```
Errors were encountered while processing:
 hostname
E: Sub-process /usr/bin/dpkg returned an error code (1)
butch@Car-Photo-Ubuntu:~$ sudo apt-get remove libcogl-pango15 libcwidget3 libflickrnet2.2-cil libmono-cairo2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-messaging2.0-cil libmono-posix2.0-cil libmono-security2.0-cil
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 bogofilter-bdb : Depends: libgsl0ldbl (>= 1.9) but it is not installable
 frei0r-plugins : Depends: libopencv-core2.4 but it is not installable
                  Depends: libopencv-imgproc2.4 but it is not installable
                  Depends: libopencv-objdetect2.4 but it is not installable
 gdb : Depends: libbabeltrace-ctf1 (>= 1.2.1) but it is not going to be installed
       Depends: libbabeltrace1 (>= 1.2.1) but it is not going to be installed
       Recommends: gdbserver but it is not going to be installed
 gnupg2 : Depends: gnupg-agent (= 2.0.22-3ubuntu1.3)
 gstreamer1.0-clutter : Depends: libcogl15 (>= 1.15.8) but it is not installable
 libalgorithm-diff-xs-perl : Depends: perlapi-5.18.1 but it is not installable
 libapt-pkg-perl : Depends: perlapi-5.18.1 but it is not installable
 libasync-interrupt-perl : Depends: perlapi-5.18.1 but it is not installable
 libbit-vector-perl : Depends: perlapi-5.18.1 but it is not installable
 libcairo-perl : Depends: perlapi-5.18.1 but it is not installable
 libclone-perl : Depends: perlapi-5.18.1 but it is not installable
 libcompress-raw-lzma-perl : Depends: perlapi-5.18.1 but it is not installable
 libdate-calc-xs-perl : Depends: perlapi-5.18.1 but it is not installable
 libdatetime-perl : Depends: perlapi-5.18.1 but it is not installable
 libdbd-mysql-perl : Depends: perlapi-5.18.2 but it is not installable
 libdbi-perl : Depends: perlapi-5.18.1 but it is not installable
 libdevice-serialport-perl : Depends: perlapi-5.18.1 but it is not installable
 libevent-perl : Depends: perlapi-5.18.1 but it is not installable
 libfile-fcntllock-perl : Depends: perlapi-5.18.1 but it is not installable
 libglib-perl : Depends: perlapi-5.18.1 but it is not installable
 libgnome2-canvas-perl : Depends: perlapi-5.18.1 but it is not installable
 libgnome2-perl : Depends: perlapi-5.18.1 but it is not installable
 libgnome2-vfs-perl : Depends: perlapi-5.18.1 but it is not installable
 libgtk2-gladexml-perl : Depends: perlapi-5.18.1 but it is not installable
 libgtk2-perl : Depends: perlapi-5.18.2 but it is not installable
 libguard-perl : Depends: perlapi-5.18.1 but it is not installable
 libhtml-parser-perl : Depends: perlapi-5.18.1 but it is not installable
 libimage-imlib2-perl : Depends: perlapi-5.18.1 but it is not installable
 libio-pty-perl : Depends: perlapi-5.18.1 but it is not installable
 libjson-xs-perl : Depends: perlapi-5.18.1 but it is not installable
 liblist-moreutils-perl : Depends: perlapi-5.18.1 but it is not installable
 libmono-system-data2.0-cil : Depends: libmono-corlib2.0-cil (>= 3.2.8) but it is not installable
                              Depends: libmono-data-tds2.0-cil (>= 3.0.6) but it is not going to be installed
                              Depends: libmono-system2.0-cil (>= 3.2.1) but it is not installable
 libmono-system-messaging2.0-cil : Depends: libmono-corlib2.0-cil (>= 3.2.8) but it is not installable
                                   Depends: libmono-messaging2.0-cil (>= 3.0.6) but it is not going to be installed
                                   Depends: libmono-system2.0-cil (>= 3.2.1) but it is not installable
 libmono-system-runtime2.0-cil : Depends: libmono-corlib2.0-cil (>= 3.2.8) but it is not installable
                                 Depends: libmono-system-web2.0-cil (>= 2.10.3) but it is not installable
                                 Depends: libmono-system2.0-cil (>= 3.2.1) but it is not installable
 libndesk-dbus1.0-cil : Depends: libmono-corlib4.0-cil (>= 2.10.1) but it is not installable
 libnet-dbus-perl : Depends: perlapi-5.18.1 but it is not installable
 libnet-dns-perl : Depends: perlapi-5.18.1 but it is not installable
 libnet-libidn-perl : Depends: perlapi-5.18.1 but it is not installable
 libnet-ssleay-perl : Depends: perlapi-5.18.2 but it is not installable
 libnotify0.4-cil : Depends: libmono-corlib4.0-cil (>= 2.10.1) but it is not installable
 libpackage-stash-xs-perl : Depends: perlapi-5.18.1 but it is not installable
 libpango-perl : Depends: perlapi-5.18.1 but it is not installable
 libparams-classify-perl : Depends: perlapi-5.18.1 but it is not installable
 libparams-util-perl : Depends: perlapi-5.18.1 but it is not installable
 libparams-validate-perl : Depends: perlapi-5.18.1 but it is not installable
 libperl5.18 : Depends: perl-base (= 5.18.2-2ubuntu1.1) but 5.22.1-9 is to be installed
 libperlio-gzip-perl : Depends: perlapi-5.18.1 but it is not installable
 libsocket6-perl : Depends: perlapi-5.18.2 but it is not installable
 libsub-identify-perl : Depends: perlapi-5.18.1 but it is not installable
 libsub-name-perl : Depends: perlapi-5.18.1 but it is not installable
 libterm-readkey-perl : Depends: perlapi-5.18.1 but it is not installable
 libterm-readline-gnu-perl : Depends: perlapi-5.18.1 but it is not installable
 libtext-charwidth-perl : Depends: perlapi-5.18.1 but it is not installable
 libtext-csv-xs-perl : Depends: perlapi-5.18.1 but it is not installable
 libtext-soundex-perl : Depends: perlapi-5.18.1 but it is not installable
 libtotem0 : Depends: libcogl15 (>= 1.15.8) but it is not installable
 libuuid-perl : Depends: perlapi-5.18.1 but it is not installable
 libxml-libxml-perl : Depends: perlapi-5.18.2 but it is not installable
 libxml-parser-perl : Depends: perlapi-5.18.1 but it is not installable
 mono-2.0-gac : Depends: libmono-corlib2.0-cil (>= 3.2.8) but it is not installable
                Depends: libmono-security2.0-cil (>= 3.0.6) but it is not going to be installed
 nvidia-349-uvm : Depends: nvidia-349 but it is not installable
 totem : Depends: libcogl15 (>= 1.15.8) but it is not installable
         Depends: totem-common (= 3.10.1-1ubuntu4) but 3.18.1-1ubuntu4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```Is there anyone who can help?

---

### Post by RobGoss on 2017-01-15
Hello and welcome, It's probably a good idea to do a clean installation of **16.04 **trying to upgrade from one distribution and skipping another will have all kind of issues such as this. Make a backup of all your important files and data and do a clean installation of 16.04

---

### Post by Autodave on 2017-01-15
I'm w/RobGoss: copy the files you need to keep and do a clean install. I have never had any luck upgrading the OS.

---

### Post by RobGoss on 2017-01-15
The chances of you breaking your system are very high do to the fact that not upgrading from one distribution to another are not being done correctly skipping distributions only results with error and broken packages I have also never had luck upgrading distributions I always do clean installations

---

### Post by cscj01 on 2017-01-15
I have a few questions about a clean install since I have nnot done one since the first install of Ubuntu masny versions ago.

I have backed up /home.  If I do a clean install, can I copy that over the new /home?
I use NFS V3 and MySQL.  Both have been customized. Should I back up any files associated with these two packages?
I could make that last question "What system files should I back up?  Is there a guide somewhere for the files that need backing up?

Thank you for your responses.  I was at the point of considering a clean install, but I was unsure of how to proceed.

---

### Post by RobGoss on 2017-01-15
Depending are what data you want to save backing up your home folder should work it will have your documents and pictures and so on. I my self don't keep much on any of my machines so when I do a clean installation I do not create any backups because I have anything of value on a external dive for safe keeping. 

As far as application I have a list of apps I use on multi machines and just install them after the new installation is complete 

I'm sure someone else might have a bit more details on how to save important data

---

### Post by cscj01 on 2017-01-15
Well, I have a system backup and a Live DVD of 16.04.  I have had no luck upgrading, so I am going to try to make this happen with a fresh install.  Worst case is, I have to restore my backup.  Nothing new there.  Thanks for the responses.

---

### Post by RobGoss on 2017-01-15
You're most welcome, as long as this is a single boot and not a dual you should be OK 

Best of luck

---

### Post by cscj01 on 2017-01-17
Well, I backed up my entire system on a USB drive, used a Live DVD to install 16.04 as a clean install.  I am in the process of getting things back where they were on 14.04 from an application standpoint.  I am having a problem that I don't seem to be able to get past.  I cannot connect to my database because I get the following message:> ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)This followed the following command```
sudo mysql -u root
```I was asked for a password that I do not know.  Additionally, I must close the terminal session and start over in a new session to try again.  If I enter ```
sudo mysql -u root
```in the same session, I get the error message with no prompt.  Anyone have any insight into this issue.  Maybe I need to open a new thread, huh?

---

