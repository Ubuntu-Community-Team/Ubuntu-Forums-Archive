---
title: "Direct upgrade from ubuntu dapper server amd 64 to edgy amd 64"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by ctof78 on 2006-11-21
Hi,

My server computer is actually an ubuntu dapper amd 64 (installed from the official CD).
It means i have no x-server installed.
I have to make the upgrade from command line (and install package over internet). 

I try to upgrade to edgy, to do that i have read some help and post and so i decide to change my /etc/ap/source.list (replace dapper to edgy) and make a "sudo apt-get update".
After here no pb, i have no extra repository into my apt configuration.

So i try to make a "apt-get dist-upgrade" and i check what package will be installed. Surprise! it seems the upgrade want to install a generic kernel (see at end of post for ouput information)

I not sure but if i understand what apt-get says:
* it download all generic (i386) install or update all package
* After that i have to re-install amd 64b package and to re-install all the system ?

[B]Is there a way to directly upgade an AMD 64b server from dapper to edgy ?
[/B]
Thx
Christophe
uname -a: Linux aragorn 2.6.15-27-amd64-server #1 SMP Sat Sep 16 02:04:37 UTC 2006 x86_64 GNU/Linux
"apt-get dist-upgrade" output 
[I]Les NOUVEAUX paquets suivants seront installés :
  console-setup console-terminus courier-authlib courier-authlib-userdb dash
  fontconfig-config gcc-4.1-base liba52-0.7.4 libavcodec0d libavformat0d libdb4.4
  libdbus-1-3 libdirectfb-0.9-24 libgnutls13 libgssapi2 libhd13 libnewt0.52
  libparted1.7-1 libpci2 libraw1394-8 librpcsecgss2 libtasn1-3 libvolumeid0
  libx11-data libxdmcp6 **[COLOR="Red"]linux-image-2.6.17-10-server[/COLOR]** linux-image-server linux-server
  mktemp python-central python-support sysvutils tasksel tasksel-data tzdata
  util-linux-locales vim-tiny volumeid xbitmaps xkb-data
Les paquets suivants ont été conservés :
  ubuntu-minimal
Les paquets suivants seront mis à jour :
  adduser alsa-base alsa-utils apache-common apache2 apache2-common
  apache2-mpm-prefork apache2-utils apt apt-utils aptitude at awstats backup-manager
  backup-manager-doc backupninja base-files bash belocs-locales-bin bind9 bind9-host
  bsdmainutils bsdutils busybox-initramfs bzip2 cdrecord console-common console-data
  console-tools coreutils courier-authdaemon courier-base courier-imap cpio
  cracklib-runtime cracklib2 cron dcraw debconf debconf-i18n debianutils defoma
  dhcp3-client dhcp3-common dhcp3-server dialog dictionaries-common dmidecode
  dmsetup dnsutils dpkg dselect e2fslibs e2fsprogs eject evms evms-ncurses fdutils
  fetchmail ffmpeg file findutils fontconfig gamin gcc-4.0-base gettext gettext-base
  gnupg grep groff-base grub gsasl gzip hdparm hostname hwdata hwinfo imagemagick
  info initramfs-tools initscripts installation-report iproute iptables
  iputils-arping iputils-ping iputils-tracepath iso-codes jhead klibc-utils klogd
  ldap-utils ldapscripts less libacl1 libapache2-mod-php5 libapache2-svn libapr0
  libasound2 libattr1 libbind9-0 libblkid1 libbz2-1.0 libc6 libcomerr2 libconsole
  libcupsys2 libdbd-mysql-perl libdbi-perl libdc1394-13 libdevmapper1.02 libdns21
  libelfg0 libevms-2.5 libexpat1 libfontconfig1 libfreetype6 libfribidi0 libgamin0
  libgc1c2 libgcc1 libgcrypt11 libgd2-xpm libgdbm3 libglib2.0-0 libgnutls12
  libgpg-error0 libgpmg1 libgsasl7 libhal1 libice6 libidn11 libimlib2
  libio-multiplex-perl libiodbc2 libisc11 libisccc0 libisccfg1 libiw28 libjpeg-progs
  libjpeg62 libklibc libkrb53 liblcms1 libldap-2.2-7 libldap2 liblockfile1 libltdl3
  liblwres9 libmagic1 libmagick9 libmysqlclient15off libncurses5 libncursesw5
  libnet-daemon-perl libnet-dns-perl libnet-ssleay-perl libnetpbm10 libnfsidmap1
  libnss-ldap libogg0 libopencdk8 libpam-ccreds libpam-cracklib libpam-ldap
  libpam-modules libpam-runtime libpam0g libpcap0.8 libpcre3 libperl5.8
  libplrpc-perl libpng12-0 libpopt0 libsasl2 libsasl2-modules libsdl1.2debian
  libsdl1.2debian-alsa libselinux1 libsepol1 libslang2 libsm6 libsqlite3-0 libss2
  libssl0.9.8 libstdc++6 libsvn0 libsysfs2 libtasn1-2 libtext-charwidth-perl
  libtext-iconv-perl libtext-wrapi18n-perl libtheora0 libtiff4 libungif4g
  liburi-perl libusb-0.1-4 libuuid1 libvorbis0a libvorbisenc2 libwrap0 libx11-6
  libxau6 libxaw7 libxext6 libxft2 libxml2 libxmu6 libxpm4 libxrender1 libxt6
  linux-amd64-server linux-image-amd64-server linux-sound-base locales login
  logrotate lsb-base lsb-release lshw lsof ltrace lvm-common lvm2 lynx makedev
  manpages mawk mdadm memtest86+ mii-diag mime-support mkisofs mldonkey-server
  module-init-tools mount mtr-tiny mysql-client-5.0 mysql-common mysql-server
  mysql-server-5.0 nano ncurses-base ncurses-bin net-tools netbase netcat netpbm
  nfs-common nfs-kernel-server ntp ntp-server ntp-simple ntpdate openssh-client
  openssh-server openssl p7zip parted passwd patch pciutils pcmciautils perl
  perl-base perl-modules php5-common php5-ldap php5-mysql php5-mysqli phpldapadmin
  popularity-contest portmap postfix postgrey ppp pppconfig pppoeconf procmail
  procps psmisc python python-clearsilver python-minimal python-pysqlite2
  python-subversion python2.4 python2.4-minimal python2.4-subversion rcs
  reiserfsprogs reportbug rsync samba samba-common samba-doc screen sed slapd smbfs
  squirrelmail squirrelmail-locales strace subversion subversion-tools sudo sysklogd
  sysv-rc sysvinit tar tcpd tcpdump trac ttf-bitstream-vera ttf-dejavu ttf-freefont
  ubuntu-standard ucf udev unzip usbmount usbutils util-linux vim vim-common
  vim-runtime wget whiptail wireless-tools wpasupplicant x11-common xfsprogs xterm
  zip zlib1g
335 mis à jour, 40 nouvellement installés, 2 à enlever et 1 non mis à jour.
Il est nécessaire de prendre 192Mo dans les archives.
[/I]

---

