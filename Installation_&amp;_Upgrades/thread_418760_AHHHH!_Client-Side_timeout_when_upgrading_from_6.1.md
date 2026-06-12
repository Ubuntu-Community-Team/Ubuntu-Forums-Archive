---
title: "AHHHH! Client-Side timeout when upgrading from 6.1 to Feisty"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by hothgremlin on 2007-04-22
Dear community!

I tried to upgrade to Feisty today but my client's internet connection broke down (ssh only access to server).
When i now try to restart the script  do-release-upgrade he stops saying "No new release found".

The connection broke when he was waiting for input concerning some configs....

what am i supposed to do now?

with best regards,
hg a wg


PS: the following upgrade relevant processes are still running:

/usr/bin/python /tmp/tmpg29-Ia/feisty --mode=server --frontend=DistUpgradeViewText

root     25695  0.0  4.1  58500 41920 pts/0    S+   20:08   0:00 /usr/bin/python /tmp/tmpg29-Ia/feisty --mode=server --frontend=DistUpgradeViewText

/usr/bin/dpkg --status-fd 37 --configure linux-libc-dev libc6-dev libc6-i686 belocs-locales-bin locales libapr1 libdb4.4 libexpat1 libgpg-error0 libgcrypt11 zlib1g-dev libopencdk8 libtasn1-3 libgnutls13 libmysqlclient15off libdb4.2 libssl0.9.8 libsasl2-modules libkrb53 libpq5 libsqlite0 libsasl2-modules-sql libsasl2-2 ifupdown iputils-ping update-inetd netbase postfix postfix-mysql perl perl-modules libsasl2 libldap2 libsqlite3-0 libaprutil1 libpcre3 mime-support libbz2-1.0 libncursesw5 readline-common libreadline5 python2.5 python lsb-release python-central bzip2 python-support bittornado libfreetype6 ucf ttf-dejavu fontconfig-config libfontconfig1 libpng12-0 libxau6 libxdmcp6 libx11-data libx11-6 libxpm4 libgd2-xpm libxml2 apache2-utils libmagic1 apache2.2-common apache2-mpm-prefork php5-common libapache2-mod-php5 php5-gd php5-mysql php5 libphp-adodb dbconfig-common torrentflux phpmyadmin file libnewt0.52 libpopt0 whiptail libconsole console-tools console-common libice6 libsm6 libxt6 libvolume-id0 libklibc klibc-utils busybox-initramfs module-init-tools procps udev initramfs-tools volumeid lvm-common lvm2 libdbi-perl libdbd-mysql-perl libwrap0 mysql-client-5.0 psmisc mysql-server-5.0 mysql-server mysql-client cpp-4.1 binutils gcc-4.1 libstdc++6-4.1-dev g++-4.1 screen vim-common vim-runtime libgpmg1 vim apt-utils python-apt libsigc++-2.0-0c2a aptitude python2.4 dhcp3-common dhcp3-client eject ethtool gettext-base gpgv makedev gnupg iproute klogd sysklogd less libasound2 libdbus-1-3 libfribidi0 libiw28 libpci2 pciutils libsysfs2 ntpdate pcmciautils usbutils wireless-tools wpasupplicant at libisc11 libdns22 libisccc0 libisccfg1 libbind9-0 liblwres9 bind9-host bsdmainutils cron dnsutils dosfstools dselect fdutils hdparm info iptables iputils-arping iputils-tracepath libgc1c2 libparted1.7-1 libpcap0.8 man-db manpages nano openssh-client openssh-server parted popularity-contest ppp pppconfig pppoeconf reiserfsprogs rsync strace tcpdump telnet update-manager-core w3m wget m4 autoconf autotools-dev automake1.4 binutils-static tcl8.4 expect courier-authlib courier-authdaemon courier-authlib-mysql courier-authlib-userdb libfam0 courier-base courier-pop openssl courier-ssl courier-pop-ssl cpp make dpkg-dev libevms-2.5 evms evms-ncurses gcc g++ gcc-3.3-base gettext hwdata libxext6 libmagick9 imagemagick installation-report intltool-debian jfsutils libneon26 libsvn1 libapache2-svn libasn1-6-heimdal libcupsys2 libidn11 libgsasl7 libroken16-heimdal libkrb5-17-heimdal libgssapi4-heimdal libneon25 libpq4 libslp1 libstdc++5 mbr lilo linux-image-2.6.20-15-server linux-image-server linux-restricted-modules-common lynx mdadm mutt ntp ntp-simple p7zip p7zip-full po-debconf postfix-doc rar reiser4progs reportbug sasl2-bin squirrelmail ssh subversion tcpd unzip websvn xfsprogs courier-imap courier-imap-ssl libgd-gd2-perl netatalk vsftpd

---

### Post by hothgremlin on 2007-04-22
Ok, great, I now tried a manual dist-upgrade.. the server rebooted but had problems installing those two packages
```

linux-image-2.6.20-15-server
linux-image-server

```
that seem quite important to me :/. Here is the errorcode:
```
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-15-server
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: error processing linux-image-2.6.20-15-server (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-2.6.20-15-server; however:
  Package linux-image-2.6.20-15-server is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.20-15-server
 linux-image-server
```

it may has to do sth with the mdadm.conf (looking at the warnings) but i really can't say.. btw: i do not even have a RAID!!!

hoping for help!

greetinx,
hg a wg

---

