---
title: "command line upgrade from 10.04 to 12.04 for a vm has issues"
date: 2012-07-18
forum: Installation &amp; Upgrades
---

### Post by dsalmen on 2012-07-18
My command line upgrade to 12.04 seems to have ended up with some issues:

$ sudo apt-get upgrade
         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.10.1-0ubuntu19) but 2.15-0ubuntu10 is installed
         Recommends: libc6-i686 but it is not installed
E: Unmet dependencies. Try using -f.

I have done a fair number of command line upgrades with success, but not quite sure where to go next on this one.

I believe it gave a message about reverting back to previous version and current shows:

linux 2.6.18-194.17.1.el5.028stab070.7 i686
ubuntu 10.04 lucid

Thanks for any ideas...

---

### Post by darkod on 2012-07-18
apt-get upgrade does not upgrade to a new release. That only upgrades the packages that can be upgraded, not the ubuntu version itself.

The CLI command to upgrade was something like dist-upgrade and do-release-upgrade.

Also, I think the upgrade to 12.04 LTS from 10.04 LTS will be available only after 12.04.1 is released in August (late August).

As suggested, try the:
sudo apt-get install -f

to fix any broken packages/dependencies.

Are you sure you have ubuntu 10.04? The 2.6.18-194.17.1.el5.028stab070.7 i686 sounds more like CentOS or Red Hat to me.

---

### Post by dsalmen on 2012-07-18
I think my mistake was I used the -d option:[B]

sudo do-release-upgrade -d[/B]

I did not realize final cut was so far out.  It rolled back to 10.04 at the end, but left me in a messy state.  Not sure if any manual steps exist to fix up the dependency problems I am hitting.

---

### Post by dsalmen on 2012-07-18
I think my mistake was I used the -d option:[B]

sudo do-release-upgrade -d[/B]

I did not realize final cut was so far out.  It rolled back to 10.04 at the end, but left me in a messy state.  Not sure if any manual steps exist to fix up the dependency problems I am hitting.

Output from sudo apt-get install -f follows:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libgtk2.0-common ttf-dejavu-core libgtop2-common libgnomeui-common libavahi-common-data
  libbonoboui2-common esound-common hicolor-icon-theme geoip-database gcj-4.4-base libgsf-1-common
  libgnomecanvas2-common libthai-data gnome-mime-data tsconf libbonobo2-common libdjvulibre-text
  libvte-common make
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  adduser ant apt apt-utils apt-xapian-index aptitude apturl apturl-common base-files base-passwd bash
  bind9-host binfmt-support bsdmainutils bsdutils busybox-initramfs bzip2 ca-certificates consolekit
  coreutils cpio cpp cpp-4.4 cron dash dbus dbus-x11 debconf debconf-i18n debianutils defoma
  devicekit-disks dhcp3-client dhcp3-common dictionaries-common diff dmidecode dnsutils docbook-xml dpkg
  e2fslibs e2fsprogs esound-clients file findutils firefox firefox-3.0 firefox-3.0-branding
  firefox-branding fontconfig fontconfig-config gamin gappletviewer-4.3 gcj-4.4-jre-headless
  gcj-4.4-jre-lib gconf2 gconf2-common gettext-base ghostscript gij-4.3 gksu gnome-icon-theme
  gnome-keyring gnupg gpgv grep groff-base gsfonts gvfs gvfs-backends gzip hostname hunspell-en-us
  ifupdown initramfs-tools initscripts insserv install-info iproute iptables iputils-ping
  launchpad-integration less libacl1 libapr1 libaprutil1 libapt-inst1.4 libapt-pkg4.12 libarchive1
  libart-2.0-2 libasound2 libatasmart4 libatk1.0-0 libatm1 libattr1 libaudiofile0 libavahi-client3
  libavahi-common3 libavahi-glib1 libbind9-50 libblkid1 libbluetooth3 libbonobo2-0 libbonoboui2-0 libbsd0
  libbz2-1.0 libc6 libcairo-perl libcairo2 libcap2 libcdio-cdda0 libcdio-paranoia0 libcdio7
  libck-connector0 libcomerr2 libconsole libcroco3 libcups2 libcupsimage2 libcurl3-gnutls libcwidget3
  libdatrie1 libdb4.2 libdb4.5 libdb4.6 libdb4.7 libdbus-1-3 libdbus-glib-1-2 libdevmapper1.02.1
  libdirectfb-1.2-0 libdjvulibre21 libdns43 libdns53 libedit2 libeggdbus-1-0 libept0 libesd-alsa0
  libexif12 libexpat1 libffi5 libfontconfig1 libfreetype6 libfribidi0 libgail18 libgamin0 libgcc1
  libgcj-common libgcj10 libgcj9-0 libgcj9-0-awt libgcj9-jar libgconf2-4 libgcr0 libgcrypt11 libgd2-noxpm
  libgdbm3 libgdu0 libgeoip1 libgksu2-0 libglade2-0 libglib-perl libglib2.0-0 libgmp3c2 libgnome-keyring0
  libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomecanvas2-0
  libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgnutls13 libgnutls26 libgomp1
  libgp11-0 libgpg-error0 libgphoto2-2 libgphoto2-port0 libgpm2 libgraphviz4 libgs8 libgsf-1-114
  libgssapi-krb5-2 libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtkhtml2-0 libgtop2-7 libgudev-1.0-0
  libgvfscommon0 libhal-storage1 libhal1 libhunspell-1.1-0 libhunspell-1.2-0 libice6 libidl0 libidn11
  libilmbase6 libisc44 libisc50 libisccc50 libisccfg50 libiw29 libjasper1 libjaxp1.3-java libjpeg62
  libk5crypto3 libkeyutils1 libkrb5-3 libkrb53 libkrb5support0 liblaunchpad-integration1 liblcms1
  libldap-2.4-2 liblocale-gettext-perl libltdl3 libltdl7 liblua5.1-0 liblwres50 liblzo2-2 libmagic1
  libmagickcore2 libmagickwand2 libmpfr1ldbl libncurses5 libncursesw5 libneon27 libneon27-gnutls
  libnewt0.52 libnspr4-0d libnss3-0d libnss3-1d libopencdk10 libopencdk8 libopenexr6 libopenobex1
  liborbit2 libpam-ck-connector libpam-foreground libpam-gnome-keyring libpam-modules libpam-runtime
  libpam0g libpango-perl libpango1.0-0 libpango1.0-common libpaper-utils libpaper1 libparted1.8-12
  libpcap0.8 libpcre3 libpixman-1-0 libpng12-0 libpolkit-agent-1-0 libpolkit-backend-1-0
  libpolkit-gobject-1-0 libpopt0 libproxy0 libpython2.6 libreadline5 libreadline6 librsvg2-2
  librsvg2-common libsasl2-2 libsasl2-modules libscrollkeeper0 libselinux1 libsepol1 libsgutils2-2
  libsigc++-2.0-0c2a libslang2 libsm6 libsmbclient libsoup-gnome2.4-1 libsoup2.4-1 libsqlite3-0 libss2
  libssl0.9.8 libstartup-notification0 libstdc++5 libstdc++6 libsvn1 libsysfs2 libtalloc1 libtasn1-3
  libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libthai0 libtiff4 libtimedate-perl
  libts-0.0-0 libudev0 libusb-0.1-4 libuuid1 libvte9 libwbclient0 libwmf0.2-7 libwrap0 libx11-6
  libxapian15 libxau6 libxcb-atom1 libxcb-aux0 libxcb-event1 libxcb-render-util0 libxcb-render0 libxcb1
  libxcomposite1 libxcursor1 libxdamage1 libxdmcp6 libxerces2-java libxext6 libxfixes3 libxft2 libxi6
  libxinerama1 libxml2 libxmuu1 libxp6 libxrandr2 libxrender1 libxslt1.1 libxt6 libxtst6 locales login
  lsb-base lsb-release lsof lzma makedev man-db mawk mktemp module-init-tools mount mountall ncurses-base
  ncurses-bin net-tools netbase netcat netcat-traditional nmap obex-data-server odbcinst1debian1
  openssh-client openssh-server openssl passwd perl perl-base perl-modules policykit-1 policykit-1-gnome
  procps psfontmgr psmisc python python-apt python-cairo python-central python-dbus python-debian
  python-glade2 python-gnupginterface python-gobject python-gtk2 python-gtkhtml2 python-minimal
  python-software-properties python-support python-vte python-xapian python2.4 python2.4-minimal python2.5
  python2.5-minimal python2.6 python2.6-minimal quota readline-common release-upgrader-python-apt rsync
  scrollkeeper sed sgml-base sgml-data shared-mime-info software-properties-gtk ssh subversion sudo
  sun-java6-bin sun-java6-jdk sun-java6-jre synaptic sysv-rc sysvinit-utils sysvutils tar tcpd tzdata
  ubufox ubuntu-keyring ucf udev unattended-upgrades unixodbc unzip update-inetd update-manager-core
  update-motd upstart util-linux util-linux-locales vim-common vim-runtime vim-tiny wget whiptail
  x11-common xauth xml-core zlib1g
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libc6 (due to apt) libgcc1 (due to apt) libstdc++6 (due to apt) base-files base-passwd (due to
  base-files) libpam-modules (due to base-files) mawk (due to base-files) bash debianutils (due to bash)
  dash (due to bash) libncurses5 (due to bash) bsdutils coreutils libacl1 (due to coreutils) libattr1 (due
  to coreutils) libselinux1 (due to coreutils) diff dpkg lzma (due to dpkg) e2fsprogs e2fslibs (due to
  e2fsprogs) libblkid1 (due to e2fsprogs) libcomerr2 (due to e2fsprogs) libss2 (due to e2fsprogs) libuuid1
  (due to e2fsprogs) findutils grep gzip hostname upstart (due to hostname) login libpam0g (due to login)
  libpam-runtime (due to login) mount libsepol1 (due to mount) ncurses-base ncurses-bin perl-base
  python-minimal python2.6-minimal (due to python-minimal) sed install-info (due to sed) tar util-linux
  lsb-base (due to util-linux) tzdata (due to util-linux) libslang2 (due to util-linux) zlib1g (due to
  util-linux)
0 upgraded, 0 newly installed, 430 to remove and 1 not upgraded.
After this operation, 819MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
```

---

### Post by CharlesA on 2012-07-18
If you ran the upgrade, it should have prompted you saying you were upgrading to 12.04, if it downgraded to 10.04 (which it shouldn't have), your system is more than likely hosed.

---

### Post by darkod on 2012-07-18
I think you didn't understand me. The 12.04 LTS version is final and was released in April. The option -d should allow you to upgrade from the previous LTS without waiting for the first point release.

For the LTS versions, after a while a so called point release is released, like .1, .2, .3, etc.

LTS to LTS upgrade is designed to be offered only after the .1 is released, which will be 12.04.1 in August. But with the -d option you can upgrade to 12.04 without waiting for 12.04.1.

But the 12.04 is final and should have worked. Not really sure what happened.

And those REMOVE packages in the info you provided, doesn't look good. Can't really help too much. All I know is that you can finish interrupted upgrade of packages with something like:
```
sudo dpkg --configure -a
sudo apt-get install -f
```

---

