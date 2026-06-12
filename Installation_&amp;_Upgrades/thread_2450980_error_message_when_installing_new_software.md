---
title: "error message when installing new software"
date: 2020-09-24
forum: Installation &amp; Upgrades
---

### Post by aveenhoff on 2020-09-24
[COLOR=#333333][FONT=Ubuntu]Hello,[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]When installing new software I get an error message as shown in the attachment. [/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Can anyone help me fix this? I tried to install Virtual Box but get the same error message when installing other software.[/FONT][/COLOR]
[ATTACH]287017[/ATTACH]
[COLOR=#333333][FONT=Ubuntu]
The problem seems to be in the Ubuntu software but I have no idea how to fix it. Is their a command line for this? 

Hope anyone can be of help. Thanks in advance.[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]Arnoldus[/FONT][/COLOR]

---

### Post by Impavidus on 2020-09-24
It's a bit inconvenient if you paste a screenshot in a libreoffice document, then attach that. You can attach the screenshot directly to your forum post. And in case of text from a terminal or file, you can paste it as text in your post. Use code tags in that case. If you quote my post in your reply, you can see how to use code tags.

Let's have a look at the status of your package management. Try```
sudo apt update
sudo apt upgrade
```Post the commands as you ran them and the complete output.

---

### Post by aveenhoff on 2020-09-24
```
arnold@arnold-Aspire-5542:~$ sudo apt update
[sudo] password for arnold: 
Hit:1 [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) bionic InRelease
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease                        
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]    
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]     
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed InRelease [242 kB]      
Hit:6 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy InRelease                      
Get:7 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease [6,259 B]      
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [9,296 B]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security/main Sources [168 kB]   
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security/main i386 Packages [544 kB]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security/main amd64 Packages [867 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [49.0 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security/universe amd64 Packages [706 kB]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security/universe i386 Packages [641 kB]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [55.9 kB]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/main amd64 Packages [93.7 kB]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/main i386 Packages [59.6 kB]
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/main Translation-en [32.6 kB]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/restricted amd64 Packages [31.9 kB]
Get:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/restricted Translation-en [8,376 B]
Get:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/universe i386 Packages [10.4 kB]
Get:23 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/universe amd64 Packages [18.1 kB]
Get:24 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/universe Translation-en [10.9 kB]
Err:7 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease                
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F

```


The upgrade is still running ...

---

### Post by aveenhoff on 2020-09-24
```
arnold@arnold-Aspire-5542:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  icedtea-netx-common libclamav7 libllvm6.0
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  systemd-shim
The following NEW packages will be installed:
  bubblewrap fwupd-signed gstreamer1.0-gtk3 libclamav9 libllvm9 librhino-java
  libtagsoup-java libwayland-egl1 libxmlb1 linux-headers-4.15.0-119
  linux-headers-4.15.0-119-generic linux-image-4.15.0-119-generic
  linux-modules-4.15.0-119-generic linux-modules-extra-4.15.0-119-generic
  python3-dateutil
The following packages will be upgraded:
  amd64-microcode apache2-bin apport apport-gtk apt apt-transport-https
  apt-utils aptdaemon aptdaemon-data aspell avahi-autoipd avahi-daemon
  avahi-utils bind9-host binutils binutils-common binutils-x86-64-linux-gnu
  bluez bluez-cups bluez-obexd bsdutils busybox-initramfs busybox-static bzip2
  ca-certificates chromium-codecs-ffmpeg-extra clamav clamav-base
  clamav-freshclam cpio cpp cpp-7 cups cups-browsed cups-bsd cups-client
  cups-common cups-core-drivers cups-daemon cups-filters
  cups-filters-core-drivers cups-ipp-utils cups-ppdc cups-server-common curl
  dbus dbus-user-session dbus-x11 default-jre default-jre-headless dirmngr
  distro-info-data djvulibre-bin dnsutils e2fslibs e2fsprogs e2fsprogs-l10n
  evince evince-common evolution-data-server evolution-data-server-common
  fdisk ffmpeg file file-roller firefox fonts-opensymbol freerdp-x11 fwupd gcc
  gcc-7 gcc-7-base gcc-8-base gcc-8-base:i386 gdm3 gettext gettext-base
  ghostscript ghostscript-x gir1.2-camel-1.2 gir1.2-ebook-1.2
  gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gir1.2-gdm-1.0
  gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0
  gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-ibus-1.0
  gir1.2-javascriptcoregtk-4.0 gir1.2-networkmanager-1.0 gir1.2-nm-1.0
  gir1.2-polkit-1.0 gir1.2-rsvg-2.0 gir1.2-snapd-1 gir1.2-soup-2.4
  gir1.2-webkit2-4.0 glib-networking glib-networking-common
  glib-networking-services gnome-bluetooth gnome-desktop3-data gnome-shell
  gnome-shell-common gnupg gnupg-agent gnupg-l10n gnupg-utils gnupg2 gpg
  gpg-agent gpg-wks-client gpg-wks-server gpgconf gpgsm gpgv grub-common
  grub-pc grub-pc-bin grub2-common gstreamer1.0-alsa gstreamer1.0-gl
  gstreamer1.0-plugins-base gstreamer1.0-plugins-base-apps gstreamer1.0-tools
  gstreamer1.0-x gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons
  gvfs-fuse gvfs-libs ibus ibus-gtk ibus-gtk3 icedtea-8-plugin icedtea-netx
  icedtea-netx-common icedtea-plugin imagemagick imagemagick-6-common
  imagemagick-6.q16 initramfs-tools initramfs-tools-bin initramfs-tools-core
  intel-microcode iproute2 isc-dhcp-client isc-dhcp-common java-common
  kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools krb5-locales
  language-pack-en language-pack-gnome-en language-pack-gnome-nl
  language-pack-nl libapt-inst2.0 libapt-pkg5.0 libarchive13 libasan4
  libaspell15 libasprintf-dev libasprintf0v5 libatomic1 libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core7 libavahi-glib1
  libavahi-gobject0 libavahi-ui-gtk3-0 libavcodec57 libavdevice57 libavfilter6
  libavformat57 libavresample3 libavutil55 libbind9-160 libbinutils libblkid1
  libblkid1:i386 libbluetooth3 libbsd0 libbsd0:i386 libbz2-1.0 libbz2-1.0:i386
  libc-bin libc-dev-bin libc6 libc6:i386 libc6-dbg libc6-dev libcaca0
  libcamel-1.2-61 libcc1-0 libcephfs2 libcilkrts5 libclamav7 libcom-err2
  libcom-err2:i386 libcomerr2 libcups2 libcupscgi1 libcupsfilters1
  libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3-gnutls libcurl4 libdb5.3
  libdb5.3:i386 libdbus-1-3 libdbus-1-dev libdjvulibre-text libdjvulibre21
  libdns-export1100 libdns1100 libdrm-amdgpu1 libdrm-common libdrm-intel1
  libdrm-nouveau2 libdrm-radeon1 libdrm2 libdw1 libebackend-1.2-10 libebml-dev
  libebml4v5 libebook-1.2-19 libebook-contacts-1.2-2 libecal-1.2-19
  libedata-book-1.2-25 libedata-cal-1.2-28 libedataserver-1.2-23
  libedataserverui-1.2-2 libegl-mesa0 libegl1-mesa libelf1 libevdocument3-4
  libevview3-3 libexif12 libexiv2-14 libexpat1 libext2fs2 libfdisk1
  libfontembed1 libfreerdp-cache1.1 libfreerdp-client1.1 libfreerdp-client2-2
  libfreerdp-codec1.1 libfreerdp-common1.1.0 libfreerdp-core1.1
  libfreerdp-crypto1.1 libfreerdp-gdi1.1 libfreerdp-locale1.1
  libfreerdp-plugins-standard libfreerdp-primitives1.1 libfreerdp-rail1.1
  libfreerdp-utils1.1 libfreerdp2-2 libfwupd2 libgbm1 libgcc-7-dev libgcc1
  libgcc1:i386 libgcrypt20 libgcrypt20:i386 libgd3 libgdm1 libgettextpo-dev
  libgettextpo0 libgfortran4 libgif7 libgl1-mesa-dri libgl1-mesa-glx
  libglapi-mesa libgles2-mesa libglib2.0-0 libglib2.0-0:i386 libglib2.0-bin
  libglib2.0-data libglx-mesa0 libgnome-bluetooth13 libgnome-desktop-3-17
  libgnutls-openssl27 libgnutls30 libgomp1 libgpgme11 libgpgmepp6
  libgraphicsmagick++-q16-12 libgraphicsmagick-q16-3 libgs9 libgs9-common
  libgssapi-krb5-2 libgstreamer-gl1.0-0 libgstreamer-plugins-base1.0-0
  libgstreamer1.0-0 libibus-1.0-5 libicu60 libidn2-0 libimage-magick-perl
  libimage-magick-q16-perl libio-socket-ssl-perl libirs160 libisc-export169
  libisc169 libisccc160 libisccfg160 libitm1 libjavascriptcoregtk-4.0-18
  libjpeg-turbo8 libjson-c3 libk5crypto3 libkcmutils4 libkde3support4
  libkdeclarative5 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4
  libkemoticons4 libkf5config-bin libkf5config-data libkf5configcore5
  libkf5configgui5 libkfile4 libkhtml5 libkio5 libkjsapi4 libkjsembed4
  libkmediaplayer4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4
  libkpty4 libkrb5-3 libkrb5support0 libkrosscore4 libktexteditor4
  libldap-2.4-2 libldap-common libldb1 liblsan0 liblua5.3-0 liblwres160
  libmagic-mgc libmagic1 libmagick++-6.q16-7 libmagickcore-6.q16-3
  libmagickcore-6.q16-3-extra libmagickwand-6.q16-3 libmount1 libmount1:i386
  libmpx2 libmspack0 libmysofa0 libmysqlclient20 libnb-org-openide-util-java
  libnb-org-openide-util-lookup-java libnet-ssleay-perl libnm-glib-vpn1
  libnm-glib4 libnm-util2 libnm0 libnss-myhostname libnss-systemd
  libnss-winbind libnss3 libntfs-3g88 libopenexr22 libopenjp2-7 libpam-systemd
  libpam-winbind libparted-fs-resize0 libparted2 libpcap0.8 libperl5.26
  libplasma3 libpng16-16 libpolkit-agent-1-0 libpolkit-backend-1-0
  libpolkit-gobject-1-0 libpoppler-glib8 libpoppler-qt5-1 libpoppler73
  libpostproc54 libpq5 libproxy-tools libproxy1-plugin-gsettings
  libproxy1-plugin-networkmanager libproxy1v5 libpulse-mainloop-glib0
  libpulse0 libpulsedsp libpython2.7 libpython2.7-minimal libpython2.7-stdlib
  libpython3.6 libpython3.6-minimal libpython3.6-stdlib libqt5concurrent5
  libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5
  libqt5printsupport5 libqt5sql5 libqt5sql5-sqlite libqt5test5 libqt5widgets5
  libqt5xml5 libquadmath0 librados2 libraw16
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk libreoffice-gtk2 libreoffice-gtk3 libreoffice-help-en-us
  libreoffice-help-nl libreoffice-impress libreoffice-l10n-nl libreoffice-math
  libreoffice-ogltrans libreoffice-pdfimport libreoffice-style-breeze
  libreoffice-style-galaxy libreoffice-style-human libreoffice-style-tango
  libreoffice-writer librsvg2-2 librsvg2-common libruby2.5 libsane-common
  libsane1 libsasl2-2 libsasl2-modules libsasl2-modules-db libsdl-image1.2
  libsdl1.2debian libsdl2-2.0-0 libseccomp2 libsmartcols1 libsmbclient
  libsnapd-glib1 libsndfile1 libsnmp-base libsnmp30 libsolid4
  libsoup-gnome2.4-1 libsoup2.4-1 libsqlite3-0 libss2 libssh-4 libssh-gcrypt-4
  libssl1.0.0 libssl1.1 libstdc++6 libstdc++6:i386 libswresample2 libswscale4
  libsystemd0 libsystemd0:i386 libthreadweaver4 libtiff-tools libtiff5
  libtsan0 libu2f-udev libubsan0 libudev1 libudev1:i386 libuuid1 libuuid1:i386
  libvlc-bin libvlc5 libvlccore9 libvncclient1 libvpx5 libwavpack1
  libwayland-client0 libwayland-cursor0 libwayland-egl1-mesa
  libwayland-server0 libwbclient0 libwebkit2gtk-4.0-37
  libwebkit2gtk-4.0-37-gtk2 libwhoopsie0 libwinpr-crt0.1 libwinpr-dsparse0.1
  libwinpr-environment0.1 libwinpr-file0.1 libwinpr-handle0.1 libwinpr-heap0.1
  libwinpr-input0.1 libwinpr-interlocked0.1 libwinpr-library0.1
  libwinpr-path0.1 libwinpr-pool0.1 libwinpr-registry0.1 libwinpr-rpc0.1
  libwinpr-sspi0.1 libwinpr-synch0.1 libwinpr-sysinfo0.1 libwinpr-thread0.1
  libwinpr-utils0.1 libwinpr2-2 libwww-perl libx11-6 libx11-6:i386 libx11-data
  libx11-xcb1 libxatracker2 libxfreerdp-client1.1 libxkbcommon-x11-0
  libxkbcommon0 libxml2 libxml2-utils libxslt1.1 libzmq5 libzstd1 linux-base
  linux-firmware linux-generic linux-headers-generic linux-image-generic
  linux-libc-dev locales login mesa-va-drivers mesa-vdpau-drivers mount
  multiarch-support netplan.io network-manager
  network-manager-config-connectivity-ubuntu nplan ntfs-3g openjdk-11-jre
  openjdk-11-jre-headless openjdk-8-jre openjdk-8-jre-headless openssh-client
  openssl parted passwd patch perl perl-base perl-modules-5.26 policykit-1
  policykit-desktop-privileges poppler-utils ppp pulseaudio
  pulseaudio-module-bluetooth pulseaudio-utils python-apport python-apt
  python-apt-common python-aptdaemon python-aptdaemon.gtk3widgets
  python-cryptography python-httplib2 python-ldb python-libxml2 python-lxml
  python-pil python-problem-report python-psutil python-renderpm
  python-reportlab python-reportlab-accel python-samba python-twisted-bin
  python-twisted-core python-twisted-names python-twisted-web python-urllib3
  python2.7 python2.7-minimal python3-apport python3-apt python3-aptdaemon
  python3-aptdaemon.gtk3widgets python3-cryptography python3-distro-info
  python3-httplib2 python3-jinja2 python3-lxml python3-pil
  python3-problem-report python3-renderpm python3-reportlab
  python3-reportlab-accel python3-software-properties python3-uno
  python3-urllib3 python3.6 python3.6-minimal qt5-gtk-platformtheme rake
  remmina remmina-common remmina-plugin-rdp remmina-plugin-secret
  remmina-plugin-vnc rfkill rsync ruby2.5 samba samba-common samba-common-bin
  samba-dsdb-modules samba-libs samba-vfs-modules sane-utils secureboot-db
  smbclient snapd software-properties-common software-properties-gtk
  ssh-askpass-gnome sudo syslinux syslinux-common systemd systemd-sysv tcpdump
  thunderbird thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-us thunderbird-locale-nl tzdata udev uno-libs3 ure
  usb-creator-common usb-creator-gtk util-linux uuid-runtime vim-common
  vim-tiny vlc vlc-bin vlc-data vlc-l10n vlc-plugin-base vlc-plugin-notify
  vlc-plugin-qt vlc-plugin-samba vlc-plugin-skins2 vlc-plugin-video-output
  vlc-plugin-video-splitter vlc-plugin-visualization wavpack wget whoopsie
  winbind wpasupplicant xserver-common xserver-xephyr xserver-xorg-core
  xserver-xorg-legacy xvfb xwayland xxd
679 upgraded, 15 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 712 MB of archives.
After this operation, 636 MB of additional disk space will be used.

Do you want to continue? [Y/n] Y

```

Then a lot of information that is not really helpfull, I think but at the end of the proces this is the message and probably the problem:
```

Extracting templates from packages: 100%
Preconfiguring packages ...
setting xserver-xorg-legacy/xwrapper/allowed_users from configuration file
(Reading database ... 270980 files and directories currently installed.)
Removing systemd-shim (9-1bzr4ubuntu1) ...
Removing 'diversion of /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service to /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd by systemd-shim'
dpkg-divert: error: rename involves overwriting '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service' with
  different file '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd', not allowed
dpkg: error processing package systemd-shim (--remove):
 installed systemd-shim package post-removal script subprocess returned error exit status 2
Errors were encountered while processing:
 systemd-shim
E: Sub-process /usr/bin/dpkg returned an error code (1)
arnold@arnold-Aspire-5542:~$ 

```
I hope this gives sufficient information on what is the problem and how to solve it.

---

### Post by SeijiSensei on 2020-09-24
You seem to have run afoul of this issue: [https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1773859](https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1773859)

You can follow the proposed work-arounds, but if it were me, I'd install a brand-new copy of 20.04 Groovy Gorilla. If you don't have a separate /home partition, now would be a good time to make one. Backup /home to another device, then when you reach the partitioning screen in the installer, choose manual partitioning. Set aside maybe 40 GB for the root ("/") partition, then make the remaining available space /home.  Then you can easily replace the operating system without endangering your personal files.

---

### Post by Impavidus on 2020-09-24
There are two small problems in the first command:
> **aveenhoff said:**
> ```
arnold@arnold-Aspire-5542:~$ sudo apt update
[sudo] password for arnold: 
...
Hit:6 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy InRelease                      
...
Err:7 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease                
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F

```...
Saucy is a very old Ubuntu release (13.10). For some reason it's still there in your sources. The other is a PPA with an authentication issue, so it can't be used. It can be fixed.

> **aveenhoff said:**
> ```
arnold@arnold-Aspire-5542:~$ sudo apt upgrade
...
679 upgraded, 15 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed....

```
679 upgrades! That's amazing. Sounds like your upgrades have been blocked by this issue for ages.

> **SeijiSensei said:**
> You seem to have run afoul of this issue: [https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1773859](https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1773859)

You can follow the proposed work-arounds, but if it were me, I'd install a brand-new copy of 20.04 Groovy Gorilla. If you don't have a separate /home partition, now would be a good time to make one. Backup /home to another device, then when you reach the partitioning screen in the installer, choose manual partitioning. Set aside maybe 40 GB for the root ("/") partition, then make the remaining available space /home.  Then you can easily replace the operating system without endangering your personal files.
Good catch that this is a known bug. But I agree: this system is seriously outdated, with so many unpatched bugs, undoubtedly including some security upgrades. A fresh install is the easy way out, so that would be 20.04 LTS Focal Fossa (Groovy Gorilla is 20.10, the current development version and next interim  release). I suggest you stick to LTS releases.

---

