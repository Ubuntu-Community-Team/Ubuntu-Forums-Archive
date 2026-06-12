---
title: "APT-GET add recommended packages"
date: 2013-03-06
forum: Installation &amp; Upgrades
---

### Post by m666 on 2013-03-06
I installed lubuntu:

sudo apt-get install ubuntu-desktop --no-install-recommends

but then I changed my mind: I want recommended packages to be installed too!
whats the command?

---

### Post by sisco311 on 2013-03-06
Did you try to run the same command without the --no-install-recommends option?

---

### Post by m666 on 2013-03-06
yes but it's 'too late':

'lubuntu-desktop is already installed'

---

### Post by m666 on 2013-03-06
Do I have to install them manually???

$ apt-cache show ubuntu-desktop


Recommends: acpi-support, activity-log-manager-control-center, aisleriot, app-install-data-partner, apport-gtk, avahi-autoipd, avahi-daemon, bluez, bluez-alsa, bluez-cups, bluez-gstreamer, branding-ubuntu, brasero, brltty, cups, cups-bsd, cups-client, deja-dup, empathy, example-content, firefox, firefox-gnome-support, fonts-kacst-one, fonts-khmeros-core, fonts-lao, fonts-liberation, fonts-lklug-sinhala, fonts-nanum, fonts-sil-abyssinica, fonts-sil-padauk, fonts-takao-pgothic, fonts-thai-tlwg, fonts-tibetan-machine, gcc, gnome-accessibility-themes, gnome-bluetooth, gnome-disk-utility, gnome-mahjongg, gnome-orca, gnome-screensaver, gnome-sudoku, gnomine, gvfs-fuse, gwibber, hplip, ibus, ibus-gtk3, ibus-pinyin, ibus-pinyin-db-android, ibus-table, im-switch, kerneloops-daemon, landscape-client-ui-install, laptop-detect, libgail-common, libnss-mdns, libpam-gnome-keyring, libproxy1-plugin-gsettings, libproxy1-plugin-networkmanager, libqt4-sql-sqlite, libreoffice-calc, libreoffice-gnome, libreoffice-help-en-us, libreoffice-impress, libreoffice-math, libreoffice-ogltrans, libreoffice-pdfimport, libreoffice-presentation-minimizer, libreoffice-presenter-console, libreoffice-style-human, libreoffice-writer, libwmf0.2-7-gtk, linux-headers-generic-pae, make, mousetweaks, nautilus-share, network-manager-gnome, network-manager-pptp, network-manager-pptp-gnome, onboard, overlay-scrollbar, pcmciautils, plymouth-theme-ubuntu-logo, policykit-desktop-privileges, printer-driver-c2esp, printer-driver-foo2zjs, printer-driver-min12xxw, printer-driver-ptouch, printer-driver-pxljr, printer-driver-sag-gdi, printer-driver-splix, pulseaudio-module-bluetooth, pulseaudio-module-gconf, pulseaudio-module-x11, python3-aptdaemon.pkcompat, qt-at-spi, remmina, rhythmbox, rhythmbox-plugin-magnatune, rhythmbox-ubuntuone, shotwell, simple-scan, sni-qt, speech-dispatcher, telepathy-idle, thunderbird, thunderbird-gnome-support, totem, totem-mozilla, transmission-gtk, ttf-indic-fonts-core, ttf-punjabi-fonts, ttf-ubuntu-font-family, ttf-wqy-microhei, ubuntu-docs, ubuntuone-client-gnome, ubuntuone-control-panel-qt, unity-webapps-common, usb-creator-gtk, vino, whoopsie, xcursor-themes, xdg-utils, xul-ext-ubufox, xul-ext-unity

---

### Post by sisco311 on 2013-03-06
Well, ubuntu-desktop is just a metapackage. It does not contain actual software, it  just depends on other packages to be installed. So you can try to remove it (no other packages will be removed) and reinstall it.

---

### Post by m666 on 2013-03-06
Yes indeed.
I forgot that apt-get (unlike aptitude) does not 'autoremove' packages.
Cheers!

---

### Post by m666 on 2013-03-06
...unless you mess something up in

 /etc/apt/apt.conf.d/01autoremove

;)

---

