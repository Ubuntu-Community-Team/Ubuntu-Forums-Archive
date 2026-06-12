---
title: "Software Updater offers partial upgrade."
date: 2014-07-03
forum: Installation &amp; Upgrades
---

### Post by drprinsloo on 2014-07-03
I just tried to run "Updater" and I get the message as shown in the attached thumbnail.
What do I do?

---

### Post by drprinsloo on 2014-07-03
[COLOR=#000000]I just tried to run "Updater" and I get the message as shown in the attached thumbnail.[/COLOR]
[COLOR=#000000]What do I do?[/COLOR]

---

### Post by coffeecat on 2014-07-03
@drprinsloo, you posted to two threads, neither of which was appropriate to your particular problem. It is generally better to start your own thread. I have moved your two posts to their own thread, and given it an appropriate title.

---

### Post by drprinsloo on 2014-07-03
Thank you so much. I was not sure where to post the query, which is why I posted in two different places. I thank you for doing this as I am new to communicating on forums.

---

### Post by coffeecat on 2014-07-03
It would be useful to those helping you if you could provide some more information. To help this along, here are some questions to answer:

1 - Which version of Ubuntu are you using? That is, the release number code, such as "14.04".

2 - Have you added any 3rd party repositories, such as PPAs?

3 - Did you upgrade your system from an earlier release?

It would also be useful if you provided some terminal output. Open a terminal (ctrl-alt-t) and run these two commands:

```
sudo apt-get update
sudo apt-get -s upgrade
```

The second won't actually do an upgrade - just give us some useful output to see what would happen if you proceeded.

The output will be lengthy. You can copy and paste it into your post by highlighting the output, right-click -> copy and then pasting it with ctrl-v or however you like to do a paste. Please enclose the output in [noparse]```
 and 
```[/noparse] tags for clarity.

---

### Post by drprinsloo on 2014-07-03
I've been using Ubuntu exclusively for many years already. I started off with 5.10 if I remember correctly and I am currently using 14.04 LTS, which I upgraded to when it was released. 
Today I just wanted to check for updates and this message popped up. 
I have to add that we had a power failure for a few hours, which means that my PC had not shut down correctly. The moment I switched it on, it said there was some system program error and I should restart, which I did, but to no avail.
I've learned over the years to not run weird software on my PC, but the most recent addition was LibreCAD.

I ran both, one after the other, and both went smooth, without any errors?
Does this mean that the problem was with running "Updater"?

```
sty-updates [i386]) [libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst libmessagelist4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst libmessagecore4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libkdepim4:i386 libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst libksieveui4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libkdepim4:i386 libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst blogilo [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libkdepim4:i386 libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst libpimcommon4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libkdepim4:i386 libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst libmailimporter4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libkdepim4:i386 libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst libincidenceeditorsng4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libkdepim4:i386 libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst libkdepim4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst libmailcommon4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libmessagecomposer4:i386 ]
Inst libmessagecomposer4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libsendlater4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libcalendarsupport4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkdepimdbusinterfaces4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkdgantt2-0 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libqgpgme1 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libgpgme++2 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkpgp4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libbaloopim4 [4:4.13.0-0ubuntu3] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkleo4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libksieve4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkmanagesieve4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkontactinterface4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libakonadi-kabc4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst kdepim-runtime [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libcomposereditorng4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst network-manager-gnome [0.9.8.8-0ubuntu4.1] (0.9.8.8-0ubuntu4.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libnm-gtk0 [0.9.8.8-0ubuntu4.1] (0.9.8.8-0ubuntu4.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libnm-gtk-common [0.9.8.8-0ubuntu4.1] (0.9.8.8-0ubuntu4.2 Ubuntu:14.04/trusty-updates [all])
Inst libunity-control-center1 [14.04.3+14.04.20140410-0ubuntu1] (14.04.3+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst nautilus-data [1:3.10.1-0ubuntu9] (1:3.10.1-0ubuntu9.2 Ubuntu:14.04/trusty-updates [all])
Inst gnome-settings-daemon-schemas [3.8.6.1-0ubuntu11.1] (3.8.6.1-0ubuntu11.2 Ubuntu:14.04/trusty-updates [all]) [gnome-settings-daemon:i386 ]
Inst gnome-settings-daemon [3.8.6.1-0ubuntu11.1] (3.8.6.1-0ubuntu11.2 Ubuntu:14.04/trusty-updates [i386])
Inst unity-settings-daemon [14.04.0+14.04.20140414-0ubuntu1] (14.04.0+14.04.20140606-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst unity-control-center [14.04.3+14.04.20140410-0ubuntu1] (14.04.3+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst libcompizconfig0 [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386]) []
Inst compiz-plugins [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386]) []
Inst compiz-gnome [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386]) []
Inst compiz-plugins-default [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libdecoration0 [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386]) []
Inst compiz-core [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst compiz [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst cups-browsed [1.0.52-0ubuntu1.1] (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst cups-filters-core-drivers [1.0.52-0ubuntu1.1] (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst cups-filters [1.0.52-0ubuntu1.1] (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst libkonqsidebarplugin4a [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst kde-baseapps-data [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all]) [kde-baseapps-bin:i386 konqueror:i386 ]
Inst konqueror [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [kde-baseapps-bin:i386 ]
Inst kde-baseapps-bin [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst dolphin [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst evince [3.10.3-0ubuntu10] (3.10.3-0ubuntu10.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libevdocument3-4 [3.10.3-0ubuntu10] (3.10.3-0ubuntu10.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libevview3-3 [3.10.3-0ubuntu10] (3.10.3-0ubuntu10.1 Ubuntu:14.04/trusty-updates [i386])
Inst libnautilus-extension1a [1:3.10.1-0ubuntu9] (1:3.10.1-0ubuntu9.2 Ubuntu:14.04/trusty-updates [i386])
Inst evince-common [3.10.3-0ubuntu10] (3.10.3-0ubuntu10.1 Ubuntu:14.04/trusty-updates [all])
Inst ffmpegthumbs [4:4.13.0-0ubuntu1] (4:4.13.1-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst fontconfig [2.11.0-0ubuntu4] (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [i386])
Inst gir1.2-gudev-1.0 [1:204-5ubuntu20.2] (1:204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Inst gir1.2-webkit-3.0 [2.4.2-1ubuntu0.1] (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386]) []
Inst gir1.2-javascriptcoregtk-3.0 [2.4.2-1ubuntu0.1] (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst gir1.2-nmgtk-1.0 [0.9.8.8-0ubuntu4.1] (0.9.8.8-0ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Inst gnome-sudoku [1:3.10.2-0ubuntu2] (1:3.10.2-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Inst printer-driver-postscript-hp [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [all]) []
Inst printer-driver-hpijs [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libsane-hpaio [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386]) [hplip:i386 ]
Inst hplip [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libhpmud0 [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst hplip-data [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [all]) []
Inst printer-driver-hpcups [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386])
Inst hud [13.10.1+14.04.20140402-0ubuntu1] (14.04+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst juk [4:4.13.0-0ubuntu1] (4:4.13.1-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst kde-config-pimactivity [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libpimactivity4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst kdebase-bin [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Inst kdebase-runtime [4:4.13.0-0ubuntu1.1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Inst kfind [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst konqueror-nsplugins [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst marble-plugins [4:4.13.0-0ubuntu1.1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst marble-data [4:4.13.0-0ubuntu1.1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all]) []
Inst libmarblewidget18 [4:4.13.0-0ubuntu1.1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libastro1 [4:4.13.0-0ubuntu1.1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst libgphoto2-l10n [2.5.3.1-1ubuntu2] (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [all])
Inst libgtk-3-bin [3.10.8-0ubuntu1] (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libkcompactdisc4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst libkcddb4 [4:4.13.0-0ubuntu1] (4:4.13.1-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst libkworkspace4abi2 [4:4.11.8-0ubuntu6] (4:4.11.10-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst libtar0 [1.2.20-3] (1.2.20-3ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst unity [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libunity-core-6.0-9 [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [i386]) []
Inst unity-services [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst libunity-2d-private0 [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst whoopsie [0.2.24.5] (0.2.24.6 Ubuntu:14.04/trusty-updates [i386]) []
Inst libwhoopsie0 [0.2.24.5] (0.2.24.6 Ubuntu:14.04/trusty-updates [i386])
Inst nautilus [1:3.10.1-0ubuntu9] (1:3.10.1-0ubuntu9.2 Ubuntu:14.04/trusty-updates [i386])
Inst telepathy-gabble [0.18.2-1] (0.18.3-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst xul-ext-ubufox [2.8-0ubuntu1] (2.9-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst ubufox [2.8-0ubuntu1] (2.9-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst unity-2d [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst unity-2d-common [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst unity-2d-panel [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst unity-2d-shell [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst unity-2d-spread [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst usb-creator-gtk [0.2.56] (0.2.56.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst usb-creator-common [0.2.56] (0.2.56.1 Ubuntu:14.04/trusty-updates [i386])
Inst compizconfig-backend-gconf [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst indicator-printers [0.1.7+14.04.20140313-0ubuntu1] (0.1.7+14.04.20140527-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst kolourpaint4 [4:4.13.0-0ubuntu1] (4:4.13.1-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf resolvconf (1.69ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libcgmanager0 (0.24-0ubuntu7 Ubuntu:14.04/trusty-updates [i386])
Conf libudev1 (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf udev (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf libsystemd-daemon0 (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf systemd-services (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf libpam-systemd (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf libsystemd-login0 (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf libboost-date-time1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Conf libboost-system1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Conf libboost-filesystem1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Conf libboost-program-options1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Conf libboost-regex1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Conf libboost-signals1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Conf libboost-thread1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Conf libcupsfilters1 (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf libdbusmenu-glib4 (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-dbusmenu-glib-0.4 (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libdbusmenu-gtk3-4 (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libdbusmenu-gtk4 (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-dbusmenu-gtk-0.4 (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf fontconfig-config (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [all])
Conf libfontconfig1 (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [i386])
Conf libfontconfig1-dev (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [i386])
Conf libfontembed1 (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf libgtk-3-common (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libgtk-3-0 (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-gtk-3.0 (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libgtk-3-dev (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libgail-3-0 (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libgphoto2-port10 (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [i386])
Conf libgphoto2-6 (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [i386])
Conf libgudev-1.0-0 (1:204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf libhud2 (14.04+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libwebkitgtk-1.0-common (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf libjavascriptcoregtk-1.0-0 (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libwebkitgtk-1.0-0 (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libwebkitgtk-3.0-common (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf libjavascriptcoregtk-3.0-0 (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libwebkitgtk-3.0-0 (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libspectre1 (0.2.7-2ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libsystemd-journal0 (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf initramfs-tools-bin (0.103ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Conf initramfs-tools (0.103ubuntu4.2 Ubuntu:14.04/trusty-updates [all])
Conf uuid-runtime (2.20.1-5.1ubuntu20.1 Ubuntu:14.04/trusty-updates [i386])
Conf nepomuk-core-data (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf kate-data (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf libkdecore5 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkdeui5 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libnepomuk4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libsolid4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkio5 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libnepomukcore4abi1 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkactivities-models1 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkactivities6 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkcmutils4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkdeclarative5 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libnepomukquery4a (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libnepomukutils4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkparts4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkdewebkit5 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkdnssd4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libknewstuff3-4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libthreadweaver4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libplasma3 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkactivities-bin (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libakonadi-kde4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkmime4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libakonadi-kmime4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libbaloocore4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libbalooxapian4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libbaloofiles4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkldap4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkresources4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkabc4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkcalcore4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkfilemetadata4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkidletime4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkemoticons4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkpimutils4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf baloo (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kde-runtime-data (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf libnepomukcleaner4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf nepomuk-core-runtime (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkpty4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkdesu5 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkfile4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkjsapi4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libktexteditor4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkhtml5 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkmediaplayer4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libknotifyconfig4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkxmlrpcclient4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkde3support4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkjsembed4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkntlm4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkrosscore4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf kdelibs5-data (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [all])
Conf kdoctools (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf kdelibs-bin (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkatepartinterfaces4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf katepart (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kdelibs5-plugins (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf plasma-scriptengine-javascript (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kde-runtime (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkrossui4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkprintutils4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkutils4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkcal4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libsyndication4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkblog4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libakonadi-kcal4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmicroblog4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkpimtextedit4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkpimidentities4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkcalutils4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libktnef4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libakonadi-contact4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmailtransport4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libakonadi-calendar4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkholidays4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkalarmcal2 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkmbox4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkimap4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kdepimlibs-kio-plugins (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libakonadi-notes4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libakonadi-socialutils4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkonq5-templates (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf libkonq-common (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkonq5abi1 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf ark (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libakonadi-kabc4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kdepim-runtime (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkdepimdbusinterfaces4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libcalendarsupport4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libgpgme++2 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libbaloopim4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libpimcommon4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmessagecore4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkdgantt2-0 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libincidenceeditorsng4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libqgpgme1 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkleo4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkpgp4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmessageviewer4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libsendlater4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libtemplateparser4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmessagecomposer4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmailcommon4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkdepim4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmailimporter4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkmanagesieve4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkontactinterface4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libksieve4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libksieveui4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmessagelist4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kmail (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libcomposereditorng4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf blogilo (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libnm-gtk-common (0.9.8.8-0ubuntu4.2 Ubuntu:14.04/trusty-updates [all])
Conf libnm-gtk0 (0.9.8.8-0ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Conf network-manager-gnome (0.9.8.8-0ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Conf libunity-control-center1 (14.04.3+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf nautilus-data (1:3.10.1-0ubuntu9.2 Ubuntu:14.04/trusty-updates [all])
Conf gnome-settings-daemon-schemas (3.8.6.1-0ubuntu11.2 Ubuntu:14.04/trusty-updates [all])
Conf gnome-settings-daemon (3.8.6.1-0ubuntu11.2 Ubuntu:14.04/trusty-updates [i386])
Conf unity-settings-daemon (14.04.0+14.04.20140606-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf unity-control-center (14.04.3+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf compiz-core (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libcompizconfig0 (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libdecoration0 (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf compiz-plugins-default (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf compiz-plugins (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf compiz-gnome (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf compiz (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf cups-browsed (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf cups-filters-core-drivers (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf cups-filters (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkonqsidebarplugin4a (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kde-baseapps-data (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf kde-baseapps-bin (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf konqueror (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf dolphin (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libevdocument3-4 (3.10.3-0ubuntu10.1 Ubuntu:14.04/trusty-updates [i386])
Conf libevview3-3 (3.10.3-0ubuntu10.1 Ubuntu:14.04/trusty-updates [i386])
Conf libnautilus-extension1a (1:3.10.1-0ubuntu9.2 Ubuntu:14.04/trusty-updates [i386])
Conf evince-common (3.10.3-0ubuntu10.1 Ubuntu:14.04/trusty-updates [all])
Conf evince (3.10.3-0ubuntu10.1 Ubuntu:14.04/trusty-updates [i386])
Conf ffmpegthumbs (4:4.13.1-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf fontconfig (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-gudev-1.0 (1:204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-javascriptcoregtk-3.0 (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-webkit-3.0 (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-nmgtk-1.0 (0.9.8.8-0ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Conf gnome-sudoku (1:3.10.2-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Conf libhpmud0 (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386])
Conf libsane-hpaio (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386])
Conf hplip-data (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [all])
Conf printer-driver-hpcups (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386])
Conf hplip (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386])
Conf printer-driver-postscript-hp (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [all])
Conf printer-driver-hpijs (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386])
Conf hud (14.04+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf juk (4:4.13.1-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libpimactivity4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kde-config-pimactivity (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kdebase-bin (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf kdebase-runtime (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf kfind (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf konqueror-nsplugins (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf marble-data (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf libastro1 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmarblewidget18 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf marble-plugins (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libgphoto2-l10n (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [all])
Conf libgtk-3-bin (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkcompactdisc4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkcddb4 (4:4.13.1-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkworkspace4abi2 (4:4.11.10-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libtar0 (1.2.20-3ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf unity-services (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libunity-core-6.0-9 (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf unity (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libunity-2d-private0 (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf libwhoopsie0 (0.2.24.6 Ubuntu:14.04/trusty-updates [i386])
Conf whoopsie (0.2.24.6 Ubuntu:14.04/trusty-updates [i386])
Conf nautilus (1:3.10.1-0ubuntu9.2 Ubuntu:14.04/trusty-updates [i386])
Conf telepathy-gabble (0.18.3-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf xul-ext-ubufox (2.9-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf ubufox (2.9-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf unity-2d (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf unity-2d-common (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf unity-2d-panel (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf unity-2d-shell (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf unity-2d-spread (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf usb-creator-common (0.2.56.1 Ubuntu:14.04/trusty-updates [i386])
Conf usb-creator-gtk (0.2.56.1 Ubuntu:14.04/trusty-updates [i386])
Conf compizconfig-backend-gconf (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf indicator-printers (0.1.7+14.04.20140527-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf kolourpaint4 (4:4.13.1-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
drsjp@Biocura-PC:~$ ^C
drsjp@Biocura-PC:~$ ^C
drsjp@Biocura-PC:~$
```

---

### Post by slickymaster on 2014-07-03
@drprinsloo
I edit your last post, adding code tags to it. Output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers, like coffeecat previously said.

---

### Post by coffeecat on 2014-07-03
Your posted output is incomplete - no output of update and you ctrl-c cancelled upgrade. Let's try it a different way. Run:

```
sudo apt-get update > ~/Desktop/update.txt
sudo apt-get -s upgrade > ~/Desktop/upgrade.txt
```

You'll get two text files on your desktop, update.txt and upgrade.txt. Add them as attachments to a post by using the Manage Attachments button which you can find below the advanced message editor.

---

### Post by drprinsloo on 2014-07-03
txt file exceeds forum limits. Here is Update.txt

```
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty InRelease
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates InRelease
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty Release.gpg
Get:1 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates Release.gpg [933 B]
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty Release
Get:2 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates Release [58,5 kB]
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/main Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/restricted Sources
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/universe Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/multiverse Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/main i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/restricted i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/universe i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/multiverse i386 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/main Translation-en
Hit [http://dl.google.com](http://dl.google.com) stable Release
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/restricted Translation-en
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/universe Translation-en
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages
Get:3 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/main Sources [80,4 kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources
Get:5 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/restricted Sources [14 B]
Get:6 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/universe Sources [60,1 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [58,5 kB]
Get:8 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/multiverse Sources [2 681 B]
Get:9 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/main i386 Packages [210 kB]
Get:10 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/restricted i386 Packages [14 B]
Get:11 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/universe i386 Packages [154 kB]
Get:12 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [7 569 B]
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/main Translation-en
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/universe Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_ZA
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_ZA
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [30,6 kB]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_ZA
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/main Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/multiverse Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/universe Translation-en_ZA
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/universe Translation-en_US
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/main Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/main Translation-en_US
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/multiverse Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/restricted Translation-en_US
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/universe Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/universe Translation-en_US
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [6 808 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [688 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [102 kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [35,9 kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1 392 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US
Fetched 811 kB in 21s (37,0 kB/s)
Reading package lists...
```

---

### Post by drprinsloo on 2014-07-03
upgrade.txt
```

Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  flam3 linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-headers-3.13.0-27 linux-headers-3.13.0-27-generic
  linux-image-3.13.0-24-generic linux-image-3.13.0-27-generic
  linux-image-extra-3.13.0-24-generic linux-image-extra-3.13.0-27-generic
  python3-dirspec
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  ark baloo blogilo bsdutils compiz compiz-core compiz-gnome compiz-plugins
  compiz-plugins-default compizconfig-backend-gconf cups-browsed cups-filters
  cups-filters-core-drivers dolphin evince evince-common ffmpegthumbs
  fontconfig fontconfig-config gir1.2-dbusmenu-glib-0.4
  gir1.2-dbusmenu-gtk-0.4 gir1.2-gtk-3.0 gir1.2-gudev-1.0
  gir1.2-javascriptcoregtk-3.0 gir1.2-nmgtk-1.0 gir1.2-webkit-3.0
  gnome-settings-daemon gnome-settings-daemon-schemas gnome-sudoku hplip
  hplip-data hud indicator-printers initramfs-tools initramfs-tools-bin
  intel-gpu-tools juk kate-data katepart kde-baseapps-bin kde-baseapps-data
  kde-config-pimactivity kde-runtime kde-runtime-data kdebase-bin
  kdebase-runtime kdelibs-bin kdelibs5-data kdelibs5-plugins kdepim-runtime
  kdepimlibs-kio-plugins kdoctools kfind kmail kolourpaint4 konqueror
  konqueror-nsplugins libakonadi-calendar4 libakonadi-contact4
  libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4
  libakonadi-notes4 libakonadi-socialutils4 libastro1 libbaloocore4
  libbaloofiles4 libbaloopim4 libbalooxapian4 libblkid1
  libboost-date-time1.54.0 libboost-filesystem1.54.0
  libboost-program-options1.54.0 libboost-regex1.54.0 libboost-signals1.54.0
  libboost-system1.54.0 libboost-thread1.54.0 libcalendarsupport4
  libcgmanager0 libcompizconfig0 libcomposereditorng4 libcupsfilters1
  libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdecoration0
  libevdocument3-4 libevview3-3 libfontconfig1 libfontconfig1-dev
  libfontembed1 libgail-3-0 libgpgme++2 libgphoto2-6 libgphoto2-l10n
  libgphoto2-port10 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk-3-dev
  libgudev-1.0-0 libhpmud0 libhud2 libincidenceeditorsng4
  libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0 libkabc4
  libkactivities-bin libkactivities-models1 libkactivities6 libkalarmcal2
  libkatepartinterfaces4 libkblog4 libkcal4 libkcalcore4 libkcalutils4
  libkcddb4 libkcmutils4 libkcompactdisc4 libkde3support4 libkdeclarative5
  libkdecore5 libkdepim4 libkdepimdbusinterfaces4 libkdesu5 libkdeui5
  libkdewebkit5 libkdgantt2-0 libkdnssd4 libkemoticons4 libkfile4
  libkfilemetadata4 libkholidays4 libkhtml5 libkidletime4 libkimap4 libkio5
  libkjsapi4 libkjsembed4 libkldap4 libkleo4 libkmanagesieve4 libkmbox4
  libkmediaplayer4 libkmime4 libknewstuff3-4 libknotifyconfig4 libkntlm4
  libkonq-common libkonq5-templates libkonq5abi1 libkonqsidebarplugin4a
  libkontactinterface4 libkparts4 libkpgp4 libkpimidentities4 libkpimtextedit4
  libkpimutils4 libkprintutils4 libkpty4 libkresources4 libkrosscore4
  libkrossui4 libksieve4 libksieveui4 libktexteditor4 libktnef4 libkutils4
  libkworkspace4abi2 libkxmlrpcclient4 libmailcommon4 libmailimporter4
  libmailtransport4 libmarblewidget18 libmessagecomposer4 libmessagecore4
  libmessagelist4 libmessageviewer4 libmicroblog4 libmount1
  libnautilus-extension1a libnepomuk4 libnepomukcleaner4 libnepomukcore4abi1
  libnepomukquery4a libnepomukutils4 libnm-gtk-common libnm-gtk0
  libpam-systemd libpimactivity4 libpimcommon4 libplasma3 libqgpgme1
  libsane-hpaio libsendlater4 libsolid4 libspectre1 libsyndication4
  libsystemd-daemon0 libsystemd-journal0 libsystemd-login0 libtar0
  libtemplateparser4 libthreadweaver4 libudev1 libunity-2d-private0
  libunity-control-center1 libunity-core-6.0-9 libuuid1 libwebkitgtk-1.0-0
  libwebkitgtk-1.0-common libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
  libwhoopsie0 marble-data marble-plugins mount nautilus nautilus-data
  nepomuk-core-data nepomuk-core-runtime network-manager-gnome
  plasma-scriptengine-javascript printer-driver-hpcups printer-driver-hpijs
  printer-driver-postscript-hp resolvconf shotwell shotwell-common
  systemd-services telepathy-gabble ubufox udev unity unity-2d unity-2d-common
  unity-2d-panel unity-2d-shell unity-2d-spread unity-control-center
  unity-services unity-settings-daemon usb-creator-common usb-creator-gtk
  util-linux uuid-runtime whoopsie xul-ext-ubufox
249 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Inst mount [2.20.1-5.1ubuntu20] (2.20.1-5.1ubuntu20.1 Ubuntu:14.04/trusty-updates [i386])
Conf mount (2.20.1-5.1ubuntu20.1 Ubuntu:14.04/trusty-updates [i386])
Inst util-linux [2.20.1-5.1ubuntu20] (2.20.1-5.1ubuntu20.1 Ubuntu:14.04/trusty-updates [i386])
Conf util-linux (2.20.1-5.1ubuntu20.1 Ubuntu:14.04/trusty-updates [i386])
Inst bsdutils [1:2.20.1-5.1ubuntu20] (1:2.20.1-5.1ubuntu20.1 Ubuntu:14.04/trusty-updates [i386])
Conf bsdutils (1:2.20.1-5.1ubuntu20.1 Ubuntu:14.04/trusty-updates [i386])
Inst libuuid1 [2.20.1-5.1ubuntu20] (2.20.1-5.1ubuntu20.1 Ubuntu:14.04/trusty-updates [i386])
Conf libuuid1 (2.20.1-5.1ubuntu20.1 Ubuntu:14.04/trusty-updates [i386])
Inst libblkid1 [2.20.1-5.1ubuntu20] (2.20.1-5.1ubuntu20.1 Ubuntu:14.04/trusty-updates [i386])
Conf libblkid1 (2.20.1-5.1ubuntu20.1 Ubuntu:14.04/trusty-updates [i386])
Inst libmount1 [2.20.1-5.1ubuntu20] (2.20.1-5.1ubuntu20.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmount1 (2.20.1-5.1ubuntu20.1 Ubuntu:14.04/trusty-updates [i386])
Inst resolvconf [1.69ubuntu1] (1.69ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst libcgmanager0 [0.24-0ubuntu6] (0.24-0ubuntu7 Ubuntu:14.04/trusty-updates [i386])
Inst udev [204-5ubuntu20.2] (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386]) []
Inst libudev1 [204-5ubuntu20.2] (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Inst libpam-systemd [204-5ubuntu20.2] (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386]) []
Inst systemd-services [204-5ubuntu20.2] (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386]) []
Inst libsystemd-daemon0 [204-5ubuntu20.2] (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Inst libsystemd-login0 [204-5ubuntu20.2] (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Inst libboost-date-time1.54.0 [1.54.0-4ubuntu3] (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Inst libboost-system1.54.0 [1.54.0-4ubuntu3] (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Inst libboost-filesystem1.54.0 [1.54.0-4ubuntu3] (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Inst libboost-program-options1.54.0 [1.54.0-4ubuntu3] (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Inst libboost-regex1.54.0 [1.54.0-4ubuntu3] (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Inst libboost-signals1.54.0 [1.54.0-4ubuntu3] (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Inst libboost-thread1.54.0 [1.54.0-4ubuntu3] (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Inst libcupsfilters1 [1.0.52-0ubuntu1.1] (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst gir1.2-dbusmenu-glib-0.4 [12.10.3+14.04.20140319-0ubuntu1] (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libdbusmenu-glib4 [12.10.3+14.04.20140319-0ubuntu1] (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst libdbusmenu-gtk3-4 [12.10.3+14.04.20140319-0ubuntu1] (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst gir1.2-dbusmenu-gtk-0.4 [12.10.3+14.04.20140319-0ubuntu1] (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libdbusmenu-gtk4 [12.10.3+14.04.20140319-0ubuntu1] (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst libfontconfig1-dev [2.11.0-0ubuntu4] (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libfontconfig1 [2.11.0-0ubuntu4] (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst fontconfig-config [2.11.0-0ubuntu4] (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [all])
Inst libfontembed1 [1.0.52-0ubuntu1.1] (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst libgtk-3-common [3.10.8-0ubuntu1] (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst libgtk-3-dev [3.10.8-0ubuntu1] (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst gir1.2-gtk-3.0 [3.10.8-0ubuntu1] (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libgail-3-0 [3.10.8-0ubuntu1] (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libgtk-3-0 [3.10.8-0ubuntu1] (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libgphoto2-port10 [2.5.3.1-1ubuntu2] (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [i386])
Inst libgphoto2-6 [2.5.3.1-1ubuntu2] (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [i386])
Inst libgudev-1.0-0 [1:204-5ubuntu20.2] (1:204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Inst libhud2 [13.10.1+14.04.20140402-0ubuntu1] (14.04+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst libwebkitgtk-1.0-common [2.4.2-1ubuntu0.1] (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst libwebkitgtk-1.0-0 [2.4.2-1ubuntu0.1] (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libjavascriptcoregtk-1.0-0 [2.4.2-1ubuntu0.1] (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst libwebkitgtk-3.0-common [2.4.2-1ubuntu0.1] (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst libwebkitgtk-3.0-0 [2.4.2-1ubuntu0.1] (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libjavascriptcoregtk-3.0-0 [2.4.2-1ubuntu0.1] (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst libspectre1 [0.2.7-2ubuntu1] (0.2.7-2ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libsystemd-journal0 [204-5ubuntu20.2] (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Inst initramfs-tools [0.103ubuntu4.1] (0.103ubuntu4.2 Ubuntu:14.04/trusty-updates [all]) []
Inst initramfs-tools-bin [0.103ubuntu4.1] (0.103ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Inst uuid-runtime [2.20.1-5.1ubuntu20] (2.20.1-5.1ubuntu20.1 Ubuntu:14.04/trusty-updates [i386])
Inst nepomuk-core-data [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Inst kate-data [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Inst libkactivities-bin [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst baloo [4:4.13.0-0ubuntu3] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst kde-runtime-data [4:4.13.0-0ubuntu1.1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all]) []
Inst nepomuk-core-runtime [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst kde-runtime [4:4.13.0-0ubuntu1.1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst katepart [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst kdelibs5-plugins [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst kdelibs-bin [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkjsembed4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkhtml5 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkjsapi4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libktexteditor4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkrossui4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkutils4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkprintutils4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkmediaplayer4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libplasma3 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkdewebkit5 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkde3support4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkparts4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libnepomukutils4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libnepomukquery4a [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libknotifyconfig4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libknewstuff3-4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkfile4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkemoticons4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst kdoctools [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkio5 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libnepomuk4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkrosscore4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libsolid4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkidletime4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkdesu5 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkpty4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkdnssd4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkdeclarative5 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkcmutils4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkdeui5 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libthreadweaver4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkatepartinterfaces4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkntlm4 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst kdelibs5-data [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [all]) []
Inst libkdecore5 [4:4.13.1-0ubuntu0.2] (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libbaloocore4 [4:4.13.0-0ubuntu3] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libbalooxapian4 [4:4.13.0-0ubuntu3] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libbaloofiles4 [4:4.13.0-0ubuntu3] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libnepomukcleaner4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libnepomukcore4abi1 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkactivities-models1 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkactivities6 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkblog4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkxmlrpcclient4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libsyndication4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libakonadi-kcal4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libmicroblog4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libktnef4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libakonadi-calendar4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkcalutils4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkpimidentities4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libkalarmcal2:i386 ]
Inst libkalarmcal2 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkholidays4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libakonadi-contact4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkcalcore4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkmbox4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkcal4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkabc4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst kdepimlibs-kio-plugins [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkldap4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkimap4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libakonadi-notes4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libmailtransport4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libakonadi-kmime4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkpimutils4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkpimtextedit4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkmime4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkresources4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libakonadi-socialutils4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libakonadi-kde4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkfilemetadata4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst plasma-scriptengine-javascript [4:4.13.0-0ubuntu1.1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst libkonq5-templates [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Inst libkonq-common [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst libkonq5abi1 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst ark [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst kmail [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libtemplateparser4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst libmessageviewer4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst libmessagelist4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst libmessagecore4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libkdepim4:i386 libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst libksieveui4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libkdepim4:i386 libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst blogilo [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libkdepim4:i386 libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst libpimcommon4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libkdepim4:i386 libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst libmailimporter4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libkdepim4:i386 libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst libincidenceeditorsng4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libkdepim4:i386 libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst libkdepim4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libmessagecomposer4:i386 libmailcommon4:i386 ]
Inst libmailcommon4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [libmessagecomposer4:i386 ]
Inst libmessagecomposer4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libsendlater4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libcalendarsupport4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkdepimdbusinterfaces4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkdgantt2-0 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libqgpgme1 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libgpgme++2 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkpgp4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libbaloopim4 [4:4.13.0-0ubuntu3] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkleo4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libksieve4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkmanagesieve4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkontactinterface4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libakonadi-kabc4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst kdepim-runtime [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libcomposereditorng4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst network-manager-gnome [0.9.8.8-0ubuntu4.1] (0.9.8.8-0ubuntu4.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libnm-gtk0 [0.9.8.8-0ubuntu4.1] (0.9.8.8-0ubuntu4.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libnm-gtk-common [0.9.8.8-0ubuntu4.1] (0.9.8.8-0ubuntu4.2 Ubuntu:14.04/trusty-updates [all])
Inst libunity-control-center1 [14.04.3+14.04.20140410-0ubuntu1] (14.04.3+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst nautilus-data [1:3.10.1-0ubuntu9] (1:3.10.1-0ubuntu9.2 Ubuntu:14.04/trusty-updates [all])
Inst gnome-settings-daemon-schemas [3.8.6.1-0ubuntu11.1] (3.8.6.1-0ubuntu11.2 Ubuntu:14.04/trusty-updates [all]) [gnome-settings-daemon:i386 ]
Inst gnome-settings-daemon [3.8.6.1-0ubuntu11.1] (3.8.6.1-0ubuntu11.2 Ubuntu:14.04/trusty-updates [i386])
Inst unity-settings-daemon [14.04.0+14.04.20140414-0ubuntu1] (14.04.0+14.04.20140606-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst unity-control-center [14.04.3+14.04.20140410-0ubuntu1] (14.04.3+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst libcompizconfig0 [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386]) []
Inst compiz-plugins [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386]) []
Inst compiz-gnome [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386]) []
Inst compiz-plugins-default [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libdecoration0 [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386]) []
Inst compiz-core [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst compiz [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst cups-browsed [1.0.52-0ubuntu1.1] (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst cups-filters-core-drivers [1.0.52-0ubuntu1.1] (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst cups-filters [1.0.52-0ubuntu1.1] (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst libkonqsidebarplugin4a [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst kde-baseapps-data [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all]) [kde-baseapps-bin:i386 konqueror:i386 ]
Inst konqueror [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) [kde-baseapps-bin:i386 ]
Inst kde-baseapps-bin [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst dolphin [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst evince [3.10.3-0ubuntu10] (3.10.3-0ubuntu10.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libevdocument3-4 [3.10.3-0ubuntu10] (3.10.3-0ubuntu10.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libevview3-3 [3.10.3-0ubuntu10] (3.10.3-0ubuntu10.1 Ubuntu:14.04/trusty-updates [i386])
Inst libnautilus-extension1a [1:3.10.1-0ubuntu9] (1:3.10.1-0ubuntu9.2 Ubuntu:14.04/trusty-updates [i386])
Inst evince-common [3.10.3-0ubuntu10] (3.10.3-0ubuntu10.1 Ubuntu:14.04/trusty-updates [all])
Inst ffmpegthumbs [4:4.13.0-0ubuntu1] (4:4.13.1-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst fontconfig [2.11.0-0ubuntu4] (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [i386])
Inst gir1.2-gudev-1.0 [1:204-5ubuntu20.2] (1:204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Inst gir1.2-webkit-3.0 [2.4.2-1ubuntu0.1] (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386]) []
Inst gir1.2-javascriptcoregtk-3.0 [2.4.2-1ubuntu0.1] (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst gir1.2-nmgtk-1.0 [0.9.8.8-0ubuntu4.1] (0.9.8.8-0ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Inst gnome-sudoku [1:3.10.2-0ubuntu2] (1:3.10.2-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Inst printer-driver-postscript-hp [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [all]) []
Inst printer-driver-hpijs [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libsane-hpaio [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386]) [hplip:i386 ]
Inst hplip [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libhpmud0 [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst hplip-data [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [all]) []
Inst printer-driver-hpcups [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386])
Inst hud [13.10.1+14.04.20140402-0ubuntu1] (14.04+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst intel-gpu-tools [1.3-0ubuntu2] (1.3-0ubuntu2.1 Ubuntu:14.04/trusty-updates [i386])
Inst juk [4:4.13.0-0ubuntu1] (4:4.13.1-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst kde-config-pimactivity [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libpimactivity4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst kdebase-bin [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Inst kdebase-runtime [4:4.13.0-0ubuntu1.1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Inst kfind [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst konqueror-nsplugins [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst marble-plugins [4:4.13.0-0ubuntu1.1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst marble-data [4:4.13.0-0ubuntu1.1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all]) []
Inst libmarblewidget18 [4:4.13.0-0ubuntu1.1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libastro1 [4:4.13.0-0ubuntu1.1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst libgphoto2-l10n [2.5.3.1-1ubuntu2] (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [all])
Inst libgtk-3-bin [3.10.8-0ubuntu1] (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libkcompactdisc4 [4:4.13.0-0ubuntu1] (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst libkcddb4 [4:4.13.0-0ubuntu1] (4:4.13.1-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst libkworkspace4abi2 [4:4.11.8-0ubuntu6] (4:4.11.10-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst libtar0 [1.2.20-3] (1.2.20-3ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst unity [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libunity-core-6.0-9 [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [i386]) []
Inst unity-services [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst libunity-2d-private0 [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst whoopsie [0.2.24.5] (0.2.24.6 Ubuntu:14.04/trusty-updates [i386]) []
Inst libwhoopsie0 [0.2.24.5] (0.2.24.6 Ubuntu:14.04/trusty-updates [i386])
Inst nautilus [1:3.10.1-0ubuntu9] (1:3.10.1-0ubuntu9.2 Ubuntu:14.04/trusty-updates [i386])
Inst shotwell-common [0.18.0-0ubuntu4] (0.18.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [all]) [shotwell:i386 ]
Inst shotwell [0.18.0-0ubuntu4] (0.18.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [i386])
Inst telepathy-gabble [0.18.2-1] (0.18.3-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Inst xul-ext-ubufox [2.8-0ubuntu1] (2.9-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst ubufox [2.8-0ubuntu1] (2.9-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst unity-2d [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst unity-2d-common [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst unity-2d-panel [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst unity-2d-shell [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst unity-2d-spread [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst usb-creator-gtk [0.2.56] (0.2.56.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst usb-creator-common [0.2.56] (0.2.56.1 Ubuntu:14.04/trusty-updates [i386])
Inst compizconfig-backend-gconf [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst indicator-printers [0.1.7+14.04.20140313-0ubuntu1] (0.1.7+14.04.20140527-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst kolourpaint4 [4:4.13.0-0ubuntu1] (4:4.13.1-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf resolvconf (1.69ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libcgmanager0 (0.24-0ubuntu7 Ubuntu:14.04/trusty-updates [i386])
Conf libudev1 (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf udev (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf libsystemd-daemon0 (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf systemd-services (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf libpam-systemd (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf libsystemd-login0 (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf libboost-date-time1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Conf libboost-system1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Conf libboost-filesystem1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Conf libboost-program-options1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Conf libboost-regex1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Conf libboost-signals1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Conf libboost-thread1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Conf libcupsfilters1 (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf libdbusmenu-glib4 (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-dbusmenu-glib-0.4 (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libdbusmenu-gtk3-4 (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libdbusmenu-gtk4 (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-dbusmenu-gtk-0.4 (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf fontconfig-config (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [all])
Conf libfontconfig1 (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [i386])
Conf libfontconfig1-dev (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [i386])
Conf libfontembed1 (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf libgtk-3-common (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libgtk-3-0 (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-gtk-3.0 (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libgtk-3-dev (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libgail-3-0 (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libgphoto2-port10 (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [i386])
Conf libgphoto2-6 (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [i386])
Conf libgudev-1.0-0 (1:204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf libhud2 (14.04+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libwebkitgtk-1.0-common (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf libjavascriptcoregtk-1.0-0 (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libwebkitgtk-1.0-0 (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libwebkitgtk-3.0-common (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf libjavascriptcoregtk-3.0-0 (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libwebkitgtk-3.0-0 (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libspectre1 (0.2.7-2ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libsystemd-journal0 (204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf initramfs-tools-bin (0.103ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Conf initramfs-tools (0.103ubuntu4.2 Ubuntu:14.04/trusty-updates [all])
Conf uuid-runtime (2.20.1-5.1ubuntu20.1 Ubuntu:14.04/trusty-updates [i386])
Conf nepomuk-core-data (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf kate-data (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf libkdecore5 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkdeui5 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libnepomuk4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libsolid4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkio5 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libnepomukcore4abi1 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkactivities-models1 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkactivities6 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkcmutils4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkdeclarative5 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libnepomukquery4a (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libnepomukutils4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkparts4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkdewebkit5 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkdnssd4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libknewstuff3-4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libthreadweaver4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libplasma3 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkactivities-bin (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libakonadi-kde4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkmime4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libakonadi-kmime4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libbaloocore4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libbalooxapian4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libbaloofiles4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkldap4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkresources4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkabc4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkcalcore4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkfilemetadata4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkidletime4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkemoticons4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkpimutils4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf baloo (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kde-runtime-data (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf libnepomukcleaner4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf nepomuk-core-runtime (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkpty4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkdesu5 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkfile4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkjsapi4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libktexteditor4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkhtml5 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkmediaplayer4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libknotifyconfig4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkxmlrpcclient4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkde3support4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkjsembed4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkntlm4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkrosscore4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf kdelibs5-data (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [all])
Conf kdoctools (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf kdelibs-bin (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkatepartinterfaces4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf katepart (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kdelibs5-plugins (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf plasma-scriptengine-javascript (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kde-runtime (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkrossui4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkprintutils4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkutils4 (4:4.13.2a-0ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkcal4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libsyndication4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkblog4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libakonadi-kcal4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmicroblog4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkpimtextedit4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkpimidentities4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkcalutils4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libktnef4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libakonadi-contact4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmailtransport4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libakonadi-calendar4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkholidays4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkalarmcal2 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkmbox4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkimap4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kdepimlibs-kio-plugins (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libakonadi-notes4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libakonadi-socialutils4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkonq5-templates (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf libkonq-common (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkonq5abi1 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf ark (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libakonadi-kabc4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kdepim-runtime (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkdepimdbusinterfaces4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libcalendarsupport4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libgpgme++2 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libbaloopim4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libpimcommon4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmessagecore4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkdgantt2-0 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libincidenceeditorsng4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libqgpgme1 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkleo4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkpgp4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmessageviewer4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libsendlater4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libtemplateparser4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmessagecomposer4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmailcommon4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkdepim4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmailimporter4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkmanagesieve4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkontactinterface4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libksieve4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libksieveui4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmessagelist4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kmail (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libcomposereditorng4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf blogilo (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libnm-gtk-common (0.9.8.8-0ubuntu4.2 Ubuntu:14.04/trusty-updates [all])
Conf libnm-gtk0 (0.9.8.8-0ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Conf network-manager-gnome (0.9.8.8-0ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Conf libunity-control-center1 (14.04.3+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf nautilus-data (1:3.10.1-0ubuntu9.2 Ubuntu:14.04/trusty-updates [all])
Conf gnome-settings-daemon-schemas (3.8.6.1-0ubuntu11.2 Ubuntu:14.04/trusty-updates [all])
Conf gnome-settings-daemon (3.8.6.1-0ubuntu11.2 Ubuntu:14.04/trusty-updates [i386])
Conf unity-settings-daemon (14.04.0+14.04.20140606-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf unity-control-center (14.04.3+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf compiz-core (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libcompizconfig0 (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libdecoration0 (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf compiz-plugins-default (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf compiz-plugins (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf compiz-gnome (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf compiz (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf cups-browsed (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf cups-filters-core-drivers (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf cups-filters (1.0.52-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkonqsidebarplugin4a (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kde-baseapps-data (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf kde-baseapps-bin (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf konqueror (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf dolphin (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libevdocument3-4 (3.10.3-0ubuntu10.1 Ubuntu:14.04/trusty-updates [i386])
Conf libevview3-3 (3.10.3-0ubuntu10.1 Ubuntu:14.04/trusty-updates [i386])
Conf libnautilus-extension1a (1:3.10.1-0ubuntu9.2 Ubuntu:14.04/trusty-updates [i386])
Conf evince-common (3.10.3-0ubuntu10.1 Ubuntu:14.04/trusty-updates [all])
Conf evince (3.10.3-0ubuntu10.1 Ubuntu:14.04/trusty-updates [i386])
Conf ffmpegthumbs (4:4.13.1-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf fontconfig (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-gudev-1.0 (1:204-5ubuntu20.3 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-javascriptcoregtk-3.0 (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-webkit-3.0 (2.4.3-1ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-nmgtk-1.0 (0.9.8.8-0ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Conf gnome-sudoku (1:3.10.2-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Conf libhpmud0 (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386])
Conf libsane-hpaio (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386])
Conf hplip-data (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [all])
Conf printer-driver-hpcups (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386])
Conf hplip (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386])
Conf printer-driver-postscript-hp (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [all])
Conf printer-driver-hpijs (3.14.3-0ubuntu3.2 Ubuntu:14.04/trusty-updates [i386])
Conf hud (14.04+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf intel-gpu-tools (1.3-0ubuntu2.1 Ubuntu:14.04/trusty-updates [i386])
Conf juk (4:4.13.1-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libpimactivity4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kde-config-pimactivity (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf kdebase-bin (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf kdebase-runtime (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf kfind (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf konqueror-nsplugins (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf marble-data (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf libastro1 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libmarblewidget18 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf marble-plugins (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libgphoto2-l10n (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [all])
Conf libgtk-3-bin (3.10.8-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkcompactdisc4 (4:4.13.2-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkcddb4 (4:4.13.1-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkworkspace4abi2 (4:4.11.10-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf libtar0 (1.2.20-3ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf unity-services (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libunity-core-6.0-9 (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf unity (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libunity-2d-private0 (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf libwhoopsie0 (0.2.24.6 Ubuntu:14.04/trusty-updates [i386])
Conf whoopsie (0.2.24.6 Ubuntu:14.04/trusty-updates [i386])
Conf nautilus (1:3.10.1-0ubuntu9.2 Ubuntu:14.04/trusty-updates [i386])
Conf shotwell-common (0.18.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [all])
Conf shotwell (0.18.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [i386])
Conf telepathy-gabble (0.18.3-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
Conf xul-ext-ubufox (2.9-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf ubufox (2.9-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf unity-2d (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf unity-2d-common (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf unity-2d-panel (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf unity-2d-shell (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf unity-2d-spread (7.2.1+14.04.20140513-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf usb-creator-common (0.2.56.1 Ubuntu:14.04/trusty-updates [i386])
Conf usb-creator-gtk (0.2.56.1 Ubuntu:14.04/trusty-updates [i386])
Conf compizconfig-backend-gconf (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf indicator-printers (0.1.7+14.04.20140527-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf kolourpaint4 (4:4.13.1-0ubuntu0.1 Ubuntu:14.04/trusty-updates [i386])
```

---

### Post by lisati on 2014-07-03
> **slickymaster said:**
> @drprinsloo
I edit your last post, adding code tags to it. Output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers, like coffeecat previously said.

^^^This

@drprinsloo
I added code tags to your reply.

---

### Post by deadflowr on 2014-07-03
> **drprinsloo said:**
> I just tried to run "Updater" and I get the message as shown in the attached thumbnail.
What do I do?

I usually accept it(the option of partial upgrade), initially.
The thing that happens with it is that it will run a setup similar to what happens when running the release upgrade through the update manager.
It will first open a window with a few items listed like retrieving packages, or something like that.
But ignore that window.
The window to look at is the one that will appear that tells you how much is going to be downloaded.
It is in that window that a dropdown arrow will appear next to the line Details.
Click on that dropdown, and review what is happening.
It will listed the packages that will be Installed, Removed, and Upgraded.
You can compare the three to see if something is odd, and it is at this stage that you can simply, still, cancel the whole process with no harm to the system.(There should be a cancel button right next to the Ok, or Install button.)

---

### Post by coffeecat on 2014-07-03
I'm seeing no problems with the output of apt-get upgrade. However, dist-upgrade rather than just upgrade is more likely to reproduce what you see with the Software Updater. I suggest you run this in the terminal:

```
sudo apt-get upgrade
```

That is, without the -s simulate option, and let it upgrade your system as far as apt-get upgrade can. Once that process is finished, try:

```
sudo apt-get dist-upgrade
```

That **won't** upgrade your system to the next release, contrary to the misunderstanding that is often posted here. Dist-upgrade simply has a more intelligent dependency handling than upgrade and will also install new kernels if they are on offer. I don't see anything in your output that would be installed with dist-upgrade that isn't by upgrade but it would be worth checking. If you get no errors with apt-get dist-upgtade, then Software Updater *should* work fine next time.

---

