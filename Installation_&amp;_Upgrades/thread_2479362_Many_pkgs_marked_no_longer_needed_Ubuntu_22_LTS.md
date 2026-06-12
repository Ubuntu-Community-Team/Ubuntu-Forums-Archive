---
title: "Many pkgs marked no longer needed Ubuntu 22 LTS"
date: 2022-09-22
forum: Installation &amp; Upgrades
---

### Post by mdtancsa on 2022-09-22
For some reason after doing an apt update and apt dist-upgrade, this particular install thinks there are a whole bunch of dependencies / packages no longer needed including netplan and udev which are for sure. Whats odd is I certainly need netplan udev as well as all the libvirt items.  Any idea whats going on here and how to fix ?

Ubuntu 22.04.1 LTS and I am able to boot 5.15.0-48-generic which brought in those updates.

```
 apt dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  acl adwaita-icon-theme alsa-topology-conf alsa-ucm-conf apport-symptoms at-spi2-core bc cpu-checker dconf-gsettings-backend dconf-service distro-info distro-info-data dns-root-data dnsmasq-base eatmydata
  fontconfig gir1.2-atk-1.0 gir1.2-ayatanaappindicator3-0.1 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0 gir1.2-glib-2.0 gir1.2-gstreamer-1.0 gir1.2-gtk-3.0 gir1.2-gtk-vnc-2.0 gir1.2-gtksource-4 gir1.2-harfbuzz-0.0
  gir1.2-libosinfo-1.0 gir1.2-libvirt-glib-1.0 gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gir1.2-spiceclientglib-2.0 gir1.2-spiceclientgtk-3.0 gir1.2-vte-2.91 glib-networking glib-networking-common
  glib-networking-services gsettings-desktop-schemas gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-x gtk-update-icon-cache hicolor-icon-theme humanity-icon-theme i965-va-driver ibverbs-providers
  intel-media-va-driver ipxe-qemu ipxe-qemu-256k-compat-efi-roms iso-codes jq libaa1 libappstream4 libasound2 libasound2-data libasyncns0 libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatspi2.0-0 libavahi-client3
  libavahi-common-data libavahi-common3 libavc1394-0 libayatana-appindicator3-1 libayatana-ido3-0.4-0 libayatana-indicator3-7 libboost-iostreams1.74.0 libboost-thread1.74.0 libbrlapi0.8 libcaca0 libcacard0
  libcairo-gobject2 libcairo2 libcdparanoia0 libcolord2 libcups2 libdatrie1 libdaxctl1 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdconf1 libdecor-0-0 libdecor-0-plugin-1-cairo libdeflate0 libdv4 libdw1 libeatmydata1
  libepoxy0 libfdt1 libflac8 libgbm1 libgdk-pixbuf-2.0-0 libgdk-pixbuf2.0-bin libgdk-pixbuf2.0-common libgfapi0 libgfrpc0 libgfxdr0 libgirepository-1.0-1 libglib2.0-bin libglusterfs0 libgovirt-common libgovirt2
  libgraphite2-3 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk-vnc-2.0-0 libgtksourceview-4-0 libgtksourceview-4-common libgvnc-1.0-0
  libharfbuzz0b libibverbs1 libiec61883-0 libigdgmm12 libinih1 libiscsi7 libjack-jackd2-0 libjbig0 libjpeg-turbo8 libjpeg8 libjq1 liblcms2-2 libmp3lame0 libmpg123-0 libmspack0 libndctl6 libnetplan0 libnfsidmap1
  libnl-route-3-200 libogg0 libonig5 libopus0 liborc-0.4-0 libosinfo-1.0-0 libpackagekit-glib2-18 libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpangoxft-1.0-0 libpcsclite1 libphodav-2.0-0
  libphodav-2.0-common libpixman-1-0 libpmem1 libpmemobj1 libproxy1v5 libpulse0 librados2 libraw1394-11 librbd1 librdmacm1 librest-0.7-0 librsvg2-2 librsvg2-common libsamplerate0 libsdl2-2.0-0 libshout3 libslirp0
  libsndfile1 libsoup-gnome2.4-1 libsoup2.4-1 libsoup2.4-common libspeex1 libspice-client-glib-2.0-8 libspice-client-gtk-3.0-5 libspice-server1 libstemmer0d libtag1v5 libtag1v5-vanilla libthai-data libthai0
  libtheora0 libtiff5 libtpms0 libtwolame0 liburing2 libusbredirhost1 libusbredirparser1 libv4l-0 libv4lconvert0 libva-x11-2 libva2 libvirglrenderer1 libvirt-clients libvirt-daemon libvirt-daemon-config-network
  libvirt-daemon-config-nwfilter libvirt-daemon-driver-qemu libvirt-daemon-system libvirt-daemon-system-systemd libvirt-glib-1.0-0 libvirt-glib-1.0-data libvisual-0.4-0 libvorbis0a libvorbisenc2 libvpx7
  libvte-2.91-0 libvte-2.91-common libwavpack1 libwayland-cursor0 libwayland-egl1 libwayland-server0 libwebp7 libxcb-render0 libxcursor1 libxdamage1 libxkbcommon0 libxml2-utils libxmlsec1 libxmlsec1-openssl
  libxslt1.1 libxss1 libyaml-0-2 mdevctl mesa-va-drivers msr-tools osinfo-db ovmf packagekit packagekit-tools python-apt-common python-babel-localedata qemu-block-extra qemu-system-common qemu-system-data
  qemu-system-gui qemu-system-x86 qemu-utils rpcbind run-one seabios session-migration spice-client-glib-usb-acl-helper swtpm swtpm-tools ubuntu-mono va-driver-all virt-viewer zerofree
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  cloud-guest-utils netplan.io nfs-common python3-cairo python3-certifi python3-cffi-backend python3-chardet python3-dbus python3-gi python3-gi-cairo python3-idna python3-libvirt python3-libxml2 python3-netifaces
  python3-pkg-resources python3-requests python3-six python3-urllib3 python3-yaml virt-manager virtinst
The following packages have been kept back:
  grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed libpython3-stdlib libpython3.10 libpython3.10-minimal libpython3.10-stdlib python3 python3-distutils python3-gdbm python3-lib2to3 python3-minimal python3.10
  python3.10-minimal
The following packages will be upgraded:
  gzip
1 upgraded, 0 newly installed, 21 to remove and 14 not upgraded.
Need to get 96.0 kB of archives.
After this operation, 15.8 MB disk space will be freed.



```

---

### Post by ian-weisser on 2022-09-22
Couple issues:

1) Ensure that you have the "ubuntu-desktop" metapackage installed (if this is a Desktop system). If it's not installed, then install it. That will cure a lot of your problems.

2) The list of packages in the first section ("*The following packages were automatically installed and are no longer required*:") has nothing to do with dist-upgrade. Those are packages that you orphaned in the in the past. Review that list item-by-item. If you encounter a package that should not be removed, then "sudo apt install" it.

3) Looks like you have tried to change the version of Python included  with your release of Ubuntu. Never do that. Too much of your system  depends upon it. Change it back.

4) Many of those kept-back packages are undergoing Phased Updates. Run "apt-cache policy <packagename>" on each one. Leave the packages that are phasing alone -- they are not broken. Investigate kept-back packages that are NOT phasing -- you have likely introduced version conflicts or some other problem.

5) Avoid misusing "dist-upgrade". Using that command authorizes the system to remove packages. In most cases, plain old "upgrade" is all you need.

There is no single solution to all your problems. Plan on incremental progress.

---

### Post by encyclopedist on 2022-09-22
I seem to have similar problem. Today suddenly after `apt update` and `apt full-upgrade` apt shows it wants to remove 125 packages, including some essential ones, such as `ubnutu-desktop`. I did not proceed with upgrade, and my system is still working.

Last time I did `apt upgrade` was a couple of days ago, and that time there was nothing unusual. I have not manually installed or removed any packages lately. 

Therefore I conclude this is either a bug in apt or some erroneous dependency metadata was uploaded to repositories.

```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  apg apport-symptoms aptdaemon-data avahi-utils blt clang-tools-14 cups-pk-helper distro-info
  fonts-glyphicons-halflings fonts-lyx fonts-mathjax gedit-common genisoimage gir1.2-ayatanaappindicator3-0.1
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-goa-1.0 gir1.2-gst-plugins-base-1.0 gir1.2-gtksource-3.0
  gir1.2-gtksource-4 gir1.2-gudev-1.0 gir1.2-packagekitglib-1.0 gir1.2-rb-3.0 gir1.2-secret-1 gir1.2-snapd-1
  gir1.2-totem-1.0 gir1.2-totemplparser-1.0 gir1.2-udisks-2.0 gir1.2-unity-7.0 gir1.2-vte-2.91 gir1.2-wnck-3.0
  gnome-control-center-faces gnome-terminal-data hplip-data ibus-data ibus-gtk4 iw
  jupyter-nbextension-jupyter-js-widgets libblosc1 libboost-atomic-dev libboost-atomic1.74-dev libboost-atomic1.74.0
  libboost-chrono-dev libboost-chrono1.74-dev libboost-chrono1.74.0 libboost-container-dev libboost-container1.74-dev
  libboost-container1.74.0 libboost-context-dev libboost-context1.74-dev libboost-context1.74.0 libboost-coroutine-dev
  libboost-coroutine1.74-dev libboost-coroutine1.74.0 libboost-date-time-dev libboost-date-time1.74-dev
  libboost-date-time1.74.0 libboost-dev libboost-exception-dev libboost-exception1.74-dev libboost-fiber-dev
  libboost-fiber1.74-dev libboost-fiber1.74.0 libboost-filesystem-dev libboost-filesystem1.74-dev libboost-graph-dev
  libboost-graph-parallel-dev libboost-graph-parallel1.74-dev libboost-graph-parallel1.74.0 libboost-graph1.74-dev
  libboost-graph1.74.0 libboost-iostreams-dev libboost-iostreams1.74-dev libboost-locale-dev libboost-locale1.74-dev
  libboost-log-dev libboost-log1.74-dev libboost-log1.74.0 libboost-math-dev libboost-math1.74-dev libboost-math1.74.0
  libboost-mpi-dev libboost-mpi-python-dev libboost-mpi-python1.74-dev libboost-mpi-python1.74.0 libboost-mpi1.74-dev
  libboost-mpi1.74.0 libboost-nowide-dev libboost-nowide1.74-dev libboost-nowide1.74.0 libboost-numpy-dev
  libboost-numpy1.74-dev libboost-numpy1.74.0 libboost-program-options-dev libboost-program-options1.74-dev
  libboost-python1.74.0 libboost-random-dev libboost-random1.74-dev libboost-random1.74.0 libboost-regex-dev
  libboost-regex1.74-dev libboost-serialization-dev libboost-serialization1.74-dev libboost-serialization1.74.0
  libboost-stacktrace-dev libboost-stacktrace1.74-dev libboost-stacktrace1.74.0 libboost-system-dev
  libboost-system1.74-dev libboost-system1.74.0 libboost-test-dev libboost-test1.74-dev libboost-test1.74.0
  libboost-thread-dev libboost-thread1.74-dev libboost-timer-dev libboost-timer1.74-dev libboost-timer1.74.0
  libboost-tools-dev libboost-type-erasure-dev libboost-type-erasure1.74-dev libboost-type-erasure1.74.0
  libboost-wave-dev libboost-wave1.74-dev libboost-wave1.74.0 libboost1.74-dev libboost1.74-tools-dev libclang-cpp11
  libcmark-gfm-extensions0.29.0.gfm.3 libcmark-gfm0.29.0.gfm.3 libcolord-gtk1 libdmapsharing-3.0-2 libgpod-common
  libgpod4 libgssdp-1.2-0 libgupnp-1.2-1 libgupnp-av-1.0-3 libgupnp-dlna-2.0-4 libhpmud0 libimagequant0 libjs-backbone
  libjs-bootstrap libjs-bootstrap-tour libjs-codemirror libjs-es6-promise libjs-jed libjs-jquery-typeahead
  libjs-marked libjs-mathjax libjs-moment libjs-requirejs libjs-requirejs-text libjs-sphinxdoc libjs-text-encoding
  libjs-underscore libjs-xterm liblbfgsb0 libllvm11 libncurses-dev libnetplan0 libpfm4 libpython3-dev libqhull-r8.0
  libraqm0 librsync2 librygel-core-2.6-2 librygel-db-2.6-2 librygel-renderer-2.6-2 librygel-server-2.6-2 libsane-hpaio
  libsgutils2-2 libtbb12 libtbbmalloc2 libtinfo-dev libwhoopsie-preferences0 libwnck-3-0 libwnck-3-common
  libxatracker2 libxres1 libxsimd-dev libxvmc1 libz3-dev llvm-11 llvm-11-linker-tools llvm-11-runtime llvm-13
  llvm-13-runtime llvm-14 llvm-14-runtime mobile-broadband-provider-info mpi-default-bin network-manager-gnome
  node-jed numba-doc pandoc pandoc-data printer-driver-hpcups printer-driver-postscript-hp python-apt-common
  python-babel-localedata python-matplotlib-data python-odf-doc python-odf-tools python-tables-data python3-appdirs
  python3-argon2 python3-attr python3-babel python3-backcall python3-bcrypt python3-beniget python3-bleach
  python3-blinker python3-brlapi python3-brotli python3-bs4 python3-certifi python3-cffi-backend python3-click
  python3-colorama python3-cryptography python3-cycler python3-dateutil python3-debconf python3-debian
  python3-decorator python3-defer python3-defusedxml python3-distro-info python3-entrypoints python3-et-xmlfile
  python3-fasteners python3-fs python3-gast python3-html5lib python3-httplib2 python3-idna python3-importlib-metadata
  python3-iniconfig python3-ipython python3-ipython-genutils python3-jdcal python3-jedi python3-jeepney
  python3-jsonschema python3-jupyterlab-pygments python3-jwt python3-keyring python3-kiwisolver python3-launchpadlib
  python3-lazr.restfulclient python3-lazr.uri python3-llvmlite python3-lockfile python3-louis python3-lz4
  python3-matplotlib-inline python3-monotonic python3-more-itertools python3-mpmath python3-nest-asyncio
  python3-oauthlib python3-odf python3-olefile python3-packaging python3-pandocfilters python3-parso python3-pexpect
  python3-pickleshare python3-pluggy python3-ply python3-problem-report python3-prometheus-client
  python3-prompt-toolkit python3-protobuf python3-ptyprocess python3-py python3-pyparsing python3-pyrsistent
  python3-pytest python3-pyudev python3-renderpm python3-reportlab-accel python3-requests python3-rfc3339
  python3-secretstorage python3-send2trash python3-soupsieve python3-sympy python3-systemd python3-testpath
  python3-toml python3-traitlets python3-tz python3-unicodedata2 python3-urllib3 python3-wadllib python3-wcwidth
  python3-webencodings python3-xkit python3-xlib python3-xlwt python3-zipp rygel sphinx-rtd-theme-common tk8.6-blt2.5
  unicode-data whoopsie-preferences x11-apps x11-session-utils xbitmaps xbrlapi xcvt xfonts-scalable xinit xinput
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-libinput xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-nouveau xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-vesa
  xserver-xorg-video-vmware
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  apport apport-gtk aptdaemon apturl apturl-common clang-tidy clang-tidy-14 command-not-found deja-dup duplicity gedit
  gnome-control-center gnome-online-accounts gnome-terminal hplip ibus ibus-table jupyter-core jupyter-notebook
  language-selector-common language-selector-gnome libboost-all-dev libboost-python-dev libboost-python1.74-dev
  llvm-11-dev llvm-11-tools llvm-13-dev llvm-13-tools llvm-14-dev llvm-14-tools meld nautilus-extension-gnome-terminal
  nautilus-share netplan.io networkd-dispatcher orca python3-apport python3-apt python3-aptdaemon
  python3-aptdaemon.gtk3widgets python3-bottleneck python3-cairo python3-commandnotfound python3-cups
  python3-cupshelpers python3-dbus python3-dev python3-distupgrade python3-fonttools python3-future python3-gdbm
  python3-gi-cairo python3-ibus-1.0 python3-ipykernel python3-ipywidgets python3-jinja2 python3-jupyter-client
  python3-jupyter-core python3-lxml python3-macaroonbakery python3-mako python3-markupsafe python3-matplotlib
  python3-nacl python3-nbclient python3-nbconvert python3-nbformat python3-netifaces python3-notebook python3-numba
  python3-numexpr python3-numpy python3-openpyxl python3-pandas python3-pandas-lib python3-paramiko python3-pil
  python3-pil.imagetk python3-pip python3-pyatspi python3-pymacaroons python3-pythran python3-reportlab python3-scipy
  python3-software-properties python3-tables python3-tables-lib python3-terminado python3-tk python3-tornado
  python3-ufolib2 python3-uno python3-update-manager python3-venv python3-wheel python3-widgetsnbextension
  python3-yaml python3-zmq rhythmbox-plugin-alternative-toolbar rhythmbox-plugins software-properties-common
  software-properties-gtk solaar system-config-printer system-config-printer-common system-config-printer-udev
  totem-plugins ubuntu-advantage-desktop-daemon ubuntu-advantage-tools ubuntu-desktop ubuntu-desktop-minimal
  ubuntu-drivers-common ubuntu-minimal ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk ubuntu-session
  unattended-upgrades update-manager update-manager-core update-notifier update-notifier-common usb-creator-common
  usb-creator-gtk xorg xserver-xorg
The following NEW packages will be installed:
  gnome-session
The following packages have been kept back:
  evolution-data-server evolution-data-server-common gnome-tweaks grub-efi-amd64-bin grub-efi-amd64-signed gzip
  libcamel-1.2-63 libebackend-1.2-10 libebook-1.2-20 libebook-contacts-1.2-3 libecal-2.0-1 libedata-book-1.2-26
  libedata-cal-2.0-1 libedataserver-1.2-26 libedataserverui-1.2-3 libnss-systemd libpam-systemd libpython3-dev
  libpython3-stdlib libpython3.10 libpython3.10-dev libpython3.10-minimal libpython3.10-stdlib libspeechd2 libsystemd0
  libudev-dev libudev1 mypy python3 python3-distutils python3-lib2to3 python3-minimal python3-mypy python3-oauthlib
  python3-speechd python3.10 python3.10-dev python3.10-minimal python3.10-venv speech-dispatcher
  speech-dispatcher-audio-plugins speech-dispatcher-espeak-ng systemd systemd-oomd systemd-sysv systemd-timesyncd udev
  xwayland
The following packages will be upgraded:
  libpcre2-16-0 libpcre2-32-0 libpcre2-8-0 libpcre2-dev libpcre2-posix3
5 upgraded, 1 newly installed, 125 to remove and 48 not upgraded.
5 standard security updates
Need to get 1,369 kB of archives.
After this operation, 1,015 MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.

```

---

### Post by encyclopedist on 2022-09-22
APT log since the last manual upgrade:

```
Start-Date: 2022-09-20  13:35:50
Commandline: apt full-upgrade
Requested-By: ilya (1000)
Install: linux-image-5.15.0-48-generic:amd64 (5.15.0-48.54, automatic), linux-tools-5.15.0-48-generic:amd64 (5.15.0-48.54, automatic), linux-headers-5.15.0-48-generic:amd64 (5.15.0-48.54, automatic), linux-modules-5.15.0-48-generic:amd64 (5.15.0-48.54, automatic), linux-modules-extra-5.15.0-48-generic:amd64 (5.15.0-48.54, automatic), linux-tools-5.15.0-48:amd64 (5.15.0-48.54, automatic), linux-headers-5.15.0-48:amd64 (5.15.0-48.54, automatic)
Upgrade: libreoffice-l10n-en-gb:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libreoffice-l10n-en-za:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libreoffice-calc:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), linux-tools-common:amd64 (5.15.0-47.51, 5.15.0-48.54), libreoffice-gnome:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), uno-libs-private:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libreoffice-base-core:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libreoffice-pdfimport:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), linux-headers-generic:amd64 (5.15.0.47.47, 5.15.0.48.48), libreoffice-core:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libreoffice-common:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), ure:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libtiffxx5:amd64 (4.3.0-6, 4.3.0-6ubuntu0.1), linux-image-generic-hwe-22.04:amd64 (5.15.0.47.47, 5.15.0.48.48), libreoffice-draw:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libtiff5:amd64 (4.3.0-6, 4.3.0-6ubuntu0.1), libuno-purpenvhelpergcc3-3:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libuno-cppu3:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libreoffice-impress:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libreoffice-l10n-ru:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libuno-cppuhelpergcc3-3:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), fonts-opensymbol:amd64 (2:102.12+LibO7.3.5-0ubuntu0.22.04.1, 2:102.12+LibO7.3.6-0ubuntu0.22.04.1), linux-generic:amd64 (5.15.0.47.47, 5.15.0.48.48), libreoffice-style-colibre:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libreoffice-writer:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libuno-salhelpergcc3-3:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libreoffice-style-breeze:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libreoffice-help-ru:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), linux-headers-generic-hwe-22.04:amd64 (5.15.0.47.47, 5.15.0.48.48), linux-generic-hwe-22.04:amd64 (5.15.0.47.47, 5.15.0.48.48), linux-image-generic:amd64 (5.15.0.47.47, 5.15.0.48.48), libreoffice-help-common:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), linux-tools-generic:amd64 (5.15.0.47.47, 5.15.0.48.48), python3-uno:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libuno-sal3:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libreoffice-ogltrans:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libreoffice-style-yaru:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libreoffice-math:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libreoffice-gtk3:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libtiff-dev:amd64 (4.3.0-6, 4.3.0-6ubuntu0.1), libreoffice-help-en-gb:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libreoffice-help-en-us:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), libreoffice-style-elementary:amd64 (1:7.3.5-0ubuntu0.22.04.1, 1:7.3.6-0ubuntu0.22.04.1), linux-libc-dev:amd64 (5.15.0-47.51, 5.15.0-48.54)
End-Date: 2022-09-20  13:36:23

Start-Date: 2022-09-21  06:50:16
Commandline: /usr/bin/unattended-upgrade
Remove: linux-image-5.15.0-46-generic:amd64 (5.15.0-46.49), linux-modules-5.15.0-46-generic:amd64 (5.15.0-46.49), linux-modules-extra-5.15.0-46-generic:amd64 (5.15.0-46.49)
End-Date: 2022-09-21  06:50:18

Start-Date: 2022-09-21  06:50:19
Commandline: /usr/bin/unattended-upgrade
Remove: linux-tools-5.15.0-46-generic:amd64 (5.15.0-46.49), linux-tools-5.15.0-46:amd64 (5.15.0-46.49)
End-Date: 2022-09-21  06:50:19

Start-Date: 2022-09-21  06:50:21
Commandline: /usr/bin/unattended-upgrade
Remove: linux-headers-5.15.0-46-generic:amd64 (5.15.0-46.49)
End-Date: 2022-09-21  06:50:21

Start-Date: 2022-09-21  06:50:23
Commandline: /usr/bin/unattended-upgrade
Remove: linux-headers-5.15.0-46:amd64 (5.15.0-46.49)
End-Date: 2022-09-21  06:50:23

Start-Date: 2022-09-22  06:47:17
Commandline: /usr/bin/unattended-upgrade
Upgrade: bind9-host:amd64 (1:9.18.1-1ubuntu1.1, 1:9.18.1-1ubuntu1.2), bind9-dnsutils:amd64 (1:9.18.1-1ubuntu1.1, 1:9.18.1-1ubuntu1.2), bind9-libs:amd64 (1:9.18.1-1ubuntu1.1, 1:9.18.1-1ubuntu1.2)
End-Date: 2022-09-22  06:47:17

Start-Date: 2022-09-22  06:47:19
Commandline: /usr/bin/unattended-upgrade
Upgrade: python3-mako:amd64 (1.1.3+ds1-2, 1.1.3+ds1-2ubuntu0.1)
End-Date: 2022-09-22  06:47:20
```

---

### Post by encyclopedist on 2022-09-22
This bug on launchpad: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1990586](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1990586)

---

### Post by mdtancsa on 2022-09-22
> **ian-weisser said:**
> Couple issues:


3) Looks like you have tried to change the version of Python included  with your release of Ubuntu. Never do that. Too much of your system  depends upon it. Change it back.

There is no single solution to all your problems. Plan on incremental progress.

Odd, I never intentionally changed the python version. Its python3.10 which seems to be on the other ubuntu 22 LTS boxes I have too which I have yet to update.

---

### Post by mdtancsa on 2022-09-22
> **encyclopedist said:**
> This bug on launchpad: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1990586](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1990586)

Thanks! It sure felt like a bug

---

### Post by ian-weisser on 2022-09-22
> **encyclopedist said:**
> This bug on launchpad: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1990586](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1990586)

Good job finding the Launchpad bug that DOES tie both of these together!

Looks like this can be avoided either by waiting a few days for phasing to finish (avoid use of 'full-upgrade'), OR by waiting a few days for the bug to be addressed, OR by temporarily disabling phasing (apt -o APT::Get::Always-Include-Phased-Updates=true upgrade). 

Gentle reminder that "dist-upgrade" is a bit too old-school. Ubuntu folks should have migrated to using "full-upgrade" years ago.

EDIT: The phasing of Python3 packages has been stopped due to the bug report. Normal apt upgrades and apt full-upgrades should work properly again. The fix was applied about one hour after the first bug report.

---

