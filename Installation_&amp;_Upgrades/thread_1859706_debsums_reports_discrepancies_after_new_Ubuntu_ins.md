---
title: "debsums reports discrepancies after new Ubuntu install with Wubi"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by robinhood2008 on 2011-10-14
After installing Ubuntu 11.10 "Oneiric Ocelot" inside a system running Windows Vista Home Basic 32-bit edition with Service Pack 2 using Wubi, I decided to follow the instructions in ZDNet's article, [How to lock down Linux]("http://www.zdnet.com/blog/open-source/how-to-lock-down-linux/9665?tag=nl.e550"). It told me to input the following commands in a terminal window:

```
dpkg -l \*|while read s n rest; do if [ "$s" == "ii" ]; then echo $n;
fi; done > ~/tmp.txt
for f in `cat ~/tmp.txt`; do debsums -s -a $f; done
```

When I first tried this, it told me the program 'debsums' wasn't installed, so I used the command 'sudo apt-get install debsums' to install this program, and re-ran the above commands. When debsums was finished, it generated this output:

```
debsums: can't open at file /etc/at.deny (Permission denied)
debsums: no md5sums for binutils
debsums: changed file /usr/share/doc/consolekit/changelog.Debian.gz (from consolekit package)
debsums: can't open fuse-utils file /etc/fuse.conf (Permission denied)
debsums: changed file /usr/share/doc/gir1.2-launchpad-integration-3.0/changelog.gz (from gir1.2-launchpad-integration-3.0 package)
debsums: changed file /usr/share/gnome/help/gnome-sound-recorder/uk/figures/grecord_window.png (from gnome-media package)
debsums: changed file /usr/share/gnome/help/gnome-system-monitor/eu/figures/addColumn.png (from gnome-system-monitor package)
debsums: no md5sums for libaudio2
debsums: changed file /usr/share/doc/libgtk-vnc-2.0-0/changelog.Debian.gz (from libgtk-vnc-2.0-0 package)
debsums: changed file /usr/share/doc/liblaunchpad-integration1.0-cil/changelog.gz (from liblaunchpad-integration1.0-cil package)
debsums: changed file /usr/share/doc/libpam-ck-connector/changelog.Debian.gz (from libpam-ck-connector package)
debsums: changed file /usr/share/doc/libpaper-utils/changelog.gz (from libpaper-utils package)
debsums: changed file /usr/share/doc/libxcb-dri2-0/changelog.Debian.gz (from libxcb-dri2-0 package)
debsums: changed file /usr/share/doc/libxcb-render0/changelog.Debian.gz (from libxcb-render0 package)
debsums: changed file /usr/share/doc/libxcb-shape0/changelog.Debian.gz (from libxcb-shape0 package)
debsums: changed file /usr/share/doc/libxcb-shm0/changelog.Debian.gz (from libxcb-shm0 package)
debsums: can't open linux-image-3.0.0-12-generic file /boot/System.map-3.0.0-12-generic (Permission denied)
debsums: can't open linux-image-3.0.0-12-generic file /boot/vmcoreinfo-3.0.0-12-generic (Permission denied)
debsums: no md5sums for netbase
debsums: changed file /usr/share/doc/perl/changelog.Debian.gz (from perl-base package)
debsums: can't open policykit-desktop-privileges file /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla (Permission denied)
debsums: can't open ppp file /etc/chatscripts/pap (Permission denied)
debsums: can't open ppp file /etc/chatscripts/gprs (Permission denied)
debsums: changed file /usr/share/doc/python-farsight/changelog.Debian.gz (from python-farsight package)
debsums: changed file /usr/share/glib-2.0/schemas/gschemas.compiled (from shotwell package)
debsums: changed file /usr/share/doc/speech-dispatcher/changelog.Debian.gz (from speech-dispatcher package)
debsums: can't open sudo file /etc/sudoers.d/README (Permission denied)
debsums: can't open sudo file /etc/sudoers (Permission denied)
debsums: changed file /usr/share/gnome/help/tomboy/es/figures/notebook-icon.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/es/figures/tomboy-pindown.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/es/figures/tomboy-pinup.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/es/figures/tomboy-tools.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/eu/figures/notebook-icon.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/eu/figures/tomboy-pindown.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/eu/figures/tomboy-pinup.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/eu/figures/tomboy-tools.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/it/figures/notebook-icon.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/it/figures/tomboy-pindown.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/it/figures/tomboy-pinup.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/it/figures/tomboy-tools.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/pl/figures/notebook-icon.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/pl/figures/tomboy-pindown.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/pl/figures/tomboy-pinup.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/sv/figures/notebook-icon.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/sv/figures/tomboy-pindown.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/sv/figures/tomboy-pinup.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/sv/figures/tomboy-tools.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/uk/figures/tomboy-pindown.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/uk/figures/tomboy-pinup.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/uk/figures/tomboy-tools.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/totem/pl/figures/totem_volume_maximum_button.png (from totem-common package)
debsums: changed file /usr/share/gnome/help/totem/pl/figures/totem_volume_mute_button.png (from totem-common package)
debsums: missing file /usr/bin/user-setup (from user-setup package)
debsums: missing file /usr/lib/user-setup/functions.sh (from user-setup package)
debsums: missing file /usr/lib/user-setup/reserved-usernames (from user-setup package)
debsums: missing file /usr/lib/user-setup/user-setup-apply (from user-setup package)
debsums: missing file /usr/lib/user-setup/user-setup-ask (from user-setup package)
debsums: missing file /usr/share/doc/user-setup/changelog.gz (from user-setup package)
debsums: missing file /usr/share/doc/user-setup/copyright (from user-setup package)
debsums: missing file /usr/share/lintian/overrides/user-setup (from user-setup package)
debsums: changed file /usr/share/doc/wireless-tools/changelog.Debian.gz (from wireless-tools package)
```

Surely this should not happen on a new Ubuntu installation out of the box! So what's the deal here?

Brandon Taylor

---

### Post by jaccall on 2011-11-02
Yes! I got this too!

Anybody???

TIA

---

