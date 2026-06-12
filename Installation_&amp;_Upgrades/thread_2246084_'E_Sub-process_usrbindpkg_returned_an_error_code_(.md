---
title: "'E: Sub-process /usr/bin/dpkg returned an error code (1)' when installing anything"
date: 2014-09-28
forum: Installation &amp; Upgrades
---

### Post by jimb0b360 on 2014-09-28
Don't mark this as a duplicate, as solutions posted in other threads have not worked in this case.
When I try to install software or run sudo apt-get upgrade, the same error message returns every time:

```
james@JimUbuntuTop:~$ sudo apt-get upgrade[sudo] password for james: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED
  linux-image-3.8.0-19-generic linux-image-extra-3.8.0-19-generic
The following packages have been kept back:
  account-plugin-aim account-plugin-facebook account-plugin-flickr
  account-plugin-google account-plugin-jabber account-plugin-salut
  account-plugin-twitter account-plugin-windows-live account-plugin-yahoo
  accountsservice activity-log-manager-control-center alsa-utils anacron
  apparmor appmenu-qt5 apport apport-gtk apt-clone apt-utils aptdaemon
  aptitude aptitude-common apturl apturl-common avahi-daemon bamfdaemon baobab
  bind9-host blt brasero brasero-cdrkit brasero-common brltty checkbox
  checkbox-qt chromium-browser chromium-browser-l10n colord compiz compiz-core
  compiz-gnome compiz-plugins-default cpp cpp-4.7 cups cups-browsed cups-bsd
  cups-client cups-daemon cups-filters dbus dconf-tools deja-dup dnsutils
  duplicity empathy empathy-common eog evince evince-common
  evolution-data-server evolution-data-server-common fakeroot file-roller
  firefox folks-common friends-dispatcher friends-facebook friends-twitter g++
  g++-4.7 gcc gcc-4.7 gcc-4.7-base gcr gdb gdebi gdebi-core gedit gedit-common
  gir1.2-dee-1.0 gir1.2-ebook-1.2 gir1.2-edataserver-1.2 gir1.2-gdata-0.0
  gir1.2-goa-1.0 gir1.2-gtk-3.0 gir1.2-gtksource-3.0
  gir1.2-javascriptcoregtk-3.0 gir1.2-packagekitglib-1.0 gir1.2-pango-1.0
  gir1.2-rb-3.0 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-unity-5.0
  gir1.2-webkit-3.0 gir1.2-wnck-3.0 gnome-calculator gnome-contacts
  gnome-control-center gnome-control-center-data gnome-disk-utility
  gnome-font-viewer gnome-keyring gnome-mines gnome-orca gnome-power-manager
  gnome-screensaver gnome-session gnome-session-bin gnome-session-common
  gnome-settings-daemon gnome-sudoku gnome-system-log gnome-system-monitor
  gnome-terminal gstreamer0.10-plugins-ugly gstreamer0.10-x
  gstreamer1.0-clutter gstreamer1.0-libav gstreamer1.0-plugins-bad
  gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly gstreamer1.0-x gucharmap
  guile-2.0-libs gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons
  gvfs-fuse gvfs-libs hplip hplip-data hud ibus ibus-gtk ibus-gtk3 ibus-pinyin
  ibus-table ifupdown indicator-application indicator-appmenu
  indicator-bluetooth indicator-datetime indicator-power indicator-printers
  indicator-session indicator-sound iproute iptables iputils-ping
  isc-dhcp-client isc-dhcp-common language-selector-common
  language-selector-gnome libaccount-plugin-1.0-0 libaccountsservice0
  libalgorithm-diff-xs-perl libaprutil1 libapt-pkg-perl libasound2 libav-tools
  libavdevice53 libbind9-90 libbrasero-media3-1 libcairo-perl libcdr-0.0-0
  libclone-perl libclutter-1.0-0 libclutter-gst-2.0-0 libclutter-gtk-1.0-0
  libcolord1 libcompizconfig0 libcups2 libcupscgi1 libcupsfilters1
  libcupsimage2 libcupsmime1 libcupsppdc1 libdbusmenu-gtk3-4 libdbusmenu-gtk4
  libdecoration0 libdee-1.0-4 libebook-1.2-14 libegl1-mesa
  libegl1-mesa-drivers libevdocument3-4 libevview3-3 libfile-fcntllock-perl
  libfolks-eds25 libfolks-telepathy25 libfolks25 libgail-3-0 libgail-common
  libgail18 libgbm1 libgcc-4.7-dev libgcc1 libgcr-3-1 libgdata13
  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libgles2-mesa libglib-perl
  libgnome-control-center1 libgnutls26 libgoa-1.0-common libgomp1 libgpgme11
  libgpod-common libgpod4 libgstreamer-plugins-bad1.0-0
  libgstreamer-plugins-good1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtkmm-3.0-1
  libgtksourceview-3.0-common libgucharmap-2-90-7 libhpmud0 libido3-0.1-0
  libio-pty-perl libisccc90 libisccfg90 libitm1 libjavascriptcoregtk-3.0-0
  libjson-glib-1.0-0 libjson0 liblocale-gettext-perl liblwres90
  libmailtools-perl libmetacity-private0a libmspub-0.0-0 libnet-dns-perl
  libnetfilter-conntrack3 libnm-gtk0 libnss3 libnss3-1d libnux-4.0-0
  libnux-4.0-common libopencv-core2.4 libopencv-highgui2.4
  libopencv-imgproc2.4 libopencv-video2.4 libpam-modules libpam-modules-bin
  libpango-perl libpango1.0-0 libpangomm-1.4-1 libpeas-1.0-0 libplymouth2
  libpolkit-backend-1-0 libpolkit-gobject-1-0 libpoppler-glib8 libppl-c4
  libpulse0 libpurple0 libpwquality1 libpython-stdlib libpython2.7
  libpython2.7-minimal libpython2.7-stdlib libpython3-stdlib libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-sqlite libqt4-svg
  libqt4-test libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libquadmath0
  libquvi7 librdf0 libreoffice-base-core libreoffice-calc libreoffice-common
  libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk
  libreoffice-help-en-gb libreoffice-help-en-us libreoffice-impress
  libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-math
  libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-style-human
  libreoffice-writer librsvg2-2 librsvg2-common libsane libsane-common
  libsane-hpaio libsasl2-2 libsignon-extension1 libsignon-plugins-common1
  libsmbclient libsnmp-base libsocket6-perl libstdc++6 libstdc++6-4.7-dev
  libsub-name-perl libsvn1 libswscale2 libtext-charwidth-perl
  libtext-iconv-perl libtotem0 libudev1 libunity-protocol-private0
  libunity-webapps0 libunity9 libuuid-perl libvisio-0.0-0 libvte-2.90-9
  libvte-2.90-common libwayland0 libwebkitgtk-3.0-0 libwnck-3-0 libwnck22
  libxfixes3 libxi6 lintian linux-generic linux-generic-pae
  linux-headers-generic linux-headers-generic-pae linux-image-generic
  lsb-release mcp-account-manager-uoa mercurial mercurial-common metacity
  metacity-common modemmanager mousetweaks nautilus nautilus-data
  nautilus-sendto nautilus-sendto-empathy network-manager
  network-manager-gnome notify-osd onboard openttd openttd-data
  overlay-scrollbar-gtk3 perl perl-base perl-modules plymouth plymouth-label
  pm-utils policykit-1 poppler-utils printer-driver-foo2zjs
  printer-driver-hpcups printer-driver-postscript-hp procps protobuf-compiler
  pulseaudio python python-crypto python-gtk2 python-ibus python-imaging
  python-imaging-compat python-minimal python-oauthlib python-protobuf
  python-reportlab python-smbc python-ubuntu-sso-client python2.7
  python2.7-minimal python3 python3-apport python3-apt python3-aptdaemon
  python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-brlapi
  python3-cairo python3-commandnotfound python3-crypto python3-dbus
  python3-defer python3-dirspec python3-distupgrade python3-gdbm python3-gi
  python3-gi-cairo python3-httplib2 python3-louis python3-lxml python3-minimal
  python3-oauthlib python3-oneconf python3-piston-mini-client
  python3-pkg-resources python3-problem-report python3-pyatspi python3-pyicu
  python3-six python3-software-properties python3-speechd python3-tk
  python3-uno python3-update-manager python3-virtkey python3-xdg python3-xkit
  qdbus qpdf qtchooser rhythmbox rhythmbox-data rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rsyslog samba-common
  samba-common-bin seahorse sessioninstaller shotwell signon-keyring-extension
  signon-plugin-oauth2 signon-plugin-password signon-ui signond smbclient
  software-properties-common software-properties-gtk speech-dispatcher
  subversion supertuxkart supertuxkart-data synaptic systemd-services tcl8.5
  thin-client-config-agent thunderbird thunderbird-gnome-support
  thunderbird-locale-en tk8.5 totem totem-common totem-mozilla totem-plugins
  transmission-common transmission-gtk ttf-dejavu-core ttf-wqy-microhei
  ubiquity ubiquity-frontend-debconf ubiquity-ubuntu-artwork ubuntu-desktop
  ubuntu-drivers-common ubuntu-minimal ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk ubuntu-restricted-addons ubuntu-sso-client
  ubuntu-sso-client-qt ubuntu-wallpapers udev udisks2 ufw unity unity-greeter
  unity-lens-applications unity-lens-files unity-lens-friends unity-lens-music
  unity-lens-photos unity-lens-video unity-scope-gdrive
  unity-scope-musicstores unity-scope-video-remote unity-services
  unity-webapps-service uno-libs3 update-manager update-manager-core
  update-notifier update-notifier-common upower upstart ure usb-creator-common
  usb-creator-gtk xdiagnose xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware zeitgeist-core
  zeitgeist-datahub zenity zenity-common
The following packages will be upgraded:
  libfftw3-double3 libfftw3-single3
2 to upgrade, 0 to newly install, 2 to remove and 543 not to upgrade.
4 not fully installed or removed.
Need to get 0 B/1,179 kB of archives.
After this operation, 123 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 176614 files and directories currently installed.)
Removing linux-image-extra-3.8.0-19-generic (3.8.0-19.30) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Syntax error: "(" unexpected
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.8.0-19-generic.postrm line 328.
dpkg: error processing package linux-image-extra-3.8.0-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.8.0-19-generic (3.8.0-19.30) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Syntax error: "(" unexpected
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.8.0-19-generic.postrm line 328.
dpkg: error processing package linux-image-3.8.0-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
[COLOR=#ff0000]Errors were encountered while processing:[/COLOR]
[COLOR=#ff0000] linux-image-extra-3.8.0-19-generic
 linux-image-3.8.0-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

```

---

### Post by Vladlenin5000 on 2014-09-28
```
[COLOR=#ff0000]4 not fully installed or removed.[/COLOR]
```

Try:
```
sudo apt-get install -f
```

It may or may not prompt you to run another command:
```
sudo dpkg --configure -a
```

---

### Post by jimb0b360 on 2014-09-28
First command:
```
james@JimUbuntuTop:~$ sudo apt-get install -f[sudo] password for james: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-image-3.8.0-19-generic linux-image-extra-3.8.0-19-generic
0 to upgrade, 0 to newly install, 2 to remove and 545 not to upgrade.
4 not fully installed or removed.
After this operation, 123 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 176614 files and directories currently installed.)
Removing linux-image-extra-3.8.0-19-generic (3.8.0-19.30) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Syntax error: "(" unexpected
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.8.0-19-generic.postrm line 328.
dpkg: error processing package linux-image-extra-3.8.0-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.8.0-19-generic (3.8.0-19.30) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Syntax error: "(" unexpected
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.8.0-19-generic.postrm line 328.
dpkg: error processing package linux-image-3.8.0-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.8.0-19-generic
 linux-image-3.8.0-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



``` had the same error.

Second command:
```
james@JimUbuntuTop:~$ sudo dpkg --configure -aSetting up memtest86+ (4.20-1.1ubuntu8) ...
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Syntax error: "(" unexpected
dpkg: error processing package memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up grub-pc (2.02~beta2-9ubuntu1) ...
/var/lib/dpkg/info/grub-pc.config: 6: /etc/default/grub: Syntax error: "(" unexpected
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 memtest86+
 grub-pc



``` has a different error...

---

### Post by Vladlenin5000 on 2014-09-28
I'm afraid you have a deeper & darker problem and is something to do with an old kernel that for some reason dpkg wants to remove but it can't. Later, this triggers an (kinda) expected error when updating grub. Expected because grub needs to enumerate all the booting possibilities, be them other OSs, the current Ubuntu kernel plus all the previous kernels. There's a problem with your *linux-image-3.8.0-19-generic*.

Other them attempting to remove the old kernels I'm out of ideas (and that may fail as well).

First of all note down the kernel version in use:
```
uname -a
```
(You want to remove everything except that one)

Then, the following command with the *--dry-run,* will show you what it'll going to remove without actually doing it. Make sure the version previously obtained ISN'T listed:
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e  `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)"  | xargs sudo apt-get --dry-run remove
```

If everything is OK, you can then proceed and actually run the command for real:
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e  `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)"  | xargs sudo apt-get -y purge
```

---

### Post by jimb0b360 on 2014-09-28
I get the same error whilst running that last command too.
```
james@JimUbuntuTop:~$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e  `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)"  | xargs sudo apt-get -y purgeReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-image-3.8.0-19-generic linux-image-extra-3.8.0-19-generic
0 to upgrade, 0 to newly install, 2 to remove and 545 not to upgrade.
4 not fully installed or removed.
After this operation, 123 MB disk space will be freed.
(Reading database ... 176614 files and directories currently installed.)
Removing linux-image-extra-3.8.0-19-generic (3.8.0-19.30) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Syntax error: "(" unexpected
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.8.0-19-generic.postrm line 328.
dpkg: error processing package linux-image-extra-3.8.0-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.8.0-19-generic (3.8.0-19.30) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Syntax error: "(" unexpected
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.8.0-19-generic.postrm line 328.
dpkg: error processing package linux-image-3.8.0-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.8.0-19-generic
 linux-image-3.8.0-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

