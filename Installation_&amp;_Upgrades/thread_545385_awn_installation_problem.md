---
title: "awn installation problem"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by Djonah Inc. on 2007-09-07
well..lets say that it just didn't work.. here's my terminal.
BTW: I'm an ubuntu newbie..really newbie

[LIST]
[*]djonah@djonah-laptop:~/avant-window-navigator-0.1.1$ sudo apt-get install build-essential 
[*]Password:
[*]Pakketlijsten worden ingelezen... Klaar
[*]Boom van vereisten wordt opgebouwd       
[*]Reading state information... Klaar
[*]De volgende extra pakketten zullen geïnstalleerd worden:
[*]  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
[*]Voorgestelde pakketten:
[*]  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev
[*]  libstdc++6-4.1-doc
[*]De volgende NIEUWE pakketten zullen geïnstalleerd worden:
[*]  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
[*]  linux-libc-dev
[*]0 pakketten opgewaardeerd, 7 nieuwe pakketten geïnstalleerd, 0 verwijderen en 0 niet opgewaardeerd.
[*]Er moeten 8054kB aan archieven opgehaald worden.
[*]Na het uitpakken zal er 33,7MB extra schijfruimte gebruikt worden.
[*]Wilt u doorgaan [J/n]? j
[*]Ophalen:1 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libc6-dev 2.5-0ubuntu14 [3018kB]
[*]Ophalen:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main linux-libc-dev 2.6.20-16.31 [668kB]
[*]Ophalen:3 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libstdc++6-4.1-dev 4.1.2-0ubuntu4 [1632kB]
[*]Ophalen:4 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main g++-4.1 4.1.2-0ubuntu4 [2581kB]
[*]Ophalen:5 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main g++ 4:4.1.2-1ubuntu1 [1428B]
[*]Ophalen:6 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main dpkg-dev 1.13.24ubuntu6 [147kB]
[*]Ophalen:7 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main build-essential 11.3 [6974B]
[*]8054kB opgehaald in 7s (1117kB/s)                                              
[*]Selecteren van voorheen niet geselecteerd pakket linux-libc-dev.
[*](Database inlezen ... 116890 bestanden en mappen geïnstalleerd.)
[*]Uitpakken van linux-libc-dev (uit .../linux-libc-dev_2.6.20-16.31_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libc6-dev.
[*]Uitpakken van libc6-dev (uit .../libc6-dev_2.5-0ubuntu14_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libstdc++6-4.1-dev.
[*]Uitpakken van libstdc++6-4.1-dev (uit .../libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket g++-4.1.
[*]Uitpakken van g++-4.1 (uit .../g++-4.1_4.1.2-0ubuntu4_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket g++.
[*]Uitpakken van g++ (uit .../g++_4%3a4.1.2-1ubuntu1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket dpkg-dev.
[*]Uitpakken van dpkg-dev (uit .../dpkg-dev_1.13.24ubuntu6_all.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket build-essential.
[*]Uitpakken van build-essential (uit .../build-essential_11.3_i386.deb) ...
[*]Instellen van linux-libc-dev (2.6.20-16.31) ...
[*]Instellen van libc6-dev (2.5-0ubuntu14) ...
[*]Instellen van dpkg-dev (1.13.24ubuntu6) ...
[*]Instellen van libstdc++6-4.1-dev (4.1.2-0ubuntu4) ...
[*]Instellen van g++-4.1 (4.1.2-0ubuntu4) ...
[*]Instellen van g++ (4.1.2-1ubuntu1) ...

[*]Instellen van build-essential (11.3) ...
[*]djonah@djonah-laptop:~/avant-window-navigator-0.1.1$ sudo apt-get install libgtk2.0-dev libwnck-dev libwnck-common libgconf2-dev libglib2.0-dev libgnome2-dev libgnome-desktop-2 libgnome-desktop-dev
[*]Pakketlijsten worden ingelezen... Klaar
[*]Boom van vereisten wordt opgebouwd       
[*]Reading state information... Klaar
[*]libwnck-common is reeds de nieuwste versie.
[*]libgnome-desktop-2 is reeds de nieuwste versie.
[*]De volgende extra pakketten zullen geïnstalleerd worden:
[*]  libart-2.0-dev libatk1.0-dev libaudiofile-dev libavahi-client-dev
[*]  libavahi-common-dev libavahi-glib-dev libbonobo2-dev libbonoboui2-dev
[*]  libcairo2-dev libdbus-1-dev libesd0-dev libexpat1-dev libfontconfig1-dev
[*]  libfreetype6-dev libgcrypt11-dev libglade2-dev libgnome-keyring-dev
[*]  libgnomecanvas2-dev libgnomeui-dev libgnomevfs2-dev libgnutls-dev
[*]  libgpg-error-dev libice-dev libidl-dev libjpeg62-dev liblzo-dev
[*]  libopencdk8-dev liborbit2-dev libpango1.0-dev libpng12-dev libpopt-dev
[*]  libselinux1-dev libsepol1-dev libsm-dev libstartup-notification0-dev
[*]  libtasn1-3-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev
[*]  libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml2-dev libxrandr-dev
[*]  libxrender-dev libxres-dev x11proto-core-dev x11proto-fixes-dev
[*]  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev
[*]  x11proto-resource-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev
[*]  zlib1g-dev
[*]Voorgestelde pakketten:
[*]  libcairo2-doc libgcrypt11-doc glade-2 glade-gnome-2 libglib2.0-doc
[*]  libgnome2-doc libgnomecanvas2-doc libgnomeui-doc gnutls-doc gnutls-bin
[*]  libgtk2.0-doc libpango1.0-doc
[*]Aanbevolen pakketten:
[*]  orbit2
[*]De volgende NIEUWE pakketten zullen geïnstalleerd worden:
[*]  libart-2.0-dev libatk1.0-dev libaudiofile-dev libavahi-client-dev
[*]  libavahi-common-dev libavahi-glib-dev libbonobo2-dev libbonoboui2-dev
[*]  libcairo2-dev libdbus-1-dev libesd0-dev libexpat1-dev libfontconfig1-dev
[*]  libfreetype6-dev libgconf2-dev libgcrypt11-dev libglade2-dev libglib2.0-dev
[*]  libgnome-desktop-dev libgnome-keyring-dev libgnome2-dev libgnomecanvas2-dev
[*]  libgnomeui-dev libgnomevfs2-dev libgnutls-dev libgpg-error-dev libgtk2.0-dev
[*]  libice-dev libidl-dev libjpeg62-dev liblzo-dev libopencdk8-dev liborbit2-dev
[*]  libpango1.0-dev libpng12-dev libpopt-dev libselinux1-dev libsepol1-dev
[*]  libsm-dev libstartup-notification0-dev libtasn1-3-dev libwnck-dev libx11-dev
[*]  libxau-dev libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev
[*]  libxi-dev libxinerama-dev libxml2-dev libxrandr-dev libxrender-dev
[*]  libxres-dev x11proto-core-dev x11proto-fixes-dev x11proto-input-dev
[*]  x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-resource-dev
[*]  x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
[*]0 pakketten opgewaardeerd, 66 nieuwe pakketten geïnstalleerd, 0 verwijderen en 0 niet opgewaardeerd.
[*]Er moeten 21,7MB aan archieven opgehaald worden.
[*]Na het uitpakken zal er 68,4MB extra schijfruimte gebruikt worden.
[*]Wilt u doorgaan [J/n]? j
[*]Ophalen:1 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main x11proto-core-dev 7.0.10-1 [86,3kB]
[*]Ophalen:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libfreetype6-dev 2.2.1-5ubuntu1.1 [640kB]
[*]Ophalen:3 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libice-dev 2:1.0.3-1build1 [55,9kB]
[*]Ophalen:4 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libsm-dev 2:1.0.2-1build1 [25,6kB]
[*]Ophalen:5 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libxau-dev 1:1.0.3-1 [15,5kB]
[*]Ophalen:6 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libxdmcp-dev 1:1.0.2-1 [19,8kB]
[*]Ophalen:7 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main x11proto-input-dev 1.4.1-1 [15,4kB]
[*]Ophalen:8 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main x11proto-kb-dev 1.0.3-2ubuntu1 [27,0kB]
[*]Ophalen:9 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main xtrans-dev 1.0.3-1 [69,2kB] 
[*]Ophalen:10 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libx11-dev 2:1.1.1-1ubuntu3 [8685kB]
[*]Ophalen:11 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libpng12-dev 1.2.15~beta5-1ubuntu1 [172kB]
[*]Ophalen:12 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main x11proto-render-dev 2:0.9.2-4ubuntu1 [6960B]
[*]Ophalen:13 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libxrender-dev 1:0.9.1-3 [24,4kB]
[*]Ophalen:14 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main x11proto-xext-dev 7.0.2-5ubuntu1 [42,2kB]
[*]Ophalen:15 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main x11proto-fixes-dev 1:4.0-0.1ubuntu2 [5662B]
[*]Ophalen:16 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libxfixes-dev 1:4.0.3-1 [12,1kB]
[*]Ophalen:17 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libxcursor-dev 1:1.1.8-1 [30,6kB]
[*]Ophalen:18 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libxext-dev 2:1.0.3-1build1 [81,5kB]
[*]Ophalen:19 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libexpat1-dev 1.95.8-3.4build1 [129kB]
[*]Ophalen:20 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main zlib1g-dev 1:1.2.3-13ubuntu4 [407kB]
[*]Ophalen:21 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libfontconfig1-dev 2.4.2-1ubuntu1 [344kB]
[*]Ophalen:22 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libxft-dev 2.1.12-1 [60,7kB]
[*]Ophalen:23 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libxi-dev 2:1.1.0-1build1 [67,7kB]
[*]Ophalen:24 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main x11proto-xinerama-dev 1.1.2-4ubuntu1 [5424B]
[*]Ophalen:25 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libxinerama-dev 2:1.0.1-4build1 [4196B]
[*]Ophalen:26 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main x11proto-randr-dev 1.2.1-1 [28,6kB]
[*]Ophalen:27 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libxrandr-dev 2:1.2.0-3ubuntu1 [27,5kB]
[*]Ophalen:28 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main x11proto-resource-dev 1.0.2-4ubuntu1 [3994B]
[*]Ophalen:29 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libxres-dev 2:1.0.1-2 [8048B]
[*]Ophalen:30 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libart-2.0-dev 2.3.17-1 [77,0kB]
[*]Ophalen:31 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libglib2.0-dev 2.12.11-0ubuntu1 [536kB]
[*]Ophalen:32 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libatk1.0-dev 1.18.0-0ubuntu1 [112kB]
[*]Ophalen:33 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libaudiofile-dev 0.2.6-6ubuntu3 [116kB]
[*]Ophalen:34 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libavahi-common-dev 0.6.17-0ubuntu3 [57,0kB]
[*]Ophalen:35 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty-updates/main libdbus-1-dev 1.0.2-1ubuntu4 [335kB]
[*]Ophalen:36 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libavahi-client-dev 0.6.17-0ubuntu3 [51,5kB]
[*]Ophalen:37 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libavahi-glib-dev 0.6.17-0ubuntu3 [27,7kB]
[*]Ophalen:38 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libidl-dev 0.8.7-0.1ubuntu2 [102kB]
[*]Ophalen:39 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main liborbit2-dev 1:2.14.7-0ubuntu1 [459kB]
[*]Ophalen:40 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libpopt-dev 1.10-3build1 [38,3kB]
[*]Ophalen:41 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libbonobo2-dev 2.18.0-0ubuntu1 [240kB]
[*]Ophalen:42 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libcairo2-dev 1.4.2-0ubuntu1 [507kB]
[*]Ophalen:43 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libpango1.0-dev 1.16.2-0ubuntu1 [355kB]
[*]Ophalen:44 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libgtk2.0-dev 2.10.11-0ubuntu3 [2590kB]
[*]Ophalen:45 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libgnomecanvas2-dev 2.14.0-3ubuntu2 [129kB]
[*]Ophalen:46 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libxml2-dev 2.6.27.dfsg-1ubuntu3 [672kB]
[*]Ophalen:47 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libglade2-dev 1:2.6.0-3 [129kB]
[*]Ophalen:48 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libgconf2-dev 2.18.0.1-0ubuntu1 [271kB]
[*]Ophalen:49 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libgpg-error-dev 1.4-2build1 [33,7kB]
[*]Ophalen:50 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libgcrypt11-dev 1.2.3-2build1 [248kB]
[*]Ophalen:51 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libtasn1-3-dev 0.3.6-2build1 [310kB]
[*]Ophalen:52 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libopencdk8-dev 0.5.9-2build1 [122kB]
[*]Ophalen:53 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main liblzo-dev 1.08-3 [109kB]  
[*]Ophalen:54 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libgnutls-dev 1.4.4-3build1 [358kB]
[*]Ophalen:55 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libsepol1-dev 1.14-2build1 [533kB]
[*]Ophalen:56 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libselinux1-dev 1.32-3ubuntu1 [203kB]
[*]Ophalen:57 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libgnomevfs2-dev 1:2.18.1-0ubuntu1 [533kB]
[*]Ophalen:58 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libesd0-dev 0.2.36-3ubuntu4 [24,3kB]
[*]Ophalen:59 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libgnome2-dev 2.18.0-0ubuntu1 [112kB]
[*]Ophalen:60 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libbonoboui2-dev 2.18.0-0ubuntu1 [286kB]
[*]Ophalen:61 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libgnome-keyring-dev 0.8.1-0ubuntu1 [54,1kB]
[*]Ophalen:62 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libjpeg62-dev 6b-13 [185kB]
[*]Ophalen:63 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libgnomeui-dev 2.17.92-0ubuntu1 [430kB]
[*]Ophalen:64 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libstartup-notification0-dev 0.9-1 [24,0kB]
[*]Ophalen:65 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libgnome-desktop-dev 1:2.18.1-0ubuntu1 [82,0kB]
[*]Ophalen:66 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) feisty/main libwnck-dev 2.18.0-0ubuntu1 [175kB]
[*]21,7MB opgehaald in 25s (855kB/s)                                              
[*]Extraheren van sjablonen uit pakketten: 100%
[*]Selecteren van voorheen niet geselecteerd pakket x11proto-core-dev.
[*](Database inlezen ... 118640 bestanden en mappen geïnstalleerd.)
[*]Uitpakken van x11proto-core-dev (uit .../x11proto-core-dev_7.0.10-1_all.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libice-dev.
[*]Uitpakken van libice-dev (uit .../libice-dev_2%3a1.0.3-1build1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libsm-dev.
[*]Uitpakken van libsm-dev (uit .../libsm-dev_2%3a1.0.2-1build1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libxau-dev.
[*]Uitpakken van libxau-dev (uit .../libxau-dev_1%3a1.0.3-1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libxdmcp-dev.
[*]Uitpakken van libxdmcp-dev (uit .../libxdmcp-dev_1%3a1.0.2-1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket x11proto-input-dev.
[*]Uitpakken van x11proto-input-dev (uit .../x11proto-input-dev_1.4.1-1_all.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket x11proto-kb-dev.
[*]Uitpakken van x11proto-kb-dev (uit .../x11proto-kb-dev_1.0.3-2ubuntu1_all.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket xtrans-dev.
[*]Uitpakken van xtrans-dev (uit .../xtrans-dev_1.0.3-1_all.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libx11-dev.
[*]Uitpakken van libx11-dev (uit .../libx11-dev_2%3a1.1.1-1ubuntu3_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket x11proto-render-dev.
[*]Uitpakken van x11proto-render-dev (uit .../x11proto-render-dev_2%3a0.9.2-4ubuntu1_all.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libxrender-dev.
[*]Uitpakken van libxrender-dev (uit .../libxrender-dev_1%3a0.9.1-3_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket x11proto-xext-dev.
[*]Uitpakken van x11proto-xext-dev (uit .../x11proto-xext-dev_7.0.2-5ubuntu1_all.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket x11proto-fixes-dev.
[*]Uitpakken van x11proto-fixes-dev (uit .../x11proto-fixes-dev_1%3a4.0-0.1ubuntu2_all.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libxfixes-dev.
[*]Uitpakken van libxfixes-dev (uit .../libxfixes-dev_1%3a4.0.3-1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libxcursor-dev.
[*]Uitpakken van libxcursor-dev (uit .../libxcursor-dev_1%3a1.1.8-1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libxext-dev.
[*]Uitpakken van libxext-dev (uit .../libxext-dev_2%3a1.0.3-1build1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libexpat1-dev.
[*]Uitpakken van libexpat1-dev (uit .../libexpat1-dev_1.95.8-3.4build1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket zlib1g-dev.
[*]Uitpakken van zlib1g-dev (uit .../zlib1g-dev_1%3a1.2.3-13ubuntu4_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libfreetype6-dev.
[*]Uitpakken van libfreetype6-dev (uit .../libfreetype6-dev_2.2.1-5ubuntu1.1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libfontconfig1-dev.
[*]Uitpakken van libfontconfig1-dev (uit .../libfontconfig1-dev_2.4.2-1ubuntu1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libxft-dev.
[*]Uitpakken van libxft-dev (uit .../libxft-dev_2.1.12-1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libxi-dev.
[*]Uitpakken van libxi-dev (uit .../libxi-dev_2%3a1.1.0-1build1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket x11proto-xinerama-dev.
[*]Uitpakken van x11proto-xinerama-dev (uit .../x11proto-xinerama-dev_1.1.2-4ubuntu1_all.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libxinerama-dev.
[*]Uitpakken van libxinerama-dev (uit .../libxinerama-dev_2%3a1.0.1-4build1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket x11proto-randr-dev.
[*]Uitpakken van x11proto-randr-dev (uit .../x11proto-randr-dev_1.2.1-1_all.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libxrandr-dev.
[*]Uitpakken van libxrandr-dev (uit .../libxrandr-dev_2%3a1.2.0-3ubuntu1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket x11proto-resource-dev.
[*]Uitpakken van x11proto-resource-dev (uit .../x11proto-resource-dev_1.0.2-4ubuntu1_all.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libxres-dev.
[*]Uitpakken van libxres-dev (uit .../libxres-dev_2%3a1.0.1-2_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libart-2.0-dev.
[*]Uitpakken van libart-2.0-dev (uit .../libart-2.0-dev_2.3.17-1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libglib2.0-dev.
[*]Uitpakken van libglib2.0-dev (uit .../libglib2.0-dev_2.12.11-0ubuntu1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libatk1.0-dev.
[*]Uitpakken van libatk1.0-dev (uit .../libatk1.0-dev_1.18.0-0ubuntu1_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libaudiofile-dev.
[*]Uitpakken van libaudiofile-dev (uit .../libaudiofile-dev_0.2.6-6ubuntu3_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libavahi-common-dev.
[*]Uitpakken van libavahi-common-dev (uit .../libavahi-common-dev_0.6.17-0ubuntu3_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libdbus-1-dev.
[*]Uitpakken van libdbus-1-dev (uit .../libdbus-1-dev_1.0.2-1ubuntu4_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libavahi-client-dev.
[*]Uitpakken van libavahi-client-dev (uit .../libavahi-client-dev_0.6.17-0ubuntu3_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libavahi-glib-dev.
[*]Uitpakken van libavahi-glib-dev (uit .../libavahi-glib-dev_0.6.17-0ubuntu3_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket libidl-dev.
[*]Uitpakken van libidl-dev (uit .../libidl-dev_0.8.7-0.1ubuntu2_i386.deb) ...
[*]Selecteren van voorheen niet geselecteerd pakket liborbit2-dev.
[*]Uitpakken van liborbit2-dev (uit .../liborbit2-dev_1%3a2.14.7-0ubuntu1_i386.deb) ...
[*]E: Sub-process /usr/bin/dpkg exited unexpectedly
[*]djonah@djonah-laptop:~/avant-window-navigator-0.1.1$ ./configurechecking for a BSD-compatible install... /usr/bin/install -cchecking whether build environment is sane... yes
[*]checking for gawk... no
[*]checking for mawk... mawk
[*]checking whether make sets $(MAKE)... yes
[*]checking how to create a ustar tar archive... gnutar
[*]checking whether to enable maintainer-specific portions of Makefiles... no
[*]checking for style of include used by make... GNU
[*]checking for gcc... gcc
[*]checking for C compiler default output file name... a.out
[*]checking whether the C compiler works... yes
[*]checking whether we are cross compiling... no
[*]checking for suffix of executables... 
[*]checking for suffix of object files... o
[*]checking whether we are using the GNU C compiler... yes
[*]checking whether gcc accepts -g... yes
[*]checking for gcc option to accept ANSI C... none needed
[*]checking dependency style of gcc... gcc3
[*]checking for library containing strerror... none required
[*]checking for gcc... (cached) gcc
[*]checking whether we are using the GNU C compiler... (cached) yes
[*]checking whether gcc accepts -g... (cached) yes
[*]checking for gcc option to accept ANSI C... (cached) none needed
[*]checking dependency style of gcc... (cached) gcc3
[*]checking how to run the C preprocessor... gcc -E
[*]checking for egrep... grep -E
[*]checking for ANSI C header files... yes
[*]checking build system type... i686-pc-linux-gnu
[*]checking host system type... i686-pc-linux-gnu
[*]checking for a sed that does not truncate output... /bin/sed
[*]checking for ld used by gcc... /usr/bin/ld
[*]checking if the linker (/usr/bin/ld) is GNU ld... yes
[*]checking for /usr/bin/ld option to reload object files... -r
[*]checking for BSD-compatible nm... /usr/bin/nm -B
[*]checking whether ln -s works... yes
[*]checking how to recognise dependent libraries... pass_all
[*]checking for sys/types.h... yes
[*]checking for sys/stat.h... yes
[*]checking for stdlib.h... yes
[*]checking for string.h... yes
[*]checking for memory.h... yes
[*]checking for strings.h... yes
[*]checking for inttypes.h... yes
[*]checking for stdint.h... yes
[*]checking for unistd.h... yes
[*]checking dlfcn.h usability... yes
[*]checking dlfcn.h presence... yes
[*]checking for dlfcn.h... yes
[*]checking for g++... g++
[*]checking whether we are using the GNU C++ compiler... yes
[*]checking whether g++ accepts -g... yes
[*]checking dependency style of g++... gcc3
[*]checking how to run the C++ preprocessor... g++ -E
[*]checking for g77... no
[*]checking for f77... no
[*]checking for xlf... no
[*]checking for frt... no
[*]checking for pgf77... no
[*]checking for fort77... no
[*]checking for fl32... no
[*]checking for af77... no
[*]checking for f90... no
[*]checking for xlf90... no
[*]checking for pgf90... no
[*]checking for epcf90... no
[*]checking for f95... no
[*]checking for fort... no
[*]checking for xlf95... no
[*]checking for ifc... no
[*]checking for efc... no
[*]checking for pgf95... no
[*]checking for lf95... no
[*]checking for gfortran... no
[*]checking whether we are using the GNU Fortran 77 compiler... no
[*]checking whether  accepts -g... no
[*]checking the maximum length of command line arguments... 32768
[*]checking command to parse /usr/bin/nm -B output from gcc object... ok
[*]checking for objdir... .libs
[*]checking for ar... ar
[*]checking for ranlib... ranlib
[*]checking for strip... strip
[*]checking if gcc supports -fno-rtti -fno-exceptions... no
[*]checking for gcc option to produce PIC... -fPIC
[*]checking if gcc PIC flag -fPIC works... yes
[*]checking if gcc static flag -static works... yes
[*]checking if gcc supports -c -o file.o... yes
[*]checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
[*]checking whether -lc should be explicitly linked in... no
[*]checking dynamic linker characteristics... GNU/Linux ld.so
[*]checking how to hardcode library paths into programs... immediate
[*]checking whether stripping libraries is possible... yes
[*]checking if libtool supports shared libraries... yes
[*]checking whether to build shared libraries... yes
[*]checking whether to build static libraries... yes
[*]configure: creating libtool
[*]appending configuration tag "CXX" to libtool
[*]checking for ld used by g++... /usr/bin/ld
[*]checking if the linker (/usr/bin/ld) is GNU ld... yes
[*]checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
[*]checking for g++ option to produce PIC... -fPIC
[*]checking if g++ PIC flag -fPIC works... yes
[*]checking if g++ static flag -static works... yes
[*]checking if g++ supports -c -o file.o... yes
[*]checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
[*]checking dynamic linker characteristics... GNU/Linux ld.so
[*]checking how to hardcode library paths into programs... immediate
[*]appending configuration tag "F77" to libtool
[*]checking for intltool >= 0.34... 0.35.0 found
[*]checking for perl... /usr/bin/perl
[*]checking for XML::Parser... ok
[*]checking for iconv... /usr/bin/iconv
[*]checking for msgfmt... msgfmt
[*]checking for msgmerge... msgmerge
[*]checking for xgettext... xgettext
[*]checking locale.h usability... yes
[*]checking locale.h presence... yes
[*]checking for locale.h... yes
[*]checking for LC_MESSAGES... yes
[*]checking libintl.h usability... yes
[*]checking libintl.h presence... yes
[*]checking for libintl.h... yes
[*]checking for ngettext in libc... yes
[*]checking for dgettext in libc... yes
[*]checking for bind_textdomain_codeset... yes
[*]checking for msgfmt... no
[*]checking for pkg-config... /usr/bin/pkg-config
[*]checking pkg-config is at least version 0.7... yes
[*]checking for GLIB - version >= 2.8.0... yes (version 2.12.11)
[*]checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gconf-2.0) were not met:

[*]No package 'gtk+-2.0' found
[*]No package 'gdk-2.0' found
[*]No package 'libwnck-1.0' found
[*]No package 'gconf-2.0' found

[*]Consider adjusting the PKG_CONFIG_PATH environment variable if you
[*]installed software in a non-standard prefix.

[*]Alternatively, you may set the environment variables AWN_CFLAGS
[*]and AWN_LIBS to avoid the need to call pkg-config.
[*]See the pkg-config man page for more details.

[*]djonah@djonah-laptop:~/avant-window-navigator-0.1.1$ make
[*]make: *** No targets specified and no makefile found.  Stop.
[*]djonah@djonah-laptop:~/avant-window-navigator-0.1.1$ sudo make install
[*]make: *** No rule to make target `install'.  Stop.
[*]djonah@djonah-laptop:~/avant-window-navigator-0.1.1$
[/LIST]

Thanks for  the help!
greetz

---

