---
title: "Upgrading Edgy"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by tsmets on 2006-12-23
Did the change to upgrade to edgy... as indicated [http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

and after doing ```
sudo aptitude update 
sudo aptitude dist-upgrade
```m I received the following warning .



```
The following packages will be upgraded:
  adduser alsa-base alsa-utils apt apt-utils aptitude at base-files
  base-passwd bash bind9-host binutils-static bsdmainutils bsdutils bzip2
  console-common console-data console-tools coreutils cpio cron dash
  db4.2-util debconf debconf-i18n debianutils dhcp3-client dhcp3-common
  diff discover1-data dmidecode dmsetup dnsutils dosfstools dpkg dselect
  e2fslibs e2fsprogs eject ethtool evms evms-ncurses fdutils file findutils
  ftp gcc-4.0-base gettext-base gnupg grep grepmap groff-base grub gzip
  hdparm hostname hwdata ifupdown info initramfs-tools initscripts
  installation-report iproute iptables iputils-arping iputils-ping
  iputils-tracepath klibc-utils klogd language-pack-en
  language-pack-en-base less libacl1 libapr0 libasound2 libattr1 libbind9-0
  libblkid1 libbz2-1.0 libc6 libc6-i686 libcomerr2 libconsole libdb1-compat
  libdb3 libdb4.2 libdb4.3 libdiscover1 libedit2 libelfg0 libevms-2.5
  libexpat1 libfribidi0 libgc1c2 libgcc1 libgcrypt11 libgdbm3 libglib2.0-0
  libgpg-error0 libgpmg1 libisccc0 libisccfg1 libiw28 libklibc libkrb53
  libldap2 liblzo1 libmagic1 libncurses5 libncursesw5 libneon24 libopencdk8
  libpam-modules libpam-runtime libpam0g libpcap0.8 libpcre3 libpopt0
  libpq3 libreadline4 libreadline5 libreiserfs0.3-0 libsasl2
  libsasl2-modules libselinux1 libsigc++-1.2-5c2 libslang2 libss2
  libssl0.9.7 libstdc++6 libsvn0 libtasn1-2 libtext-charwidth-perl
  libtext-iconv-perl libtext-wrapi18n-perl libusb-0.1-4 libuuid1 libwrap0
  libxml2 linux-686 linux-image-686 linux-restricted-modules-686
  linux-restricted-modules-common linux-sound-base locales login logrotate
  lsb-base lsb-release lshw lsof ltrace lvm-common lvm2 makedev manpages
  mawk mc mdadm memtest86+ mii-diag mime-support module-init-tools modutils
  mount mtr-tiny nano ncurses-base ncurses-bin net-tools netbase netcat
  ntpdate nvidia-kernel-common openssh-client openssh-server parted passwd
  patch pciutils pdksh perl-base popularity-contest postgresql
  postgresql-7.4 postgresql-client postgresql-client-7.4 postgresql-common
  ppp pppconfig pppoeconf procps psmisc python python-minimal python2.4
  python2.4-minimal reiser4progs reiserfsprogs reportbug rsync samba
  samba-common sed ssh strace subversion sudo sysklogd sysv-rc tar tcpd
  tcpdump telnet ubuntu-minimal ubuntu-standard udev usbutils util-linux
  vim vim-common w3m wget whiptail wireless-tools xfsprogs zlib1g
227 packages upgraded, 56 newly installed, 7 to remove and 0 not upgraded.
Need to get 132MB of archives. After unpacking 180MB will be used.
Do you want to continue? [Y/n/?] y
The following ESSENTIAL packages will be REMOVED!
  sysvinit

WARNING: Performing this action will probably cause your system to break!
         Do NOT continue unless you know EXACTLY what you are doing!
To continue, type the phrase "I am aware that this is a very bad idea":

Abort.

```

What do I need to do ... ?

\T,

---

### Post by Spin Doctor on 2006-12-24
Try the following which I did to upgrade my 6.06LTS to 6.10. Be aware it is a big download...so I hope you have broadband!

In your commandline, type the following:

```
gksu "update-manager -c" 
```

---

