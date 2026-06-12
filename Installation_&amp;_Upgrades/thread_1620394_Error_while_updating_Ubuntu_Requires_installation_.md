---
title: "Error while updating Ubuntu Requires installation of untrusted packages"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by $uraj on 2010-11-13
alsa-utils app-install-data-partner aptdaemon compiz compiz-core compiz-gnome compiz-plugins cups cups-bsd cups-client cups-common cups-ppdc empathy empathy-common evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins firefox firefox-branding firefox-gnome-support gcalctool gconf-defaults-service gconf2 gconf2-common gdb gdm-guest-session gnome-settings-daemon gvfs gvfs-backends gvfs-fuse gwibber gwibber-service hpijs hplip hplip-cups hplip-data indicator-sound initscripts jockey-common jockey-gtk libasound2 libc-bin libc-dev-bin libc6 libc6-dev libcamel1.2-14 libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdecoration0 libdrm-intel1 libdrm-nouveau1 libdrm-radeon1 libdrm2 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7 libedataserver1.2-13 libedataserverui1.2-8 libegroupwise1.2-13 libevolution libfreetype6 libgconf2-4 libgdata-google1.2-1 libgdata1.2-1 libgpod-common libgpod4 libgudev-1.0-0 libgvfscommon0 libhpmud0 libldap-2.4-2 libnss3-1d libpam-modules libpam-runtime libpam0g libpoppler-glib5 libpoppler7 libpulse-browse0 libpulse-mainloop-glib0 libpulse0 libpurple-bin libpurple0 libsane-hpaio libudev0 libutouch-grail1 libvte-common libvte9 libwebkit-1.0-2 libwebkit-1.0-common libxml2 libxml2-utils linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic linux-image-2.6.35-22-generic linux-libc-dev nautilus-sendto-empathy pitivi poppler-utils pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python-aptdaemon python-aptdaemon-gtk python-cupshelpers python-libxml2 python-papyon python-vte rhythmbox-ubuntuone-music-store simple-scan software-center system-config-printer-common system-config-printer-gnome system-config-printer-udev sysv-rc sysvinit-utils tzdata ubufox ubuntu-sso-client udev update-manager update-manager-core xserver-xorg-video-intel xul-ext-ubufox xulrunner-1.9.2

---

### Post by sikander3786 on 2010-11-13
Go to Software Center > Edit > Software Sources and change the Update Server to Main.

Now goto Applications > Accessories > Terminal and try these commands.

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Please post the output of above mentioned commands. Wrap your text with proper code tags # using the post menu when you reply.

Thanks.

---

