---
title: "How i can fix “ E: Internal Error, No file name for libc6 ”"
date: 2013-11-01
forum: Installation &amp; Upgrades
---

### Post by smaouh on 2013-11-01
[COLOR=#333333][FONT=UbuntuRegular]Hello all please i need your help to fix this problem i have 2 broken packages system and i can't reinstall them or make any other option : update , upgrade , install & remove app .... Ubuntu 12.04.3 I have not found any solutions please help me

[/FONT][/COLOR][IMG]http://i.stack.imgur.com/uWHW5.png[/IMG]
[IMG]http://i.stack.imgur.com/PoN7V.png[/IMG]

> [FONT=Ubuntu Mono]sudo apt-get install -f[/FONT]
smaouh@Linux:~$ sudo apt-get install -f
[sudo] password for smaouh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 libpam-winbind libao-common gnome-exe-thumbnailer
  libqca2-plugin-ossl gir1.2-champlain-0.12 libmagickcore4 libmagickwand4
  libmagickcore4-extra libcapi20-3 python-unidecode libopenal-data liblqr-1-0
  gir1.2-gtkchamplain-0.12 unixodbc wine-gecko2.21 libchamplain-0.12-0
  python-glade2 imagemagick-common libosmesa6 oss-compat gimp-help-common
  esound-common gimp-help-en libmpg123-0 ttf-mscorefonts-installer imagemagick
  winbind libodbc1 fonts-droid fonts-unfonts-core libchamplain-gtk-0.12-0
  libclutter-gtk-1.0-0 gir1.2-gtkclutter-1.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 386 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: error processing libc6 (--configure):
 libc6:amd64 2.15-0ubuntu10.5 cannot be configured because libc6:i386 is in a different version (2.15-0ubuntu10.4)
dpkg: dependency problems prevent configuration of libc-dev-bin:
 libc-dev-bin depends on libc6 (>> 2.15); however:
  Package libc6 is not configured yet.
 libc-dev-bin depends on libc6 (<< 2.16); however:
  Package libc6 is not configured yet.
dpkg: error processing libc-dev-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.15-0ubuntu10.5); however:
  Package libc6 is not configured yet.
 libc6-dev depends on libc-dev-bin (= 2.15-0ubuntu10.5); however:
  Package libc-dev-bin is not configured yet.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-i386:
 libc6-i386 depends on libc6 (= 2.15-0ubuntu10.5); however:
  Package libc6 is not configured yet.
dpkg: error processing libc6-i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    No apport report written because MaxReports is reached already
                                  Errors were encountered while processing:
 libc6
 libc-dev-bin
 libc6-dev
 libc6-i386
E: Sub-process /usr/bin/dpkg returned an error code (1) [FONT=Ubuntu Mono]smaouh@Linux:~$ [/FONT]

---

### Post by kyutums on 2013-11-02
These commands worked for me:
> dpkg -i /var/cache/apt/archives/*.deb
dpkg --configure -a

---

