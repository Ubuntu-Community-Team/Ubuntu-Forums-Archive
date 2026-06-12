---
title: "DPKG Error during upgrade and install new tool"
date: 2023-12-28
forum: Installation &amp; Upgrades
---

### Post by falcon4949 on 2023-12-28
Dear Team,

I am using the ubuntu 22.04. During the upgradation or installed a new tools I am getting below error

dpkg: error processing package libreoffice-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop-minimal:
 ubuntu-desktop-minimal depends on gdm3; however:
  Package gdm3 is not configured yet.

dpkg: error processing package ubuntu-desktop-minimal (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of libreoffice-base-drivers:
 libreoffice-base-drivers depends on libreoffice-core-nogui | libreoffice-core; however:
  Package libreoffice-core-nogui is not installed.
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-base-drivers (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-wiki-publisher:
 libreoffice-wiki-publisher depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.
 libreoffice-wiki-publisher depends on libreoffice-java-common; however:
  Package libreoffice-java-common is not configured yet.

dpkg: error processing package libreoffice-wiki-publisher (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-script-provider-python:
 libreoffice-script-provider-python depends on libreoffice-common; however:
  Package libreoffNo apport report written because MaxReports is reached already
                                                                                No apport report written because MaxReports is reached already
                                                                                                                                              No apport report written because MaxReports is reached already
                                                                                                                                                                                                           ice-common is not configured yet.
 libreoffice-script-provider-python depends on libreoffice-core-nogui | libreoffice-core; however:
  Package libreoffice-core-nogui is not installed.
  Package libreoffice-core is not configured yet.
 libreoffice-script-provider-python depends on python3-uno (>= 4.4.0~beta2); however:
  Package python3-uno is not configured yet.

dpkg: error processing package libreoffice-script-provider-python (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-nlpsolver:
 libreoffice-nlpsolver depends on libreoffice-calc; however:
  Package libreoffice-calc is not configured yet.
 libreoffice-nlpsolver depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.
 libreoffice-nlpsolver depends on libreoffice-java-common; however:
  Package libreoffice-java-common is not configured yet.

dpkg: error processing package libreoffice-nlpsolver (--configure):
 dependency problems - leNo apport report written because MaxReports is reached already
                                                                                       No apport report written because MaxReports is reached already
                                                                                                                                                     aving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-report-builder-bin:
 libreoffice-report-builder-bin depends on libreoffice-base; however:
  Package libreoffice-base is not configured yet.
 libreoffice-report-builder-bin depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-report-builder-bin (--configure):
 dependency problems - leaving unconfigured
Setting up libswresample3:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting up libldns-dev:amd64 (1.7.1-2ubuntu4+esm1) ...
Setting up libpython2.7-stdlib:amd64 (2.7.18-13ubuntu1.1+esm2) ...
dpkg: dependency problems prevent configuration of libreoffice-sdbc-firebird:
 libreoffice-sdbc-firebird depends on libreoffice-core-nogui | libreoffice-core; however:
  Package libreoffice-core-nogui is not installed.
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-sdbc-firebird (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-sdbc-mysql:
 libreoffice-sdbc-mysql depends on libreoffice-core-nogui | libreoffice-core; however:
  Package libreoffice-core-nogui is not installed.
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-sdbc-mysql (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Setting up imagemagick-6.q16 (8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3+esm2) ...
dpkg: dependency problems prevent configuration of libreoffice-base-core:
 libreoffice-base-core depends on libreoffice-core (= 1:7.3.7-0ubuntu0.22.04.4) | libreoffice-core-nogui (= 1:7.3.7-0ubuntu0.22.04.4); however:
  Package libreoffice-core is not configured yet.
  Package libreoffice-core-nogui is not installed.

dpkg: error processing package libreoffice-base-core (--configure):
 dependency problems - leaving unconfigured
Setting up libimage-magick-perl (8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3+esm2) ...
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of forticlient:
 forticlient depends on libgconf-2-4 (>> 0); however:
  Package libgconf-2-4:amd64 is not configured yet.

dpkg: error processing package forticlient (--configure):
 dependency problems - leaving unconfigured
Setting up libpython2.7:amd64 (2.7.18-13ubuntu1.1+esm2) ...
No apport report written because MaxReports is reached already
                                                              Setting up libpython2.7-dev:amd64 (2.7.18-13ubuntu1.1+esm2) ...
Setting up python2.7 (2.7.18-13ubuntu1.1+esm2) ...
Setting up libavcodec-extra58:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting up libavformat58:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting up imagemagick (8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3+esm2) ...
Setting up libavfilter7:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting up python2.7-dev (2.7.18-13ubuntu1.1+esm2) ...
Setting up libavcodec-extra:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting up libavdevice58:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting up ffmpeg (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for libc-bin (2.35-0ubuntu3.5) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Errors were encountered while processing:
 ufw
 samba-common
 gconf2-common
 libreoffice-common
 gconf-service-backend
 grub-efi-amd64
 libreoffice-gnome
 smbclient
 libreoffice-impress
 samba-common-bin
 gconf-service
 gdm3
 python3-uno
 libreoffice-script-provider-bsh
 libreoffice-core
 libreoffice-script-provider-js
 libreoffice
 samba
 libreoffice-calc
 libreoffice-base
 libreoffice-math
 ubuntu-desktop
 libreoffice-gtk3
 libreoffice-sdbc-postgresql
 libreoffice-sdbc-hsqldb
 libreoffice-writer
 grub-efi-amd64-signed
 libreoffice-report-builder
 libgconf-2-4:amd64
 libreoffice-draw
 libreoffice-java-common
 ubuntu-desktop-minimal
 libreoffice-base-drivers
 libreoffice-wiki-publisher
 libreoffice-script-provider-python
 libreoffice-nlpsolver
 libreoffice-report-builder-bin
 libreoffice-sdbc-firebird
 libreoffice-sdbc-mysql
 libreoffice-base-core
 forticlient
E: Sub-process /usr/bin/dpkg returned an error code (1)

How to resolve the issues I updated my system but no resolution.

Kindly help me on this.

---

### Post by ActionParsnip on 2023-12-28
What is the output of:
```

[COLOR=#E8E6E3]apt cache policy libreoffice-java-common[/COLOR][COLOR=#E8E6E3] ubuntu-desktop-minimal[/COLOR][COLOR=#E8E6E3] gdm3

```[/COLOR]

---

### Post by Bashing-om on 2023-12-28
> **ActionParsnip said:**
> What is the output of:
```

[COLOR=#E8E6E3]apt cache policy libreoffice-java-common[/COLOR][COLOR=#E8E6E3] ubuntu-desktop-minimal[/COLOR][COLOR=#E8E6E3] gdm3

```[/COLOR]

Like so ?
```

sudo dpkg -i --configure -a

```

[INDENT]maybe Yes
[INDENT]could be; we got to go deeper
 [/INDENT][/INDENT]

---

