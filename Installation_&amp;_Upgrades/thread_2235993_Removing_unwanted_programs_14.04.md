---
title: "Removing unwanted programs 14.04"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2014-07-24
After installing 14.04, I wanted to remove all programs that I would not use to save disk space and to make room for third-party programs that are more effective than what Ubuntu offers.  Other than games, it seem everything is tied to ubuntu-desktop.  For example, I have absolutely no need for Document Viewer (evince).  I use Qoppa's Studio Pro 9.  When I tried to remove evince, I could not as it was tied to ubuntu-desktop.

How does one get rid of all these extra programs that I will never use?

John

---

### Post by deadflowr on 2014-07-24
Ubuntu-desktop is dependent on evince
Here's a list of what is dependent for the ubuntu-desktop
> Depends: alsa-base, alsa-utils, anacron, at-spi2-core, baobab, bc, ca-certificates, checkbox-gui, dmz-cursor-theme, doc-base, eog, evince, file-roller, fonts-dejavu-core, fonts-freefont-ttf, foomatic-db-compressed-ppds, gedit, genisoimage, ghostscript-x, gnome-calculator, gnome-font-viewer, gnome-menus, gnome-power-manager, gnome-screenshot, gnome-session-canberra, gnome-system-log, gnome-system-monitor, gstreamer0.10-alsa, gstreamer0.10-plugins-base-apps, gstreamer0.10-pulseaudio, gstreamer1.0-alsa, gstreamer1.0-plugins-base-apps, gstreamer1.0-pulseaudio, gucharmap, gvfs-bin, inputattach, language-selector-gnome, libatk-adaptor, libnotify-bin, libpam-systemd, libsasl2-modules, libxp6, lightdm, memtest86+, nautilus, nautilus-sendto, notify-osd, openprinting-ppds, printer-driver-pnm2ppa, pulseaudio, rfkill, seahorse, software-center, software-properties-gtk, ssh-askpass-gnome, system-config-printer-gnome, ubuntu-artwork, ubuntu-drivers-common, ubuntu-extras-keyring, ubuntu-release-upgrader-gtk, ubuntu-session, ubuntu-settings, ubuntu-sounds, ubuntu-sso-client-qt, unity, unity-control-center, unity-greeter, unity-settings-daemon, unzip, update-manager, update-notifier, wireless-tools, wpasupplicant, xdg-user-dirs, xdg-user-dirs-gtk, xdiagnose, xkb-data, xorg, yelp, zenity, zip

And here's a list of the recommended packages for ubuntu-desktop, which you *can* remove if you want
> Recommends:  acpi-support, activity-log-manager-control-center, aisleriot, app-install-data-partner, apport-gtk, avahi-autoipd, avahi-daemon, bluez, bluez-alsa, bluez-cups, branding-ubuntu, brasero, brltty, cheese, cups, cups-bsd, cups-client, cups-filters, deja-dup, empathy, example-content, firefox, fonts-droid, fonts-kacst-one, fonts-khmeros-core, fonts-lao, fonts-liberation, fonts-lklug-sinhala, fonts-nanum, fonts-sil-abyssinica, fonts-sil-padauk, fonts-takao-pgothic, fonts-thai-tlwg, fonts-tibetan-machine, gcc, gnome-accessibility-themes, gnome-bluetooth, gnome-disk-utility, gnome-mahjongg, gnome-orca, gnome-screensaver, gnome-sudoku, gnome-terminal, gnomine, gvfs-fuse, hplip, ibus, ibus-gtk3, ibus-pinyin, ibus-table, im-config, kerneloops-daemon, landscape-client-ui-install, laptop-detect, libgail-common, libnss-mdns, libpam-gnome-keyring, libproxy1-plugin-gsettings, libproxy1-plugin-networkmanager, libqt4-sql-sqlite, libreoffice-calc, libreoffice-gnome, libreoffice-impress, libreoffice-math, libreoffice-ogltrans, libreoffice-pdfimport, libreoffice-presentation-minimizer, libreoffice-style-human, libreoffice-writer, libwmf0.2-7-gtk, make, mousetweaks, nautilus-share, network-manager-gnome, network-manager-pptp, network-manager-pptp-gnome, onboard, overlay-scrollbar, pcmciautils, plymouth-theme-ubuntu-logo, policykit-desktop-privileges, printer-driver-c2esp, printer-driver-foo2zjs, printer-driver-min12xxw, printer-driver-ptouch, printer-driver-pxljr, printer-driver-sag-gdi, printer-driver-splix, pulseaudio-module-bluetooth, pulseaudio-module-x11, python3-aptdaemon.pkcompat, qt-at-spi, remmina, rhythmbox, rhythmbox-plugin-magnatune, shotwell, simple-scan, sni-qt, speech-dispatcher, telepathy-idle, thunderbird, thunderbird-gnome-support, totem, totem-mozilla, transmission-gtk, ttf-indic-fonts-core, ttf-punjabi-fonts, ttf-ubuntu-font-family, ubuntu-docs, unity-webapps-common, usb-creator-gtk, vino, whoopsie, xcursor-themes, xdg-utils, xterm, xul-ext-ubufox, xul-ext-unity, xul-ext-webaccounts



FWIW

---

### Post by Bucky Ball on 2014-07-24
I think we talked about this in another thread. Picking what you don't need from a full install is like needle in a haystack work, and prone to crashing and breaking your system.

As suggested previously (from memory) try a minimal install and work the other way. You add the software you want/need rather than the tedious, tightrope walking process of attempting to remove what you don't want.

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Good luck however you go, but installing a full desktop version then trying to pick the nits out of that is both problematic and risky. Working from the foundations up is a LOT easier than dismantling certain sections of a high-rise apartment block. Bit like the wood block game Jenga, where you remove the wooden bars until you remove the one that get the tower a-tumbling down. ;)

---

