---
title: "Apt-get fail after attempted upgrade to 14.04"
date: 2014-07-07
forum: Installation &amp; Upgrades
---

### Post by Blake_Stamps on 2014-07-07
I was attempting to upgrade to 14.04 over ssh... the upgrade seemed to have completed, but I lost my connection and was forced to re-boot the machine remotely. After logging back on, apt-get contains numerous errors when trying to upgrade, install, or remove any packages- 

```
lab@CURIE:~$ sudo apt-get install libperl-devReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 bzip2 : Depends: libbz2-1.0 (= 1.0.6-4) but 1.0.6-5 is to be installed
 gdm : Depends: libgdm1 (= 3.10.0.1-0ubuntu3) but it is not going to be installed
       Depends: gir1.2-gdm-1.0 (= 3.10.0.1-0ubuntu3) but it is not going to be installed
 gnome-control-center : Depends: libgoa-1.0-0b (>= 3.5.90) but it is not going to be installed
                        Depends: libgoa-backend-1.0-1 (>= 3.10.0) but it is not going to be installed
                        Recommends: gnome-control-center-shared-data but it is not going to be installed
 gnome-power-manager : Depends: gnome-settings-daemon-schemas (>= 3.2) but it is not going to be installed
 gnome-session : Depends: gnome-session-bin (>= 3.9.90-0ubuntu12) but 3.9.90-0ubuntu3 is to be installed
                 Depends: gnome-session-common (= 3.9.90-0ubuntu12) but 3.9.90-0ubuntu3 is to be installed
 gnome-settings-daemon : Depends: libaccountsservice0 (>= 0.6.35-0ubuntu7) but 0.6.34-0ubuntu6 is to be installed
                         Depends: libgtk-3-0 (>= 3.9.10) but 3.8.6-0ubuntu3.1 is to be installed
                         Depends: gnome-settings-daemon-schemas (= 3.8.6.1-0ubuntu11.1) but it is not going to be installed
 gnome-shell : Depends: gir1.2-mutter-3.0 (>= 3.10.0) but 3.8.4-0ubuntu2 is to be installed
               Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
               Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
               Depends: libecal-1.2-16 (>= 3.5.91) but it is not going to be installed
               Depends: libedataserver-1.2-18 (>= 3.5.91) but it is not going to be installed
               Depends: libgjs0-libmozjs-24-0
               Depends: libgjs0e (>= 1.40.1) but it is not going to be installed
               Depends: libmozjs-24-0 but it is not going to be installed
               Depends: libmutter0c (>= 3.10) but it is not going to be installed
               Depends: libmutter0c (< 3.11) but it is not going to be installed
               Depends: gir1.2-gdm-1.0 but it is not going to be installed
 gvfs : Depends: gvfs-libs (= 1.20.1-1ubuntu1) but 1.18.2-0ubuntu1 is to be installed
 gvfs:i386 : Depends: gvfs-libs:i386 (= 1.20.1-1ubuntu1) but 1.18.2-0ubuntu1 is to be installed
 gvfs-backends : Depends: libsmbclient (>= 2:4.0.3+dfsg1) but 2:3.6.18-1ubuntu3.1 is to be installed
                 Depends: gvfs-libs (= 1.20.1-1ubuntu1) but 1.18.2-0ubuntu1 is to be installed
 gvfs-daemons : Depends: gvfs-libs (= 1.20.1-1ubuntu1) but 1.18.2-0ubuntu1 is to be installed
 gvfs-fuse : Depends: gvfs (= 1.18.2-0ubuntu1) but 1.20.1-1ubuntu1 is to be installed
 gvfs-libs : Depends: gvfs-common (= 1.18.2-0ubuntu1) but 1.20.1-1ubuntu1 is to be installed
 gvfs-libs:i386 : Depends: gvfs-common:i386 (= 1.18.2-0ubuntu1)
 libace-perl : Depends: perlapi-5.14.2 but it is not installable
 libalgorithm-diff-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libapache2-mod-perl2 : Depends: perlapi-5.14.2 but it is not installable
 libapparmor-perl : Depends: perlapi-5.14.2 but it is not installable
 libapt-pkg-perl : Depends: perlapi-5.14.2 but it is not installable
 libauthen-pam-perl : Depends: perlapi-5.14.2 but it is not installable
 libbio-scf-perl : Depends: perlapi-5.14.2 but it is not installable
 libbit-vector-perl : Depends: perlapi-5.14.2 but it is not installable
 libbsd-resource-perl : Depends: perlapi-5.14.2 but it is not installable
 libbz2-dev : Depends: libbz2-1.0 (= 1.0.6-4) but 1.0.6-5 is to be installed
 libcairo-perl : Depends: perlapi-5.14.2 but it is not installable
 libclass-c3-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libclass-load-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libclone-perl : Depends: perlapi-5.14.2 but it is not installable
 libcommon-sense-perl : Depends: perl (>= 5.18.2) but 5.14.2-21build1 is to be installed
 libconvert-binary-c-perl : Depends: perlapi-5.14.2 but it is not installable
 libcrypt-ssleay-perl : Depends: perlapi-5.14.2 but it is not installable
 libdate-calc-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libdbd-mysql-perl : Depends: perlapi-5.14.2 but it is not installable
 libdbd-pg-perl : Depends: perlapi-5.14.2 but it is not installable
 libdbd-sqlite3-perl : Depends: perlapi-5.14.2 but it is not installable
 libdbi-perl : Depends: perlapi-5.14.2 but it is not installable
 libdrm-dev : Depends: libdrm2 (= 2.4.46-1ubuntu1) but 2.4.52-1 is to be installed
 libfcgi-perl : Depends: perlapi-5.14.2 but it is not installable
 libffi-dev : Depends: libffi6 (= 3.0.13-4) but 3.1~rc1+r3.0.13-12 is to be installed
 libfile-fcntllock-perl : Depends: perlapi-5.14.2 but it is not installable
 libgd-gd2-perl : Depends: perlapi-5.14.2 but it is not installable
 libglib-perl : Depends: perlapi-5.14.2 but it is not installable
 libgnutls-openssl27 : Depends: libgnutls26 (= 2.12.23-1ubuntu4) but 2.12.23-12ubuntu2.1 is to be installed
 libgtk2-perl : Depends: perlapi-5.14.2 but it is not installable
 libhtml-parser-perl : Depends: perlapi-5.14.2 but it is not installable
 libio-pty-perl : Depends: perlapi-5.14.2 but it is not installable
 libipc-sharelite-perl : Depends: perlapi-5.14.2 but it is not installable
 libjson-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 liblist-moreutils-perl : Depends: perlapi-5.14.2 but it is not installable
 liblocale-gettext-perl : PreDepends: perlapi-5.14.2 but it is not installable
 libmoose-perl : Depends: perlapi-5.14.2 but it is not installable
 libnet-dbus-perl : Depends: perlapi-5.14.2 but it is not installable
 libnet-dns-perl : Depends: perlapi-5.14.2 but it is not installable
 libnet-ssleay-perl : Depends: perlapi-5.14.2 but it is not installable
 libossp-uuid-perl : Depends: perlapi-5.14.2 but it is not installable
 libpackage-stash-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libpango-perl : Depends: perlapi-5.14.2 but it is not installable
 libparams-classify-perl : Depends: perlapi-5.14.2 but it is not installable
 libparams-util-perl : Depends: perlapi-5.14.2 but it is not installable
 libperl-dev : Depends: perl (= 5.18.2-2ubuntu1) but 5.14.2-21build1 is to be installed
               Depends: libperl5.18 (= 5.18.2-2ubuntu1) but it is not going to be installed
 libperl5.14 : Depends: perl-base (= 5.14.2-21build1) but 5.18.2-2ubuntu1 is to be installed
 libperlio-gzip-perl : Depends: perlapi-5.14.2 but it is not installable
 libpurple0 : Depends: perlapi-5.14.2 but it is not installable
 libsocket6-perl : Depends: perlapi-5.14.2 but it is not installable
 libstring-approx-perl : Depends: perlapi-5.14.2 but it is not installable
 libsub-identify-perl : Depends: perlapi-5.14.2 but it is not installable
 libsub-name-perl : Depends: perlapi-5.14.2 but it is not installable
 libterm-readkey-perl : Depends: perlapi-5.14.2 but it is not installable
 libtext-charwidth-perl : Depends: perlapi-5.14.2 but it is not installable
 libtext-iconv-perl : Depends: perlapi-5.14.2 but it is not installable
 libunicode-map-perl : Depends: perlapi-5.14.2 but it is not installable
 libuuid-perl : Depends: perlapi-5.14.2 but it is not installable
 libvariable-magic-perl : Depends: perlapi-5.14.2 but it is not installable
 libx11-dev : Depends: libx11-6 (= 2:1.6.1-1ubuntu1) but 2:1.6.2-1ubuntu2 is to be installed
 libxcb1-dev : Depends: libxcb1 (= 1.9.1-3ubuntu1) but 1.10-2ubuntu1 is to be installed
 libxml-libxml-perl : Depends: perlapi-5.14.2 but it is not installable
 libxml-libxslt-perl : Depends: perlapi-5.14.2 but it is not installable
 libxml-parser-perl : Depends: perlapi-5.14.2 but it is not installable
 libyaml-syck-perl : Depends: perlapi-5.14.2 but it is not installable
 nautilus : Depends: libgtk-3-0 (>= 3.9.12) but 3.8.6-0ubuntu3.1 is to be installed
            Depends: nautilus-data (>= 1:3.10) but 1:3.8.2-0ubuntu2.2 is to be installed
 nautilus-sendto : Depends: libedataserver-1.2-18 (>= 3.5.91) but it is not going to be installed
 nautilus-sendto-empathy : Depends: empathy (= 3.8.6-0ubuntu9.1) but 3.8.4-1ubuntu2 is to be installed
                           Depends: empathy-common (= 3.8.6-0ubuntu9.1) but 3.8.4-1ubuntu2 is to be installed
 network-manager : Depends: libmm-glib0 (>= 0.7.991) but it is not going to be installed
 network-manager-gnome : Depends: libmm-glib0 (>= 0.7.991) but it is not going to be installed
                         Depends: libnm-gtk0 (= 0.9.8.8-0ubuntu4.1) but 0.9.8.0-1ubuntu5.1 is to be installed
 perl : Depends: perl-base (= 5.14.2-21build1) but 5.18.2-2ubuntu1 is to be installed
 perl-tk : Depends: perlapi-5.14.2 but it is not installable
 rhythmbox : Depends: librhythmbox-core8 (= 3.0.2-0ubuntu2) but it is not going to be installed
             Depends: libtotem-plparser18 (>= 3.10.0) but it is not going to be installed
             Depends: python3 (>= 3.4~) but 3.3.2-14ubuntu1 is to be installed
             Depends: python3.4 but it is not going to be installed
             Depends: gir1.2-rb-3.0 (= 3.0.2-0ubuntu2) but 2.99.1-0ubuntu1 is to be installed
 rhythmbox-plugin-cdrecorder : Depends: librhythmbox-core8 (>= 3.0) but it is not going to be installed
 rhythmbox-plugin-magnatune : Depends: gir1.2-secret-1 but it is not going to be installed
 rhythmbox-plugins : Depends: librhythmbox-core8 (= 3.0.2-0ubuntu2) but it is not going to be installed
                     Depends: libtotem-plparser18 (>= 3.10.0) but it is not going to be installed
                     Depends: python3 (>= 3.4~) but 3.3.2-14ubuntu1 is to be installed
                     Depends: python3.4 but it is not going to be installed
                     Depends: gir1.2-rb-3.0 (= 3.0.2-0ubuntu2) but 2.99.1-0ubuntu1 is to be installed
                     Depends: python3-mako but it is not going to be installed
 tzdata-java : Depends: tzdata (= 2013g-0ubuntu1) but 2014e-0ubuntu0.14.04 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

When I then try to use apt-get -f install, I receive this error- 

```
lab@CURIE:~$ sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 bzip2 : Depends: libbz2-1.0 (= 1.0.6-4) but 1.0.6-5 is installed
 gdm : Depends: libgdm1 (= 3.10.0.1-0ubuntu3) but it is not installed
       Depends: gir1.2-gdm-1.0 (= 3.10.0.1-0ubuntu3) but it is not installed
 gnome-control-center : Depends: libgoa-1.0-0b (>= 3.5.90) but it is not installed
                        Depends: libgoa-backend-1.0-1 (>= 3.10.0) but it is not installed
                        Recommends: gnome-control-center-shared-data but it is not installed
 gnome-power-manager : Depends: gnome-settings-daemon-schemas (>= 3.2) but it is not installed
 gnome-session : Depends: gnome-session-bin (>= 3.9.90-0ubuntu12) but 3.9.90-0ubuntu3 is installed
                 Depends: gnome-session-common (= 3.9.90-0ubuntu12) but 3.9.90-0ubuntu3 is installed
 gnome-settings-daemon : Depends: libaccountsservice0 (>= 0.6.35-0ubuntu7) but 0.6.34-0ubuntu6 is installed
                         Depends: libgtk-3-0 (>= 3.9.10) but 3.8.6-0ubuntu3.1 is installed
                         Depends: gnome-settings-daemon-schemas (= 3.8.6.1-0ubuntu11.1) but it is not installed
 gnome-shell : Depends: gir1.2-mutter-3.0 (>= 3.10.0) but 3.8.4-0ubuntu2 is installed
               Depends: libcogl-pango15 (>= 1.15.8) but it is not installed
               Depends: libcogl15 (>= 1.15.8) but it is not installed
               Depends: libecal-1.2-16 (>= 3.5.91) but it is not installed
               Depends: libedataserver-1.2-18 (>= 3.5.91) but it is not installed
               Depends: libgjs0-libmozjs-24-0
               Depends: libgjs0e (>= 1.40.1) but it is not installed
               Depends: libmozjs-24-0 but it is not installed
               Depends: libmutter0c (>= 3.10) but it is not installed
               Depends: libmutter0c (< 3.11) but it is not installed
               Depends: gir1.2-gdm-1.0 but it is not installed
 gvfs : Depends: gvfs-libs (= 1.20.1-1ubuntu1) but 1.18.2-0ubuntu1 is installed
 gvfs:i386 : Depends: gvfs-libs:i386 (= 1.20.1-1ubuntu1) but 1.18.2-0ubuntu1 is installed
 gvfs-backends : Depends: libsmbclient (>= 2:4.0.3+dfsg1) but 2:3.6.18-1ubuntu3.1 is installed
                 Depends: gvfs-libs (= 1.20.1-1ubuntu1) but 1.18.2-0ubuntu1 is installed
 gvfs-daemons : Depends: gvfs-libs (= 1.20.1-1ubuntu1) but 1.18.2-0ubuntu1 is installed
 gvfs-fuse : Depends: gvfs (= 1.18.2-0ubuntu1) but 1.20.1-1ubuntu1 is installed
 gvfs-libs : Depends: gvfs-common (= 1.18.2-0ubuntu1) but 1.20.1-1ubuntu1 is installed
 gvfs-libs:i386 : Depends: gvfs-common:i386 (= 1.18.2-0ubuntu1)
 libace-perl : Depends: perlapi-5.14.2 but it is not installable
 libalgorithm-diff-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libapache2-mod-perl2 : Depends: perlapi-5.14.2 but it is not installable
 libapparmor-perl : Depends: perlapi-5.14.2 but it is not installable
 libapt-pkg-perl : Depends: perlapi-5.14.2 but it is not installable
 libauthen-pam-perl : Depends: perlapi-5.14.2 but it is not installable
 libbio-scf-perl : Depends: perlapi-5.14.2 but it is not installable
 libbit-vector-perl : Depends: perlapi-5.14.2 but it is not installable
 libbsd-resource-perl : Depends: perlapi-5.14.2 but it is not installable
 libbz2-dev : Depends: libbz2-1.0 (= 1.0.6-4) but 1.0.6-5 is installed
 libcairo-perl : Depends: perlapi-5.14.2 but it is not installable
 libclass-c3-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libclass-load-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libclone-perl : Depends: perlapi-5.14.2 but it is not installable
 libcommon-sense-perl : Depends: perl (>= 5.18.2) but 5.14.2-21build1 is installed
 libconvert-binary-c-perl : Depends: perlapi-5.14.2 but it is not installable
 libcrypt-ssleay-perl : Depends: perlapi-5.14.2 but it is not installable
 libdate-calc-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libdbd-mysql-perl : Depends: perlapi-5.14.2 but it is not installable
 libdbd-pg-perl : Depends: perlapi-5.14.2 but it is not installable
 libdbd-sqlite3-perl : Depends: perlapi-5.14.2 but it is not installable
 libdbi-perl : Depends: perlapi-5.14.2 but it is not installable
 libdrm-dev : Depends: libdrm2 (= 2.4.46-1ubuntu1) but 2.4.52-1 is installed
 libfcgi-perl : Depends: perlapi-5.14.2 but it is not installable
 libffi-dev : Depends: libffi6 (= 3.0.13-4) but 3.1~rc1+r3.0.13-12 is installed
 libfile-fcntllock-perl : Depends: perlapi-5.14.2 but it is not installable
 libgd-gd2-perl : Depends: perlapi-5.14.2 but it is not installable
 libglib-perl : Depends: perlapi-5.14.2 but it is not installable
 libgnutls-openssl27 : Depends: libgnutls26 (= 2.12.23-1ubuntu4) but 2.12.23-12ubuntu2.1 is installed
 libgtk2-perl : Depends: perlapi-5.14.2 but it is not installable
 libhtml-parser-perl : Depends: perlapi-5.14.2 but it is not installable
 libio-pty-perl : Depends: perlapi-5.14.2 but it is not installable
 libipc-sharelite-perl : Depends: perlapi-5.14.2 but it is not installable
 libjson-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 liblist-moreutils-perl : Depends: perlapi-5.14.2 but it is not installable
 liblocale-gettext-perl : PreDepends: perlapi-5.14.2 but it is not installable
 libmoose-perl : Depends: perlapi-5.14.2 but it is not installable
 libnet-dbus-perl : Depends: perlapi-5.14.2 but it is not installable
 libnet-dns-perl : Depends: perlapi-5.14.2 but it is not installable
 libnet-ssleay-perl : Depends: perlapi-5.14.2 but it is not installable
 libossp-uuid-perl : Depends: perlapi-5.14.2 but it is not installable
 libpackage-stash-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libpango-perl : Depends: perlapi-5.14.2 but it is not installable
 libparams-classify-perl : Depends: perlapi-5.14.2 but it is not installable
 libparams-util-perl : Depends: perlapi-5.14.2 but it is not installable
 libperl5.14 : Depends: perl-base (= 5.14.2-21build1) but 5.18.2-2ubuntu1 is installed
 libperlio-gzip-perl : Depends: perlapi-5.14.2 but it is not installable
 libpurple0 : Depends: perlapi-5.14.2 but it is not installable
 libsocket6-perl : Depends: perlapi-5.14.2 but it is not installable
 libstring-approx-perl : Depends: perlapi-5.14.2 but it is not installable
 libsub-identify-perl : Depends: perlapi-5.14.2 but it is not installable
 libsub-name-perl : Depends: perlapi-5.14.2 but it is not installable
 libterm-readkey-perl : Depends: perlapi-5.14.2 but it is not installable
 libtext-charwidth-perl : Depends: perlapi-5.14.2 but it is not installable
 libtext-iconv-perl : Depends: perlapi-5.14.2 but it is not installable
 libunicode-map-perl : Depends: perlapi-5.14.2 but it is not installable
 libuuid-perl : Depends: perlapi-5.14.2 but it is not installable
 libvariable-magic-perl : Depends: perlapi-5.14.2 but it is not installable
 libx11-dev : Depends: libx11-6 (= 2:1.6.1-1ubuntu1) but 2:1.6.2-1ubuntu2 is installed
 libxcb1-dev : Depends: libxcb1 (= 1.9.1-3ubuntu1) but 1.10-2ubuntu1 is installed
 libxml-libxml-perl : Depends: perlapi-5.14.2 but it is not installable
 libxml-libxslt-perl : Depends: perlapi-5.14.2 but it is not installable
 libxml-parser-perl : Depends: perlapi-5.14.2 but it is not installable
 libyaml-syck-perl : Depends: perlapi-5.14.2 but it is not installable
 nautilus : Depends: libgtk-3-0 (>= 3.9.12) but 3.8.6-0ubuntu3.1 is installed
            Depends: nautilus-data (>= 1:3.10) but 1:3.8.2-0ubuntu2.2 is installed
 nautilus-sendto : Depends: libedataserver-1.2-18 (>= 3.5.91) but it is not installed
 nautilus-sendto-empathy : Depends: empathy (= 3.8.6-0ubuntu9.1) but 3.8.4-1ubuntu2 is installed
                           Depends: empathy-common (= 3.8.6-0ubuntu9.1) but 3.8.4-1ubuntu2 is installed
 network-manager : Depends: libmm-glib0 (>= 0.7.991) but it is not installed
 network-manager-gnome : Depends: libmm-glib0 (>= 0.7.991) but it is not installed
                         Depends: libnm-gtk0 (= 0.9.8.8-0ubuntu4.1) but 0.9.8.0-1ubuntu5.1 is installed
 perl : Depends: perl-base (= 5.14.2-21build1) but 5.18.2-2ubuntu1 is installed
 perl-tk : Depends: perlapi-5.14.2 but it is not installable
 rhythmbox : Depends: librhythmbox-core8 (= 3.0.2-0ubuntu2) but it is not installed
             Depends: libtotem-plparser18 (>= 3.10.0) but it is not installed
             Depends: python3 (>= 3.4~) but 3.3.2-14ubuntu1 is installed
             Depends: python3.4 but it is not installed
             Depends: gir1.2-rb-3.0 (= 3.0.2-0ubuntu2) but 2.99.1-0ubuntu1 is installed
 rhythmbox-plugin-cdrecorder : Depends: librhythmbox-core8 (>= 3.0) but it is not installed
 rhythmbox-plugin-magnatune : Depends: gir1.2-secret-1 but it is not installed
 rhythmbox-plugins : Depends: librhythmbox-core8 (= 3.0.2-0ubuntu2) but it is not installed
                     Depends: libtotem-plparser18 (>= 3.10.0) but it is not installed
                     Depends: python3 (>= 3.4~) but 3.3.2-14ubuntu1 is installed
                     Depends: python3.4 but it is not installed
                     Depends: gir1.2-rb-3.0 (= 3.0.2-0ubuntu2) but 2.99.1-0ubuntu1 is installed
                     Depends: python3-mako but it is not installed
 tzdata-java : Depends: tzdata (= 2013g-0ubuntu1) but 2014e-0ubuntu0.14.04 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```

I've tried the combo of 

sudo apt-get update
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

also with no success. Any help would be greatly appreciated.

---

### Post by deadflowr on 2014-07-07
Have you tried a simple 
```
sudo apt-get update 
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
post the output for those.

---

### Post by Blake_Stamps on 2014-07-07
Thanks for the reply! 

```
lab@CURIE:~$ sudo apt-get update[sudo] password for lab: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Ign [http://download.webmin.com](http://download.webmin.com) sarge InRelease                                 
Get:1 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease [2,980 B]                 
Ign [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Get:2 [http://download.webmin.com](http://download.webmin.com) sarge Release.gpg [189 B]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://download.webmin.com](http://download.webmin.com) sarge Release                                   
Ign [http://download.webmin.com](http://download.webmin.com) sarge Release                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib Sources/DiffIndex                 
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg [933 B]        
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib amd64 Packages/DiffIndex          
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib i386 Packages/DiffIndex           
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [58.5 kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Sources/DiffIndex            
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages/DiffIndex     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages/DiffIndex      
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Sources                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release [58.6 kB]          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner amd64 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Hit [http://download.webmin.com](http://download.webmin.com) sarge/contrib Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://download.webmin.com](http://download.webmin.com) sarge/contrib amd64 Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Hit [http://download.webmin.com](http://download.webmin.com) sarge/contrib i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib Translation-en_US                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [81.5 kB]       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_US             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [14 B]    
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [60.1 kB]   
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [2,681 B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [216 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Sources                      
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages      
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US            
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [14 B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [153 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [7,397 B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [212 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [14 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [154 kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [7,569 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources [14 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources [14 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources [7,901 B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources [768 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages [14 B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages [14 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages [9,613 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages [619 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages [14 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages [14 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages [9,633 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [619 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en [6,104 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US   
Fetched 1,052 kB in 7s (140 kB/s)                                              
Can't locate Storable.pm in @INC (you may need to install the Storable module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/bin/apt-show-versions line 37.
BEGIN failed--compilation aborted at /usr/bin/apt-show-versions line 37.
W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: GPG error: [http://download.webmin.com](http://download.webmin.com) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D97A3AE911F63C51
E: Problem executing scripts APT::Update::Post-Invoke-Success 'test -x /usr/bin/apt-show-versions || exit 0 ; apt-show-versions -i'
E: Sub-process returned an error code
```

```
lab@CURIE:~$ sudo apt-get upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 aptitude:i386 : Depends: libapt-pkg4.12:i386 (>= 0.8.16~exp12ubuntu6) but it is not installed
                 Depends: libboost-iostreams1.46.1:i386 (>= 1.46.1-1) but it is not installable
                 Depends: libcwidget3:i386 but it is not installed
                 Depends: libept1.4.12:i386 but it is not installed
                 Depends: libsigc++-2.0-0c2a:i386 (>= 2.0.2) but it is not installed
                 Depends: libxapian22:i386 but it is not installed
                 Recommends: apt-xapian-index:i386 but it is not installable
                 Recommends: libparse-debianchangelog-perl:i386 but it is not installable
 bzip2 : Depends: libbz2-1.0 (= 1.0.6-4) but 1.0.6-5 is installed
 gdm : Depends: libgdm1 (= 3.10.0.1-0ubuntu3) but it is not installed
       Depends: gir1.2-gdm-1.0 (= 3.10.0.1-0ubuntu3) but it is not installed
 gnome-control-center : Depends: libgoa-1.0-0b (>= 3.5.90) but it is not installed
                        Depends: libgoa-backend-1.0-1 (>= 3.10.0) but it is not installed
                        Recommends: gnome-control-center-shared-data but it is not installed
 gnome-power-manager : Depends: gnome-settings-daemon-schemas (>= 3.2) but it is not installed
 gnome-session : Depends: gnome-session-bin (>= 3.9.90-0ubuntu12) but 3.9.90-0ubuntu3 is installed
                 Depends: gnome-session-common (= 3.9.90-0ubuntu12) but 3.9.90-0ubuntu3 is installed
 gnome-settings-daemon : Depends: libaccountsservice0 (>= 0.6.35-0ubuntu7) but 0.6.34-0ubuntu6 is installed
                         Depends: libgtk-3-0 (>= 3.9.10) but 3.8.6-0ubuntu3.1 is installed
                         Depends: gnome-settings-daemon-schemas (= 3.8.6.1-0ubuntu11.1) but it is not installed
 gnome-shell : Depends: gir1.2-mutter-3.0 (>= 3.10.0) but 3.8.4-0ubuntu2 is installed
               Depends: libcogl-pango15 (>= 1.15.8) but it is not installed
               Depends: libcogl15 (>= 1.15.8) but it is not installed
               Depends: libecal-1.2-16 (>= 3.5.91) but it is not installed
               Depends: libedataserver-1.2-18 (>= 3.5.91) but it is not installed
               Depends: libgjs0-libmozjs-24-0
               Depends: libgjs0e (>= 1.40.1) but it is not installed
               Depends: libmozjs-24-0 but it is not installed
               Depends: libmutter0c (>= 3.10) but it is not installed
               Depends: libmutter0c (< 3.11) but it is not installed
               Depends: gir1.2-gdm-1.0 but it is not installed
 gvfs : Depends: gvfs-libs (= 1.20.1-1ubuntu1) but 1.18.2-0ubuntu1 is installed
 gvfs:i386 : Depends: gvfs-libs:i386 (= 1.20.1-1ubuntu1) but 1.18.2-0ubuntu1 is installed
 gvfs-backends : Depends: libsmbclient (>= 2:4.0.3+dfsg1) but 2:3.6.18-1ubuntu3.1 is installed
                 Depends: gvfs-libs (= 1.20.1-1ubuntu1) but 1.18.2-0ubuntu1 is installed
 gvfs-daemons : Depends: gvfs-libs (= 1.20.1-1ubuntu1) but 1.18.2-0ubuntu1 is installed
 gvfs-fuse : Depends: gvfs (= 1.18.2-0ubuntu1) but 1.20.1-1ubuntu1 is installed
 gvfs-libs : Depends: gvfs-common (= 1.18.2-0ubuntu1) but 1.20.1-1ubuntu1 is installed
 gvfs-libs:i386 : Depends: gvfs-common:i386 (= 1.18.2-0ubuntu1)
 libace-perl : Depends: perlapi-5.14.2 but it is not installable
 libalgorithm-diff-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libapache2-mod-perl2 : Depends: perlapi-5.14.2 but it is not installable
 libapparmor-perl : Depends: perlapi-5.14.2 but it is not installable
 libapt-pkg-perl : Depends: perlapi-5.14.2 but it is not installable
 libauthen-pam-perl : Depends: perlapi-5.14.2 but it is not installable
 libbio-scf-perl : Depends: perlapi-5.14.2 but it is not installable
 libbit-vector-perl : Depends: perlapi-5.14.2 but it is not installable
 libbsd-resource-perl : Depends: perlapi-5.14.2 but it is not installable
 libbz2-dev : Depends: libbz2-1.0 (= 1.0.6-4) but 1.0.6-5 is installed
 libcairo-perl : Depends: perlapi-5.14.2 but it is not installable
 libclass-c3-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libclass-load-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libclone-perl : Depends: perlapi-5.14.2 but it is not installable
 libcommon-sense-perl : Depends: perl (>= 5.18.2) but 5.14.2-21build1 is installed
 libconvert-binary-c-perl : Depends: perlapi-5.14.2 but it is not installable
 libcrypt-ssleay-perl : Depends: perlapi-5.14.2 but it is not installable
 libdate-calc-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libdbd-mysql-perl : Depends: perlapi-5.14.2 but it is not installable
 libdbd-pg-perl : Depends: perlapi-5.14.2 but it is not installable
 libdbd-sqlite3-perl : Depends: perlapi-5.14.2 but it is not installable
 libdbi-perl : Depends: perlapi-5.14.2 but it is not installable
 libdrm-dev : Depends: libdrm2 (= 2.4.46-1ubuntu1) but 2.4.52-1 is installed
 libfcgi-perl : Depends: perlapi-5.14.2 but it is not installable
 libffi-dev : Depends: libffi6 (= 3.0.13-4) but 3.1~rc1+r3.0.13-12 is installed
 libfile-fcntllock-perl : Depends: perlapi-5.14.2 but it is not installable
 libgd-gd2-perl : Depends: perlapi-5.14.2 but it is not installable
 libglib-perl : Depends: perlapi-5.14.2 but it is not installable
 libgnutls-openssl27 : Depends: libgnutls26 (= 2.12.23-1ubuntu4) but 2.12.23-12ubuntu2.1 is installed
 libgtk2-perl : Depends: perlapi-5.14.2 but it is not installable
 libhtml-parser-perl : Depends: perlapi-5.14.2 but it is not installable
 libio-pty-perl : Depends: perlapi-5.14.2 but it is not installable
 libipc-sharelite-perl : Depends: perlapi-5.14.2 but it is not installable
 libjson-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 liblist-moreutils-perl : Depends: perlapi-5.14.2 but it is not installable
 liblocale-gettext-perl : PreDepends: perlapi-5.14.2 but it is not installable
 libmoose-perl : Depends: perlapi-5.14.2 but it is not installable
 libnet-dbus-perl : Depends: perlapi-5.14.2 but it is not installable
 libnet-dns-perl : Depends: perlapi-5.14.2 but it is not installable
 libnet-ssleay-perl : Depends: perlapi-5.14.2 but it is not installable
 libossp-uuid-perl : Depends: perlapi-5.14.2 but it is not installable
 libpackage-stash-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libpango-perl : Depends: perlapi-5.14.2 but it is not installable
 libparams-classify-perl : Depends: perlapi-5.14.2 but it is not installable
 libparams-util-perl : Depends: perlapi-5.14.2 but it is not installable
 libperl5.14 : Depends: perl-base (= 5.14.2-21build1) but 5.18.2-2ubuntu1 is installed
 libperlio-gzip-perl : Depends: perlapi-5.14.2 but it is not installable
 libpurple0 : Depends: perlapi-5.14.2 but it is not installable
 libsocket6-perl : Depends: perlapi-5.14.2 but it is not installable
 libstring-approx-perl : Depends: perlapi-5.14.2 but it is not installable
 libsub-identify-perl : Depends: perlapi-5.14.2 but it is not installable
 libsub-name-perl : Depends: perlapi-5.14.2 but it is not installable
 libterm-readkey-perl : Depends: perlapi-5.14.2 but it is not installable
 libtext-charwidth-perl : Depends: perlapi-5.14.2 but it is not installable
 libtext-iconv-perl : Depends: perlapi-5.14.2 but it is not installable
 libunicode-map-perl : Depends: perlapi-5.14.2 but it is not installable
 libuuid-perl : Depends: perlapi-5.14.2 but it is not installable
 libvariable-magic-perl : Depends: perlapi-5.14.2 but it is not installable
 libx11-dev : Depends: libx11-6 (= 2:1.6.1-1ubuntu1) but 2:1.6.2-1ubuntu2 is installed
 libxcb1-dev : Depends: libxcb1 (= 1.9.1-3ubuntu1) but 1.10-2ubuntu1 is installed
 libxml-libxml-perl : Depends: perlapi-5.14.2 but it is not installable
 libxml-libxslt-perl : Depends: perlapi-5.14.2 but it is not installable
 libxml-parser-perl : Depends: perlapi-5.14.2 but it is not installable
 libyaml-syck-perl : Depends: perlapi-5.14.2 but it is not installable
 nautilus : Depends: libgtk-3-0 (>= 3.9.12) but 3.8.6-0ubuntu3.1 is installed
            Depends: nautilus-data (>= 1:3.10) but 1:3.8.2-0ubuntu2.2 is installed
 nautilus-sendto : Depends: libedataserver-1.2-18 (>= 3.5.91) but it is not installed
 nautilus-sendto-empathy : Depends: empathy (= 3.8.6-0ubuntu9.1) but 3.8.4-1ubuntu2 is installed
                           Depends: empathy-common (= 3.8.6-0ubuntu9.1) but 3.8.4-1ubuntu2 is installed
 network-manager : Depends: libmm-glib0 (>= 0.7.991) but it is not installed
 network-manager-gnome : Depends: libmm-glib0 (>= 0.7.991) but it is not installed
                         Depends: libnm-gtk0 (= 0.9.8.8-0ubuntu4.1) but 0.9.8.0-1ubuntu5.1 is installed
 perl : Depends: perl-base (= 5.14.2-21build1) but 5.18.2-2ubuntu1 is installed
 perl-tk : Depends: perlapi-5.14.2 but it is not installable
 ppa-purge : Depends: aptitude but it is not installed
 rhythmbox : Depends: librhythmbox-core8 (= 3.0.2-0ubuntu2) but it is not installed
             Depends: libtotem-plparser18 (>= 3.10.0) but it is not installed
             Depends: python3 (>= 3.4~) but 3.3.2-14ubuntu1 is installed
             Depends: python3.4 but it is not installed
             Depends: gir1.2-rb-3.0 (= 3.0.2-0ubuntu2) but 2.99.1-0ubuntu1 is installed
 rhythmbox-plugin-cdrecorder : Depends: librhythmbox-core8 (>= 3.0) but it is not installed
 rhythmbox-plugin-magnatune : Depends: gir1.2-secret-1 but it is not installed
 rhythmbox-plugins : Depends: librhythmbox-core8 (= 3.0.2-0ubuntu2) but it is not installed
                     Depends: libtotem-plparser18 (>= 3.10.0) but it is not installed
                     Depends: python3 (>= 3.4~) but 3.3.2-14ubuntu1 is installed
                     Depends: python3.4 but it is not installed
                     Depends: gir1.2-rb-3.0 (= 3.0.2-0ubuntu2) but 2.99.1-0ubuntu1 is installed
                     Depends: python3-mako but it is not installed
 tzdata-java : Depends: tzdata (= 2013g-0ubuntu1) but 2014e-0ubuntu0.14.04 is installed
E: Unmet dependencies. Try using -f.
```


```
lab@CURIE:~$ sudo apt-get dist-upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 aptitude:i386 : Depends: libapt-pkg4.12:i386 (>= 0.8.16~exp12ubuntu6) but it is not installed
                 Depends: libboost-iostreams1.46.1:i386 (>= 1.46.1-1) but it is not installable
                 Depends: libcwidget3:i386 but it is not installed
                 Depends: libept1.4.12:i386 but it is not installed
                 Depends: libsigc++-2.0-0c2a:i386 (>= 2.0.2) but it is not installed
                 Depends: libxapian22:i386 but it is not installed
                 Recommends: apt-xapian-index:i386 but it is not installable
                 Recommends: libparse-debianchangelog-perl:i386 but it is not installable
 bzip2 : Depends: libbz2-1.0 (= 1.0.6-4) but 1.0.6-5 is installed
 gdm : Depends: libgdm1 (= 3.10.0.1-0ubuntu3) but it is not installed
       Depends: gir1.2-gdm-1.0 (= 3.10.0.1-0ubuntu3) but it is not installed
 gnome-control-center : Depends: libgoa-1.0-0b (>= 3.5.90) but it is not installed
                        Depends: libgoa-backend-1.0-1 (>= 3.10.0) but it is not installed
                        Recommends: gnome-control-center-shared-data but it is not installed
 gnome-power-manager : Depends: gnome-settings-daemon-schemas (>= 3.2) but it is not installed
 gnome-session : Depends: gnome-session-bin (>= 3.9.90-0ubuntu12) but 3.9.90-0ubuntu3 is installed
                 Depends: gnome-session-common (= 3.9.90-0ubuntu12) but 3.9.90-0ubuntu3 is installed
 gnome-settings-daemon : Depends: libaccountsservice0 (>= 0.6.35-0ubuntu7) but 0.6.34-0ubuntu6 is installed
                         Depends: libgtk-3-0 (>= 3.9.10) but 3.8.6-0ubuntu3.1 is installed
                         Depends: gnome-settings-daemon-schemas (= 3.8.6.1-0ubuntu11.1) but it is not installed
 gnome-shell : Depends: gir1.2-mutter-3.0 (>= 3.10.0) but 3.8.4-0ubuntu2 is installed
               Depends: libcogl-pango15 (>= 1.15.8) but it is not installed
               Depends: libcogl15 (>= 1.15.8) but it is not installed
               Depends: libecal-1.2-16 (>= 3.5.91) but it is not installed
               Depends: libedataserver-1.2-18 (>= 3.5.91) but it is not installed
               Depends: libgjs0-libmozjs-24-0
               Depends: libgjs0e (>= 1.40.1) but it is not installed
               Depends: libmozjs-24-0 but it is not installed
               Depends: libmutter0c (>= 3.10) but it is not installed
               Depends: libmutter0c (< 3.11) but it is not installed
               Depends: gir1.2-gdm-1.0 but it is not installed
 gvfs : Depends: gvfs-libs (= 1.20.1-1ubuntu1) but 1.18.2-0ubuntu1 is installed
 gvfs:i386 : Depends: gvfs-libs:i386 (= 1.20.1-1ubuntu1) but 1.18.2-0ubuntu1 is installed
 gvfs-backends : Depends: libsmbclient (>= 2:4.0.3+dfsg1) but 2:3.6.18-1ubuntu3.1 is installed
                 Depends: gvfs-libs (= 1.20.1-1ubuntu1) but 1.18.2-0ubuntu1 is installed
 gvfs-daemons : Depends: gvfs-libs (= 1.20.1-1ubuntu1) but 1.18.2-0ubuntu1 is installed
 gvfs-fuse : Depends: gvfs (= 1.18.2-0ubuntu1) but 1.20.1-1ubuntu1 is installed
 gvfs-libs : Depends: gvfs-common (= 1.18.2-0ubuntu1) but 1.20.1-1ubuntu1 is installed
 gvfs-libs:i386 : Depends: gvfs-common:i386 (= 1.18.2-0ubuntu1)
 libace-perl : Depends: perlapi-5.14.2 but it is not installable
 libalgorithm-diff-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libapache2-mod-perl2 : Depends: perlapi-5.14.2 but it is not installable
 libapparmor-perl : Depends: perlapi-5.14.2 but it is not installable
 libapt-pkg-perl : Depends: perlapi-5.14.2 but it is not installable
 libauthen-pam-perl : Depends: perlapi-5.14.2 but it is not installable
 libbio-scf-perl : Depends: perlapi-5.14.2 but it is not installable
 libbit-vector-perl : Depends: perlapi-5.14.2 but it is not installable
 libbsd-resource-perl : Depends: perlapi-5.14.2 but it is not installable
 libbz2-dev : Depends: libbz2-1.0 (= 1.0.6-4) but 1.0.6-5 is installed
 libcairo-perl : Depends: perlapi-5.14.2 but it is not installable
 libclass-c3-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libclass-load-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libclone-perl : Depends: perlapi-5.14.2 but it is not installable
 libcommon-sense-perl : Depends: perl (>= 5.18.2) but 5.14.2-21build1 is installed
 libconvert-binary-c-perl : Depends: perlapi-5.14.2 but it is not installable
 libcrypt-ssleay-perl : Depends: perlapi-5.14.2 but it is not installable
 libdate-calc-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libdbd-mysql-perl : Depends: perlapi-5.14.2 but it is not installable
 libdbd-pg-perl : Depends: perlapi-5.14.2 but it is not installable
 libdbd-sqlite3-perl : Depends: perlapi-5.14.2 but it is not installable
 libdbi-perl : Depends: perlapi-5.14.2 but it is not installable
 libdrm-dev : Depends: libdrm2 (= 2.4.46-1ubuntu1) but 2.4.52-1 is installed
 libfcgi-perl : Depends: perlapi-5.14.2 but it is not installable
 libffi-dev : Depends: libffi6 (= 3.0.13-4) but 3.1~rc1+r3.0.13-12 is installed
 libfile-fcntllock-perl : Depends: perlapi-5.14.2 but it is not installable
 libgd-gd2-perl : Depends: perlapi-5.14.2 but it is not installable
 libglib-perl : Depends: perlapi-5.14.2 but it is not installable
 libgnutls-openssl27 : Depends: libgnutls26 (= 2.12.23-1ubuntu4) but 2.12.23-12ubuntu2.1 is installed
 libgtk2-perl : Depends: perlapi-5.14.2 but it is not installable
 libhtml-parser-perl : Depends: perlapi-5.14.2 but it is not installable
 libio-pty-perl : Depends: perlapi-5.14.2 but it is not installable
 libipc-sharelite-perl : Depends: perlapi-5.14.2 but it is not installable
 libjson-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 liblist-moreutils-perl : Depends: perlapi-5.14.2 but it is not installable
 liblocale-gettext-perl : PreDepends: perlapi-5.14.2 but it is not installable
 libmoose-perl : Depends: perlapi-5.14.2 but it is not installable
 libnet-dbus-perl : Depends: perlapi-5.14.2 but it is not installable
 libnet-dns-perl : Depends: perlapi-5.14.2 but it is not installable
 libnet-ssleay-perl : Depends: perlapi-5.14.2 but it is not installable
 libossp-uuid-perl : Depends: perlapi-5.14.2 but it is not installable
 libpackage-stash-xs-perl : Depends: perlapi-5.14.2 but it is not installable
 libpango-perl : Depends: perlapi-5.14.2 but it is not installable
 libparams-classify-perl : Depends: perlapi-5.14.2 but it is not installable
 libparams-util-perl : Depends: perlapi-5.14.2 but it is not installable
 libperl5.14 : Depends: perl-base (= 5.14.2-21build1) but 5.18.2-2ubuntu1 is installed
 libperlio-gzip-perl : Depends: perlapi-5.14.2 but it is not installable
 libpurple0 : Depends: perlapi-5.14.2 but it is not installable
 libsocket6-perl : Depends: perlapi-5.14.2 but it is not installable
 libstring-approx-perl : Depends: perlapi-5.14.2 but it is not installable
 libsub-identify-perl : Depends: perlapi-5.14.2 but it is not installable
 libsub-name-perl : Depends: perlapi-5.14.2 but it is not installable
 libterm-readkey-perl : Depends: perlapi-5.14.2 but it is not installable
 libtext-charwidth-perl : Depends: perlapi-5.14.2 but it is not installable
 libtext-iconv-perl : Depends: perlapi-5.14.2 but it is not installable
 libunicode-map-perl : Depends: perlapi-5.14.2 but it is not installable
 libuuid-perl : Depends: perlapi-5.14.2 but it is not installable
 libvariable-magic-perl : Depends: perlapi-5.14.2 but it is not installable
 libx11-dev : Depends: libx11-6 (= 2:1.6.1-1ubuntu1) but 2:1.6.2-1ubuntu2 is installed
 libxcb1-dev : Depends: libxcb1 (= 1.9.1-3ubuntu1) but 1.10-2ubuntu1 is installed
 libxml-libxml-perl : Depends: perlapi-5.14.2 but it is not installable
 libxml-libxslt-perl : Depends: perlapi-5.14.2 but it is not installable
 libxml-parser-perl : Depends: perlapi-5.14.2 but it is not installable
 libyaml-syck-perl : Depends: perlapi-5.14.2 but it is not installable
 nautilus : Depends: libgtk-3-0 (>= 3.9.12) but 3.8.6-0ubuntu3.1 is installed
            Depends: nautilus-data (>= 1:3.10) but 1:3.8.2-0ubuntu2.2 is installed
 nautilus-sendto : Depends: libedataserver-1.2-18 (>= 3.5.91) but it is not installed
 nautilus-sendto-empathy : Depends: empathy (= 3.8.6-0ubuntu9.1) but 3.8.4-1ubuntu2 is installed
                           Depends: empathy-common (= 3.8.6-0ubuntu9.1) but 3.8.4-1ubuntu2 is installed
 network-manager : Depends: libmm-glib0 (>= 0.7.991) but it is not installed
 network-manager-gnome : Depends: libmm-glib0 (>= 0.7.991) but it is not installed
                         Depends: libnm-gtk0 (= 0.9.8.8-0ubuntu4.1) but 0.9.8.0-1ubuntu5.1 is installed
 perl : Depends: perl-base (= 5.14.2-21build1) but 5.18.2-2ubuntu1 is installed
 perl-tk : Depends: perlapi-5.14.2 but it is not installable
 ppa-purge : Depends: aptitude but it is not installed
 rhythmbox : Depends: librhythmbox-core8 (= 3.0.2-0ubuntu2) but it is not installed
             Depends: libtotem-plparser18 (>= 3.10.0) but it is not installed
             Depends: python3 (>= 3.4~) but 3.3.2-14ubuntu1 is installed
             Depends: python3.4 but it is not installed
             Depends: gir1.2-rb-3.0 (= 3.0.2-0ubuntu2) but 2.99.1-0ubuntu1 is installed
 rhythmbox-plugin-cdrecorder : Depends: librhythmbox-core8 (>= 3.0) but it is not installed
 rhythmbox-plugin-magnatune : Depends: gir1.2-secret-1 but it is not installed
 rhythmbox-plugins : Depends: librhythmbox-core8 (= 3.0.2-0ubuntu2) but it is not installed
                     Depends: libtotem-plparser18 (>= 3.10.0) but it is not installed
                     Depends: python3 (>= 3.4~) but 3.3.2-14ubuntu1 is installed
                     Depends: python3.4 but it is not installed
                     Depends: gir1.2-rb-3.0 (= 3.0.2-0ubuntu2) but 2.99.1-0ubuntu1 is installed
                     Depends: python3-mako but it is not installed
 tzdata-java : Depends: tzdata (= 2013g-0ubuntu1) but 2014e-0ubuntu0.14.04 is installed
E: Unmet dependencies. Try using -f.
```

---

### Post by deadflowr on 2014-07-07
Well, first off we would prefer it if you used code tags, instead of quote tags. Quote tags tend to stretch pages out some.
[URL="http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168"]http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168
[/URL]Now then problem at hand
> Can't locate Storable.pm in @INC (you may need to install the Storable module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/bin/apt-show-versions line 37. BEGIN failed--compilation aborted at /usr/bin/apt-show-versions line 37. 
W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59 
W: GPG error: [http://download.webmin.com](http://download.webmin.com) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D97A3AE911F63C51 
E: Problem executing scripts APT::Update::Post-Invoke-Success 'test -x /usr/bin/apt-show-versions || exit 0 ; apt-show-versions -i' E: Sub-process returned an error code
For the first part, i've never seen it,(The storable.pm part) so can't help.
But spotify has had a repo problem as of late.
I would suggest opening the program "Software and Updates, and disabling the spotify entries, as well as the webmin entries, for now.
And try apt-get update again.
Then we'll look into the first part if it's still a problem.

---

### Post by Blake_Stamps on 2014-07-07
Apologies- first time here. Disabled the Spotify and Webin repos- still no luck. The error still seems to be 

```
Can't locate Storable.pm in @INC (you may need to install the Storable module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/bin/apt-show-versions line 37.
BEGIN failed--compilation aborted at /usr/bin/apt-show-versions line 37.
E: Problem executing scripts APT::Update::Post-Invoke-Success 'test -x /usr/bin/apt-show-versions || exit 0 ; apt-show-versions -i'
E: Sub-process returned an error code
```

Let's try this with the code tags...

```
lab@CURIE:/media/lab/Glacier/$ sudo apt-get updateIgn http://us.archive.ubuntu.com trusty InRelease
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Ign http://archive.canonical.com quantal InRelease                             
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]          
Get:2 http://us.archive.ubuntu.com trusty-backports Release.gpg [933 B]        
Hit http://archive.canonical.com quantal Release.gpg                           
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty Release                                
Get:3 http://us.archive.ubuntu.com trusty-updates Release [58.5 kB]            
Hit http://archive.canonical.com quantal Release                               
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://archive.canonical.com quantal/partner Sources                       
Hit http://extras.ubuntu.com trusty/main Sources                               
Get:4 http://us.archive.ubuntu.com trusty-backports Release [58.6 kB]          
Hit http://archive.canonical.com quantal/partner amd64 Packages                
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://archive.canonical.com quantal/partner i386 Packages                 
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Ign http://security.ubuntu.com trusty-security InRelease                       
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages       
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages     
Hit http://security.ubuntu.com trusty-security Release.gpg            
Hit http://security.ubuntu.com trusty-security Release                
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://us.archive.ubuntu.com trusty/main i386 Packages            
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages      
Hit http://security.ubuntu.com trusty-security/restricted Sources     
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Get:5 http://us.archive.ubuntu.com trusty-updates/main Sources [81.5 kB]       
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Ign http://archive.canonical.com quantal/partner Translation-en_US             
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://archive.canonical.com quantal/partner Translation-en                
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Get:6 http://us.archive.ubuntu.com trusty-updates/restricted Sources [14 B]
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Get:7 http://us.archive.ubuntu.com trusty-updates/universe Sources [60.1 kB]
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Get:8 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [2,681 B]
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Get:9 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [216 kB]
Get:10 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [14 B]
Get:11 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [153 kB]
Ign http://security.ubuntu.com trusty-security/main Translation-en_US
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US
Ign http://security.ubuntu.com trusty-security/universe Translation-en_US
Get:12 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [7,397 B]
Get:13 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [212 kB]
Get:14 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [14 B]
Get:15 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [154 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [7,569 B]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Get:17 http://us.archive.ubuntu.com trusty-backports/main Sources [14 B]
Get:18 http://us.archive.ubuntu.com trusty-backports/restricted Sources [14 B]
Get:19 http://us.archive.ubuntu.com trusty-backports/universe Sources [7,901 B]
Get:20 http://us.archive.ubuntu.com trusty-backports/multiverse Sources [768 B]
Get:21 http://us.archive.ubuntu.com trusty-backports/main amd64 Packages [14 B]
Get:22 http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages [14 B]
Get:23 http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages [9,613 B]
Get:24 http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [619 B]
Get:25 http://us.archive.ubuntu.com trusty-backports/main i386 Packages [14 B]
Get:26 http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages [14 B]
Get:27 http://us.archive.ubuntu.com trusty-backports/universe i386 Packages [9,633 B]
Get:28 http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages [619 B]
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com trusty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com trusty-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com trusty-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com trusty-backports/main Translation-en_US       
Ign http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com trusty-backports/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com trusty-backports/universe Translation-en_US   
Fetched 1,043 kB in 7s (132 kB/s)                                              
Can't locate Storable.pm in @INC (you may need to install the Storable module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/bin/apt-show-versions line 37.
BEGIN failed--compilation aborted at /usr/bin/apt-show-versions line 37.
E: Problem executing scripts APT::Update::Post-Invoke-Success 'test -x /usr/bin/apt-show-versions || exit 0 ; apt-show-versions -i'
E: Sub-process returned an error code
```

---

