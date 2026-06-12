---
title: "Issue with apt-get update on 10.04.4 LTS"
date: 2016-08-29
forum: Installation &amp; Upgrades
---

### Post by JAY6390 on 2016-08-29
So trying to upgrade 10.04.4 LTS to a more recent version with no success. I have updated my sources to the old-releases as per the info on the ubuntu site, but still not getting anywhere. Seems something is corrupted, but I don't know how to fix it (other than trying what is said on the console which didn't look like a good option to continue with). Any advice appreciated. Jay

EDIT: Note this is a server, not a desktop installation

```
root@my-server:~# cat /etc/apt/sources.list
deb http://old-releases.ubuntu.com/ubuntu lucid main
deb http://old-releases.ubuntu.com/ubuntu lucid-updates main
deb http://old-releases.ubuntu.com/ubuntu lucid-security main

root@my-server:~# apt-get update
Hit http://old-releases.ubuntu.com lucid Release.gpg
Hit http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_GB
Hit http://old-releases.ubuntu.com lucid-updates Release.gpg
Hit http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB
Hit http://old-releases.ubuntu.com lucid-security Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB
Hit http://old-releases.ubuntu.com lucid Release   
Hit http://old-releases.ubuntu.com lucid-updates Release
Hit http://old-releases.ubuntu.com lucid-security Release
Hit http://old-releases.ubuntu.com lucid/main Packages
Hit http://old-releases.ubuntu.com lucid-updates/main Packages
Hit http://old-releases.ubuntu.com lucid-security/main Packages
Reading package lists... Done

root@my-server:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.21) but 2.15-0ubuntu10.15 is installed
  libnih-dbus1: Depends: libnih1 (= 1.0.3-4ubuntu9.1) but 1.0.1-1 is installed
E: Unmet dependencies. Try using -f.

root@my-server:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  iso-codes plesk-wp-cli cpu-checker psa-zendframework linux-libc-dev manpages-dev libdjvulibre-text autotools-dev wpb-designs-00 wpb-designs-01 wpb-designs-03 wpb-designs-04
  wpb-designs-05 wpb-designs-12 wpb-designs-07 wpb-designs-14 wpb-designs-09 wpb-designs-20
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  adduser apache2 apache2-mpm-prefork apache2-utils apache2.2-bin apache2.2-common apt apt-utils autoconf automake awstats base-files base-passwd bash bash-completion bind9
  bind9-host bind9utils binutils bsd-mailx bsdmainutils bsdutils busybox-initramfs byobu bzip2 ca-certificates chkconfig comerr-dev console-common console-data console-tools
  console-tools-dev coreutils cpio cpp cpp-4.4 cracklib-runtime cron curl dash db4.7-util db4.8-util debconf debconf-i18n debconf-utils debianutils defoma dhcp3-common diff
  diffutils dmsetup dnsutils dpkg dselect e2fslibs e2fsprogs ed expat fetchmail file findutils finger fontconfig fontconfig-config ftp gawk gcc gcc-4.4 gettext gettext-base
  ghostscript git-core gnupg gpgv grep groff-base gsfonts gzip hostname idn ifupdown imagemagick info initramfs-tools initramfs-tools-bin initscripts insserv install-info
  iproute iptables iputils-arping iputils-ping iputils-tracepath klogd krb5-multidev ldap-utils less libacl1 libapache2-mod-aclr2-psa libapache2-mod-fcgid-psa
  libapache2-mod-perl2 libapache2-mod-php5 libapache2-mod-python libapache2-mod-rpaf libapache2-mod-suphp libapache2-mod-sysenv-psa libapache2-svn libapr1 libaprutil1
  libaprutil1-dbd-sqlite3 libaprutil1-ldap libaps libapt-inst1.4 libapt-pkg4.12 libarchive1 libatk1.0-0 libattr1 libavahi-client3 libavahi-common3 libbind9-60 libblkid1
  libboost-date-time1.40.0 libboost-filesystem1.40.0 libboost-program-options1.40.0 libboost-regex1.40.0 libboost-serialization1.40.0 libboost-system1.40.0
  libboost-thread1.40.0 libbsd0 libbz2-1.0 libc-client2007e libc-dev-bin libc6 libc6-dev libcairo2 libcap2 libcomerr2 libconsole libcrack2 libcroco3 libcups2 libcupsimage2
  libcurl3 libcurl3-gnutls libcurl4-gnutls-dev libdatrie1 libdb1-compat libdb4.7 libdb4.8 libdbd-mysql-perl libdbi-perl libdbus-1-3 libdevel-symdump-perl libdevmapper1.02.1
  libdigest-hmac-perl libdigest-sha1-perl libdirectfb-1.2-0 libdjvulibre21 libdns64 libdrm-intel1 libdrm-nouveau1 libdrm-radeon1 libdrm2 libedit2 liberror-perl libexpat1
  libexpat1-dev libffi5 libfile-copy-recursive-perl libfile-temp-perl libfontconfig1 libfreetype6 libgcc1 libgcrypt11 libgcrypt11-dev libgd2-xpm libgdbm3 libgeoip1
  libglib2.0-0 libgmp3c2 libgnutls-dev libgnutls26 libgomp1 libgpg-error-dev libgpg-error0 libgpm2 libgraphviz4 libgs8 libgssapi-krb5-2 libgssrpc4 libgtk2.0-0
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libice6 libicu42 libidn11 libidn11-dev libilmbase6 libisc60 libisccc60 libisccfg60 libjasper1 libjpeg-progs
  libjpeg62 libk5crypto3 libkadm5clnt-mit7 libkadm5srv-mit7 libkdb5-4 libkeyutils1 libkrb5-3 libkrb5-dev libkrb5support0 liblcms1 libldap-2.4-2 libldap2-dev
  liblocale-gettext-perl liblockfile1 libltdl-dev libltdl7 liblwres60 liblzma1 liblzo2-2 libmagic1 libmagickcore2 libmagickcore2-extra libmagickwand2 libmcrypt4 libmpfr1ldbl
  libmyodbc libmysqlclient16 libncurses5 libncursesw5 libneon27-gnutls libnet-daemon-perl libnet-dns-perl libnet-ip-perl libnetaddr-ip-perl libnewt0.52 libnih-dbus1 libnih1
  libnl1 libntfs10 libopenexr6 libpam-foreground libpam-modules libpam-plesk libpam-runtime libpam0g libpango1.0-0 libpango1.0-common libpaper1 libpcap0.8 libpcre3
  libperl5.10 libpixman-1-0 libpkcs11-helper1 libplrpc-perl libplymouth2 libpng12-0 libpopt0 libpq5 libpython2.6 librdbmspp libreadline6 libsasl2-2 libsasl2-modules
  libsasl2-modules-sqlite3 libselinux1 libsensors4 libsepol1 libslang2 libsm6 libsnmp-base libsnmp15 libsocket6-perl libsqlite0 libsqlite3-0 libss2 libssl-dev libssl0.9.8
  libstdc++6 libsvn1 libsys-hostname-long-perl libsysfs2 libt1-5 libtalloc2 libtasn1-3 libtasn1-3-dev libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libthai0
  libtiff4 libtimedate-perl libtokyocabinet8 libtool libts-0.0-0 libudev0 liburi-perl libusb-0.1-4 libuuid1 libwbclient0 libwmf0.2-7 libwrap0 libwww-perl libx11-6 libxau6
  libxcb-render-util0 libxcb-render0 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6 libxext6 libxfixes3 libxft2 libxi6 libxinerama1 libxml-dumper-perl
  libxml-namespacesupport-perl libxml-parser-perl libxml-sax-base-perl libxml-sax-expat-perl libxml-sax-perl libxml-simple-perl libxml2 libxmlrpc-c3 libxmlrpc-core-c3 libxpm4
  libxrandr2 libxrender1 libxslt1.1 libxt6 locales log4cpp-plesk login logrotate lsb-base lsb-release lsof lynx lynx-cur lzma m4 makedev man-db memtester mktemp mlocate mlock
  module-init-tools mount mountall mtools multiarch-support mysql-client-5.1 mysql-client-core-5.1 mysql-server-5.1 mysql-server-core-5.1 nano ncftp ncurses-base ncurses-bin
  net-tools netbase ntpdate odbcinst odbcinst1debian1 openssh-blacklist openssh-client openssh-server openssl openssl-blacklist openvpn openvpn-blacklist passwd patch perl
  perl-base perl-modules php-net-ftp php-pear php5 php5-cgi php5-cli php5-common php5-curl php5-dev php5-gd php5-imap php5-ioncube-loader php5-mcrypt php5-mysql php5-sqlite
  php5-xsl pigz pkg-config plesk-base plesk-completion plesk-core plesk-courier-imap-driver plesk-dns-bind-driver plesk-l10n plesk-librdbmspp plesk-lmlib plesk-mail-pc-driver
  plesk-management-node plesk-platform-runtime plesk-roundcube plesk-service-node-utilities plesk-web-hosting plymouth pngcrush portmap postfix postfix-pcre pp-sitebuilder
  pp10.13.4-bootstrapper pp11.0.9-bootstrapper pp11.5.30-bootstrapper pp12.0.18-bootstrapper procinfo procmail procps psa-atmail psa-autoinstaller psa-courier-authlib
  psa-courier-imap psa-libxml-proxy psa-logrotate psa-mail-driver-common psa-migration-agents psa-migration-manager psa-mod-fcgid-configurator psa-php5-configurator
  psa-phpmyadmin psa-phppgadmin psa-proftpd psa-pylibplesk psa-spamassassin psa-spf2 psa-updates psa-vhost psa-vps-optimized psfontmgr psmisc psutils pwgen python python-apt
  python-cairo python-central python-gnupginterface python-gobject python-gtk2 python-libxml2 python-minimal python-newt python-support python2.6 python2.6-minimal quota
  readline-common release-upgrader-python-apt rsync samba samba-common samba-common-bin sasl2-bin screen sed sendmail-base sendmail-cf sensible-mda shared-mime-info sharutils
  shtool smbfs snmp spamassassin spamc sqlite3 ssl-cert subversion sudo suphp-common sw-cp-server sw-engine sw-libboost-date-time1.54.0 sw-libboost-filesystem1.54.0
  sw-libboost-program-options1.54.0 sw-libboost-regex1.54.0 sw-libboost-serialization1.54.0 sw-libboost-system1.54.0 sw-libboost-thread1.54.0 sw-libmilter sw-libpoco
  sw-libsqlite3-0 sw-mariadb-client sw-rsync sysklogd syslinux sysv-rc sysvinit-utils sysvutils tar tcpd tcpdump tcsh telnet testdisk tofrodos traceroute tzdata ucf udev
  unixodbc unzip update-inetd update-manager-core update-notifier-common upstart util-linux uuid-runtime vim vim-common vim-runtime webalizer wget whiptail whois
  wide-dhcpv6-client wpb-core wpb-headers x11-common xinetd xsltproc zip zlib1g zlib1g-dev
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libc6 (due to apt) libgcc1 (due to apt) libstdc++6 (due to apt) base-files base-passwd (due to base-files) libpam-modules (due to base-files) bash debianutils (due to
  bash) dash (due to bash) libncurses5 (due to bash) bsdutils coreutils libacl1 (due to coreutils) libattr1 (due to coreutils) libselinux1 (due to coreutils) diffutils dpkg
  lzma (due to dpkg) e2fsprogs e2fslibs (due to e2fsprogs) libblkid1 (due to e2fsprogs) libcomerr2 (due to e2fsprogs) libss2 (due to e2fsprogs) libuuid1 (due to e2fsprogs)
  util-linux (due to e2fsprogs) findutils grep gzip hostname upstart (due to hostname) login libpam0g (due to login) libpam-runtime (due to login) mount libsepol1 (due to
  mount) ncurses-base ncurses-bin perl-base python-minimal python2.6-minimal (due to python-minimal) sed install-info (due to sed) tar lsb-base (due to util-linux) tzdata
  (due to util-linux) libslang2 (due to util-linux) zlib1g (due to util-linux)
0 upgraded, 0 newly installed, 542 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 1,393MB disk space will be freed.
You are about to do something potentially harmful
To continue type in the phrase &#8216;Yes, do as I say!&#8217;
 ?] n
Abort.

```

---

### Post by grahammechanical on 2016-08-29
Support for Ubuntu 12.04 ends at the end of April 2017. So, if you do succeed in doing an online upgrade to 12.04 (the next supported version from 10.04) you will have to repeat the process again in less than a year and move on to 14.04.

You should think about backing up your data and doing a fresh install of 14.04 or 16.04. You also need to consider if your hardware can run Ubuntu 14.04 or 16.04 which both have the Unity user interface. Unity requires a video adapter that can do hardware accelerated 3D rendering and that also has a sizable chunk of its own video memory.

You might have to use Xubuntu, Lubuntu or Ubuntu Mate to keep that  hardware in service. And that would require a fresh install anyway.

Prior to doing an online upgrade to another release of Ubuntu we should switch the video driver to the open source video driver; disable any PPAs and revert the desktop to as close as default as possible. Upgrading with a heavily modified user interface will increase the risk of the upgrade breaking in some way. Just so you know in case you decide to continue with this experiment.

Regards

---

### Post by JAY6390 on 2016-08-29
Hi Graham

Thanks for the reply. Yeah I was planning on upgrading to a more recent version, however this is a VPS server (I should have mentioned that!) with sites running and don't really want to clear and re-install everything as it has Plesk to deal with too. There's no issue with unity/desktop as I don't have a GUI. I'm debating trying to fix this locally on a VM. Is there any way to create an ISO of the server and load that into VM ware do you know?

Kind regards
Jay

---

