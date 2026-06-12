---
title: "problem to upgrade from 20.04 to 22.04"
date: 2023-01-22
forum: Installation &amp; Upgrades
---

### Post by luigello2010 on 2023-01-22
Hi

i want to upgrade my ubuntu to 22.04

```
New release '22.04.1 LTS' available.Run 'do-release-upgrade' to upgrade to it.

```

if i run 'do-release-upgrade' i got follow in the console:

```
root@cloud615557:~# do-release-upgradeChecking for a new Ubuntu release
Please install all available updates for your release before upgrading.

```


no i run this command [COLOR=#000000][FONT=&quot]sudo apt update && sudo apt dist-upgrade[/FONT][/COLOR]
```
root@cloud615557:~# sudo apt update && sudo apt dist-upgrade
Get:1 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Hit:2 http://archive.ubuntu.com/ubuntu focal InRelease
Get:3 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:4 http://archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]
Fetched 336 kB in 1s (284 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 bsd-mailx : Depends: default-mta or
                      mail-transport-agent
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```


no i try  'apt --fix-broken install' :

```
root@cloud615557:~# apt --fix-broken install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre postfix-lmdb
  postfix-sqlite sasl2-bin | dovecot-common resolvconf postfix-cdb postfix-doc
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 0 B/1,201 kB of archives.
After this operation, 4,577 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
debconf: Perl may be unconfigured (Symbol.pm did not return a true value at /usr/lib/x86_64-linux-gnu/perl/5.30/IO/File.pm line 130.
BEGIN failed--compilation aborted at /usr/lib/x86_64-linux-gnu/perl/5.30/IO/File.pm line 130.
Compilation failed in require at /usr/share/perl/5.30/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
dpkg: warning: files list file for package 'libctf0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-pkg-resources' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-ubuntu-console' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-entrypoints' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cryptsetup-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-distutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libip4tc2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libksba8:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pinentry-curses' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'logrotate' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libexpat1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bash' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cpio' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-pam' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'powermgmt-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpipeline1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'networkd-dispatcher' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblmdb0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gsettings-desktop-schemas' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtext-iconv-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-more-itertools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-modules-extra-5.4.0-137-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'distro-info' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'snapd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'packagekit-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'byobu' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gcc-9' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bcache-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'glib-networking-services' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtext-charwidth-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fuse' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-attr' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lsb-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libzstd1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcanberra0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'manpages-dev' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'openssh-sftp-server' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'zerofree' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'tcpdump' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-image-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'systemd-sysv' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxau6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'net-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxdmcp6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'time' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'adduser' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-dbus' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkeyutils1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'console-setup' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'eatmydata' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libapparmor1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libproxy1v5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libncurses-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pci.ids' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpsl5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxcb1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython3.8-minimal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apt' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnewt0.52:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libreadline5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'vim' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apt-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgpm2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gpg-agent' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libogg0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'irqbalance' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'telnet' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblockfile-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'perl-modules-5.30' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mime-support' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsoup2.4-1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-importlib-metadata' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'initramfs-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdevmapper-event1.02.1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-setuptools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-modules:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-distro' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'wget' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libstdc++-9-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libplist3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bsdutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gpg-wks-client' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grep' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblzma5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'openssh-server' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgpg-error0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dconf-gsettings-backend:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'init' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libqrencode4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'squashfs-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhogweed5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cryptsetup' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-minimal' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xdg-user-dirs' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bind9-libs:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iucode-tool' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxmlsec1-openssl:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libargon2-0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-jwt' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'alsa-ucm-conf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'tar' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmagic-mgc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-google-authenticator' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfile-fcntllock-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-colorama' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'at' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-firmware' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gawk' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libarchive13:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-gdbm:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'psmisc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'plymouth' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-zope.interface' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libalgorithm-diff-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub2-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libyaml-0-2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgcc1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-problem-report' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iptables' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libip6tc2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libglib2.0-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'distro-info-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdns-export1109' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'manpages' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-apt' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblz4-1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'htop' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-legacy-ec2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iproute2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lxcfs' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libicu66:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'openssh-client' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libestr0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'update-notifier-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-openssl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfastjson4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ssh-import-id' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtdb1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libssl1.1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'intel-microcode' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhx509-5-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmaxminddb0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libargon2-1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'popularity-contest' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-launchpadlib' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'uidmap' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-jsonpatch' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'btrfs-progs' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libasn1-8-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libutf8proc2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libbrotli1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libedit2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-modules-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libreadline8:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'wireless-regdb' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libc-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsqlite3-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-automat' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gpgsm' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-debconf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cron' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsasl2-modules:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ltrace' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ncurses-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmspack0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dosfstools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libffi7:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'rsyslog' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'subversion' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'netcat-openbsd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-modules-extra-4.15.0-202-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libusb-1.0-doc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libacl1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libserf-1-1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'binutils-common:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-twisted-bin:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'upower' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnghttp2-14:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmagic1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libunistring2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsmartcols1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libapr1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'less' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxext6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-libc-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libglib2.0-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'isc-dhcp-client' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libctf-nobfd0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libldap-2.4-2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnetplan0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gettext-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libusb-1.0-0-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpackagekit-glib2-18:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblxc-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgcrypt20:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'parted' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnss-systemd:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pastebinit' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'screen' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xkb-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblxc1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-yaml' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblzo2-2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'debconf-i18n' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libntfs-3g883' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnftnl11:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'coreutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'e2fsprogs' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcurl3-gnutls:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libefiboot1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'zlib1g:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-hamcrest' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnpth0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcrypt1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'hdparm' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dconf-service' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ufw' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-lazr.uri' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'systemd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'krb5-locales' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libidn2-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcom-err2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'binutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'file' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaprutil1-ldap:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lxd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'acpid' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'vim-tiny' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libusb-dev' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dnsutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'kmod' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libassuan0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dnsmasq-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-standard' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-zipp' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgomp1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-click' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'diffutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfuse2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcbor0.6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libatm1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lshw' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apache2-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-newt:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bzip2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'amd64-microcode' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-distupgrade' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'locales' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'landscape-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaprutil1-dbd-sqlite3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libldap-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'man-db' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libappstream4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libunwind8:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-markupsafe' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-keyring' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaudit-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgcc-s1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libncurses5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtext-wrapi18n-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhcrypto4-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-pc-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'finalrd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apport-symptoms' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsemanage-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'open-iscsi' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libheimntlm0-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'usbutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lvm2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libseccomp2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'software-properties-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xxd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ntfs-3g' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsystemd0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcap2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apport' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fdisk' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'debconf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfakeroot:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-5.4.0-137-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gcc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dpkg-dev' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libjansson4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libusb-0.1-4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-apport' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'netplan.io' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'acl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkrb5support0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dns-root-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsasl2-modules-db:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-serial' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'tzdata' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcap2-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fakeroot' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liberror-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdconf1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'eject' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-pc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-requests-unixsocket' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-six' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-simplejson' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgcc-9-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libasound2-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apparmor' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gdisk' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'perl-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libselinux1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dirmngr' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ca-certificates' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libvorbisfile3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'hostname' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-packagekitglib-1.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dbus-user-session' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libklibc:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libasan5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gcc-10-base:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpcre3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcap-ng0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'unattended-upgrades' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwind0-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-jinja2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libisc-export1105:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ncurses-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'plymouth-theme-ubuntu-text' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libglib2.0-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnutls30:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libext2fs2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-oauthlib' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libuv1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-chardet' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'os-prober' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam0g:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-configobj' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'vim-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cryptsetup-run' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pollinate' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libslang2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgssapi3-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-secretstorage' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-gfxpayload-lists' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'busybox-static' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfreetype6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-software-properties' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpcap0.8:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwrap0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-certifi' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mtr-tiny' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libx11-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'make' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmpfr6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lxd-client' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnupg-l10n' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-jsonschema' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ssl-cert' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ed' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dialog' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'librtmp1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'command-not-found' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libapt-pkg6.0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libidn11:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdbus-glib-1-2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-pexpect' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bash-completion' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libiptc0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-pyasn1-modules' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-twisted' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ifupdown' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ebtables' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgmp10:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-cryptography' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'friendly-recovery' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython3.8:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'init-system-helpers' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libncurses6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'strace' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-incremental' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-wadllib' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-debian' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdbus-1-3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dbus' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsigsegv2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xz-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-gi' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfribidi0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sed' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libquadmath0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'shared-mime-info' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-requests' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libp11-kit0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-commandnotfound' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaudit1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-hyperlink' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bsdmainutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-service-identity' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libssl-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpng16-16:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblvm2cmd2.03:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmpc3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gzip' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmnl0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'thin-provisioning-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'systemd-timesyncd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libatomic1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgssapi-krb5-2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libvorbis0a:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'udev' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libuuid1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-idna' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libevent-2.1-7:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'patch' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libss2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gcc-8-base:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'usb.ids' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-release-upgrader-core' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ftp' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sudo' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xfsprogs' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgdbm-compat4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'util-linux' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfl2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ucf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'git' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-glib-2.0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpcre2-8-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'g++-9' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'usbmuxd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libncursesw6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libk5crypto3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pciutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'busybox-initramfs' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxtables12:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libltdl7:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdpkg-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'logsave' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsasl2-2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libssh-4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dpkg' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libroken18-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lsof' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lz4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libc6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sosreport' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-urllib3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'update-manager-core' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfdisk1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdumbnet1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gpg-wks-server' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-netifaces' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libudev1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libutempter0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libubsan1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsepol1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'nano' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpci3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdevmapper1.02.1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnuma1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libparted2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-pyrsistent:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdrm2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'g++' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-image-5.4.0-137-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'whiptail' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'alsa-topology-conf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-apt-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnettle7:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3.8-minimal' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'passwd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libisns0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'findutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mount' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblua5.2-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dmsetup' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sound-theme-freedesktop' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'open-vm-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sensible-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'uuid-runtime' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dmeventd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xauth' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnetfilter-conntrack3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'groff-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-json-pointer' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libusbmuxd6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-update-manager' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'librhash0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xdelta3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gpgv' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcrypt-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmount1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnfnetlink0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cpp' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libplymouth5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libuchardet0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'procps' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-5.4.0-137' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libeatmydata1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnl-genl-3-200:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libattr1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libasound2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxslt1.1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnl-3-200:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-modules-4.15.0-202-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gpgconf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgeoip1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sysvinit-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnupg' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-pyasn1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-keyring' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtasn1-6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-httplib2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-systemd:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libupower-glib3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cmake' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'language-selector-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libefivar1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'build-essential' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cpp-9' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libperl5.30:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcurl4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpolkit-agent-1-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libc6-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'git-man' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libx11-6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcryptsetup12:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'packagekit' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libisl22:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgirepository-1.0-1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'kbd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-image-4.15.0-202-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'netbase' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-constantly' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'console-setup-linux' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-minimal' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'isc-dhcp-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cmake-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'debianutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mawk' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mlocate' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkrb5-3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblockfile1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'curl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-advantage-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libusb-1.0-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libstemmer0d:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bind9-dnsutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'glib-networking:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmpdec2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'keyboard-configuration' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libjson-c4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dmidecode' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libncursesw5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaccountsservice0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'install-info' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'glib-networking-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdebconfclient0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'base-files' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libbinutils:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'vim-runtime' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lsb-release' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxmlsec1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython3.8-stdlib:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'geoip-database' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iw' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfido2-1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaio1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'initramfs-tools-core' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsvn1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libbz2-1.0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libc-dev-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3.8' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'klibc-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsemanage1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-lazr.restfulclient' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libimobiledevice6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bind9-host' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'openssl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libbsd0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgpg-error-l10n' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtinfo5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-lib2to3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cloud-guest-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-modules-5.4.0-137-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdrm-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libelf1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-cap:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'run-one' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'thermald' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-distro-info' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'base-passwd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libalgorithm-diff-xs-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'overlayroot' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iputils-ping' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libevdev2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'crda' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'readline-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-runtime' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdb5.3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-asn1crypto' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'publicsuffix' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxml2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'policykit-1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'tmux' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcc1-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libblkid1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iso-codes' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libstdc++6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxmuu1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'info' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblocale-gettext-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'accountsservice' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cryptsetup-initramfs' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gpg' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgudev-1.0-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpolkit-gobject-1-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblsan0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libprocps8:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dash' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iputils-tracepath' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgstreamer1.0-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mdadm' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libitm1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'rsync' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-systemd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-cffi-backend' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libjsoncpp1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkmod2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython3-stdlib:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libheimbase1-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgdbm6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtinfo6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpopt0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gcc-9-base:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ethtool' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libalgorithm-merge-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnupg-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'binutils-x86-64-linux-gnu' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-ptyprocess' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'initramfs-tools-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ncurses-term' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaprutil1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'login' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtsan0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-blinker' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkrb5-26-heimdal:amd64' missing; assuming package has no files currently installed
(Reading database ... 36 files and directories currently installed.)
Preparing to unpack .../postfix_3.4.13-0ubuntu1.2_amd64.deb ...
base.pm did not return a true value at /usr/share/perl5/Debconf/Log.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Log.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing archive /var/cache/apt/archives/postfix_3.4.13-0ubuntu1.2_amd64.deb (--unpack):
 new postfix package pre-installation script subprocess returned error exit status 255
Errors were encountered while processing:
 /var/cache/apt/archives/postfix_3.4.13-0ubuntu1.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


what is the problem ? can anyone help to sort it out ?

thanks a lot

---

### Post by ajgreeny on 2023-01-22
I'm using Android at the moment so no easy way to check this but you must run the **do-release-upgrade** command as sudo just the same as **sudo apt update** and it looks as if you omitted the sudo.

Also bear in mind that the **sudo apt dist-upgrade** command you used does not move you from one version to the next as you may have imagined.

The command i use for normal upgrades is **sudo apt full-upgrade** but as I'm not on Linux at the moment I will leave you to search for any differences between the **dist** and **full** upgrade commands; I think they may be important for your situation

---

### Post by luigello2010 on 2023-01-22
Hi

thanks for your answer!

```
root@cloud615557:~# sudo apt full-upgradeReading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 bsd-mailx : Depends: default-mta or
                      mail-transport-agent
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```



```

root@cloud615557:~# apt --fix-broken install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre postfix-lmdb
  postfix-sqlite sasl2-bin | dovecot-common resolvconf postfix-cdb postfix-doc
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 0 B/1,201 kB of archives.
After this operation, 4,577 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
debconf: Perl may be unconfigured (Symbol.pm did not return a true value at /usr/lib/x86_64-linux-gnu/perl/5.30/IO/File.pm line 130.
BEGIN failed--compilation aborted at /usr/lib/x86_64-linux-gnu/perl/5.30/IO/File.pm line 130.
Compilation failed in require at /usr/share/perl/5.30/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
dpkg: warning: files list file for package 'libctf0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-pkg-resources' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-ubuntu-console' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-entrypoints' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cryptsetup-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-distutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libip4tc2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libksba8:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pinentry-curses' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'logrotate' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libexpat1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bash' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cpio' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-pam' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'powermgmt-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpipeline1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'networkd-dispatcher' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblmdb0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gsettings-desktop-schemas' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtext-iconv-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-more-itertools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-modules-extra-5.4.0-137-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'distro-info' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'snapd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'packagekit-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'byobu' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gcc-9' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bcache-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'glib-networking-services' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtext-charwidth-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fuse' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-attr' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lsb-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libzstd1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcanberra0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'manpages-dev' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'openssh-sftp-server' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'zerofree' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'tcpdump' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-image-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'systemd-sysv' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxau6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'net-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxdmcp6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'time' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'adduser' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-dbus' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkeyutils1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'console-setup' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'eatmydata' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libapparmor1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libproxy1v5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libncurses-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pci.ids' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpsl5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxcb1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython3.8-minimal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apt' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnewt0.52:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libreadline5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'vim' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apt-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgpm2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gpg-agent' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libogg0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'irqbalance' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'telnet' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblockfile-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'perl-modules-5.30' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mime-support' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsoup2.4-1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-importlib-metadata' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'initramfs-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdevmapper-event1.02.1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-setuptools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-modules:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-distro' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'wget' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libstdc++-9-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libplist3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bsdutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gpg-wks-client' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grep' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblzma5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'openssh-server' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgpg-error0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dconf-gsettings-backend:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'init' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libqrencode4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'squashfs-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhogweed5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cryptsetup' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-minimal' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xdg-user-dirs' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bind9-libs:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iucode-tool' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxmlsec1-openssl:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libargon2-0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-jwt' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'alsa-ucm-conf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'tar' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmagic-mgc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-google-authenticator' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfile-fcntllock-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-colorama' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'at' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-firmware' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gawk' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libarchive13:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-gdbm:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'psmisc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'plymouth' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-zope.interface' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libalgorithm-diff-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub2-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libyaml-0-2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgcc1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-problem-report' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iptables' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libip6tc2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libglib2.0-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'distro-info-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdns-export1109' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'manpages' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-apt' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblz4-1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'htop' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-legacy-ec2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iproute2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lxcfs' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libicu66:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'openssh-client' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libestr0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'update-notifier-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-openssl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfastjson4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ssh-import-id' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtdb1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libssl1.1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'intel-microcode' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhx509-5-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmaxminddb0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libargon2-1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'popularity-contest' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-launchpadlib' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'uidmap' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-jsonpatch' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'btrfs-progs' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libasn1-8-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libutf8proc2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libbrotli1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libedit2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-modules-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libreadline8:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'wireless-regdb' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libc-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsqlite3-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-automat' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gpgsm' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-debconf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cron' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsasl2-modules:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ltrace' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ncurses-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmspack0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dosfstools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libffi7:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'rsyslog' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'subversion' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'netcat-openbsd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-modules-extra-4.15.0-202-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libusb-1.0-doc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libacl1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libserf-1-1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'binutils-common:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-twisted-bin:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'upower' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnghttp2-14:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmagic1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libunistring2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsmartcols1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libapr1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'less' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxext6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-libc-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libglib2.0-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'isc-dhcp-client' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libctf-nobfd0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libldap-2.4-2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnetplan0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gettext-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libusb-1.0-0-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpackagekit-glib2-18:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblxc-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgcrypt20:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'parted' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnss-systemd:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pastebinit' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'screen' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xkb-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblxc1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-yaml' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblzo2-2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'debconf-i18n' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libntfs-3g883' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnftnl11:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'coreutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'e2fsprogs' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcurl3-gnutls:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libefiboot1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'zlib1g:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-hamcrest' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnpth0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcrypt1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'hdparm' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dconf-service' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ufw' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-lazr.uri' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'systemd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'krb5-locales' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libidn2-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcom-err2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'binutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'file' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaprutil1-ldap:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lxd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'acpid' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'vim-tiny' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libusb-dev' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dnsutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'kmod' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libassuan0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dnsmasq-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-standard' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-zipp' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgomp1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-click' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'diffutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfuse2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcbor0.6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libatm1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lshw' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apache2-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-newt:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bzip2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'amd64-microcode' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-distupgrade' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'locales' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'landscape-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaprutil1-dbd-sqlite3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libldap-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'man-db' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libappstream4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libunwind8:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-markupsafe' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-keyring' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaudit-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgcc-s1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libncurses5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtext-wrapi18n-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhcrypto4-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-pc-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'finalrd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apport-symptoms' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsemanage-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'open-iscsi' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libheimntlm0-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'usbutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lvm2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libseccomp2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'software-properties-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xxd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ntfs-3g' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsystemd0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcap2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apport' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fdisk' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'debconf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfakeroot:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-5.4.0-137-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gcc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dpkg-dev' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libjansson4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libusb-0.1-4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-apport' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'netplan.io' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'acl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkrb5support0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dns-root-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsasl2-modules-db:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-serial' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'tzdata' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcap2-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fakeroot' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liberror-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdconf1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'eject' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-pc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-requests-unixsocket' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-six' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-simplejson' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgcc-9-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libasound2-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apparmor' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gdisk' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'perl-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libselinux1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dirmngr' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ca-certificates' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libvorbisfile3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'hostname' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-packagekitglib-1.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dbus-user-session' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libklibc:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libasan5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gcc-10-base:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpcre3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcap-ng0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'unattended-upgrades' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwind0-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-jinja2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libisc-export1105:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ncurses-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'plymouth-theme-ubuntu-text' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libglib2.0-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnutls30:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libext2fs2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-oauthlib' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libuv1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-chardet' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'os-prober' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam0g:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-configobj' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'vim-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cryptsetup-run' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pollinate' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libslang2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgssapi3-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-secretstorage' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-gfxpayload-lists' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'busybox-static' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfreetype6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-software-properties' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpcap0.8:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwrap0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-certifi' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mtr-tiny' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libx11-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'make' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmpfr6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lxd-client' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnupg-l10n' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-jsonschema' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ssl-cert' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ed' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dialog' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'librtmp1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'command-not-found' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libapt-pkg6.0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libidn11:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdbus-glib-1-2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-pexpect' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bash-completion' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libiptc0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-pyasn1-modules' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-twisted' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ifupdown' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ebtables' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgmp10:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-cryptography' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'friendly-recovery' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython3.8:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'init-system-helpers' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libncurses6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'strace' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-incremental' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-wadllib' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-debian' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdbus-1-3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dbus' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsigsegv2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xz-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-gi' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfribidi0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sed' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libquadmath0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'shared-mime-info' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-requests' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libp11-kit0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-commandnotfound' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaudit1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-hyperlink' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bsdmainutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-service-identity' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libssl-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpng16-16:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblvm2cmd2.03:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmpc3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gzip' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmnl0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'thin-provisioning-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'systemd-timesyncd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libatomic1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgssapi-krb5-2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libvorbis0a:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'udev' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libuuid1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-idna' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libevent-2.1-7:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'patch' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libss2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gcc-8-base:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'usb.ids' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-release-upgrader-core' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ftp' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sudo' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xfsprogs' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgdbm-compat4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'util-linux' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfl2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ucf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'git' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-glib-2.0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpcre2-8-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'g++-9' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'usbmuxd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libncursesw6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libk5crypto3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pciutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'busybox-initramfs' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxtables12:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libltdl7:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdpkg-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'logsave' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsasl2-2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libssh-4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dpkg' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libroken18-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lsof' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lz4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libc6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sosreport' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-urllib3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'update-manager-core' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfdisk1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdumbnet1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gpg-wks-server' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-netifaces' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libudev1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libutempter0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libubsan1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsepol1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'nano' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpci3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdevmapper1.02.1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnuma1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libparted2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-pyrsistent:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdrm2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'g++' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-image-5.4.0-137-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'whiptail' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'alsa-topology-conf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-apt-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnettle7:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3.8-minimal' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'passwd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libisns0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'findutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mount' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblua5.2-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dmsetup' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sound-theme-freedesktop' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'open-vm-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sensible-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'uuid-runtime' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dmeventd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xauth' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnetfilter-conntrack3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'groff-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-json-pointer' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libusbmuxd6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-update-manager' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'librhash0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xdelta3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gpgv' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcrypt-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmount1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnfnetlink0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cpp' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libplymouth5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libuchardet0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'procps' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-5.4.0-137' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libeatmydata1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnl-genl-3-200:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libattr1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libasound2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxslt1.1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnl-3-200:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-modules-4.15.0-202-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gpgconf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgeoip1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sysvinit-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnupg' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-pyasn1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-keyring' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtasn1-6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-httplib2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-systemd:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libupower-glib3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cmake' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'language-selector-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libefivar1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'build-essential' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cpp-9' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libperl5.30:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcurl4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpolkit-agent-1-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libc6-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'git-man' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libx11-6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcryptsetup12:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'packagekit' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libisl22:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgirepository-1.0-1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'kbd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-image-4.15.0-202-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'netbase' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-constantly' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'console-setup-linux' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-minimal' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'isc-dhcp-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cmake-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'debianutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mawk' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mlocate' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkrb5-3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblockfile1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'curl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-advantage-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libusb-1.0-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libstemmer0d:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bind9-dnsutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'glib-networking:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmpdec2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'keyboard-configuration' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libjson-c4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dmidecode' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libncursesw5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaccountsservice0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'install-info' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'glib-networking-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdebconfclient0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'base-files' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libbinutils:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'vim-runtime' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lsb-release' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxmlsec1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython3.8-stdlib:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'geoip-database' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iw' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfido2-1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaio1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'initramfs-tools-core' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsvn1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libbz2-1.0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libc-dev-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3.8' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'klibc-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsemanage1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-lazr.restfulclient' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libimobiledevice6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bind9-host' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'openssl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libbsd0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgpg-error-l10n' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtinfo5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-lib2to3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cloud-guest-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-modules-5.4.0-137-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdrm-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libelf1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-cap:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'run-one' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'thermald' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-distro-info' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'base-passwd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libalgorithm-diff-xs-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'overlayroot' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iputils-ping' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libevdev2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'crda' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'readline-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-runtime' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdb5.3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-asn1crypto' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'publicsuffix' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxml2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'policykit-1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'tmux' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcc1-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libblkid1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iso-codes' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libstdc++6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxmuu1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'info' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblocale-gettext-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'accountsservice' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cryptsetup-initramfs' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gpg' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgudev-1.0-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpolkit-gobject-1-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblsan0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libprocps8:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dash' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iputils-tracepath' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgstreamer1.0-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mdadm' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libitm1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'rsync' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-systemd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-cffi-backend' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libjsoncpp1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkmod2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython3-stdlib:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libheimbase1-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgdbm6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtinfo6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpopt0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gcc-9-base:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ethtool' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libalgorithm-merge-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnupg-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'binutils-x86-64-linux-gnu' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-ptyprocess' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'initramfs-tools-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ncurses-term' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaprutil1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'login' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtsan0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-blinker' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkrb5-26-heimdal:amd64' missing; assuming package has no files currently installed
(Reading database ... 36 files and directories currently installed.)
Preparing to unpack .../postfix_3.4.13-0ubuntu1.2_amd64.deb ...
base.pm did not return a true value at /usr/share/perl5/Debconf/Log.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Log.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing archive /var/cache/apt/archives/postfix_3.4.13-0ubuntu1.2_amd64.deb (--unpack):
 new postfix package pre-installation script subprocess returned error exit status 255
Errors were encountered while processing:
 /var/cache/apt/archives/postfix_3.4.13-0ubuntu1.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


this i got with your commands

---

### Post by ajgreeny on 2023-01-22
Just as a check, can you confirm that before running any of these **apt upgrade** commands, you have also run the **sudo apt update** command.

You seem to be lacking list data for a huge number of packages. The **update** command may solve that.

---

### Post by luigello2010 on 2023-01-22
yes thats my result:

```

root@cloud615557:~# sudo apt updateGet:1 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Hit:2 http://archive.ubuntu.com/ubuntu focal InRelease
Get:3 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:4 http://archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]
Fetched 336 kB in 1s (375 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
root@cloud615557:~# apt list --upgradable
Listing... Done
git-man/focal-updates,focal-security 1:2.25.1-1ubuntu3.8 all [upgradable from: 1:2.25.1-1ubuntu3.7]
git/focal-updates,focal-security 1:2.25.1-1ubuntu3.8 amd64 [upgradable from: 1:2.25.1-1ubuntu3.7]



```

---

### Post by grahammechanical on 2023-01-22
This package seems to be the problem.

> The following packages have unmet dependencies: bsd-mailx : Depends: default-mta or
                      mail-transport-agent

[https://packages.ubuntu.com/focal/bsd-mailx](https://packages.ubuntu.com/focal/bsd-mailx)

You could try uninstalling it and then re-installing

Regards

---

### Post by Impavidus on 2023-01-22
There's a huge list of packages for which the file list is missing. apt update would fix apt's information on available packages, but this missing information is related to the currently installed packages. Somehow, apt's database was damaged. Inappropriate file deletion, filesystem damage, hard drive damage, I can't say what caused it. To fix the database, all those packages have to be reinstalled. And your perl is damaged and that's required to make the package manager run. You could try to fix it from a live disk, but I think that's too much work, just to enable a release upgrade. Simply install the new release from a live disk.

BTW, you've got back-ups, haven't you?

---

### Post by luigello2010 on 2023-01-23
hi

now i have this error and i dont have bakups from my system:

```

root@cloud615557:~# sudo apt-get install -fReading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
debconf: Perl may be unconfigured (Symbol.pm did not return a true value at /usr/lib/x86_64-linux-gnu/perl/5.30/IO/File.pm line 130.
BEGIN failed--compilation aborted at /usr/lib/x86_64-linux-gnu/perl/5.30/IO/File.pm line 130.
Compilation failed in require at /usr/share/perl/5.30/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
Setting up debconf (1.5.79ubuntu1) ...
base.pm did not return a true value at /usr/share/perl5/Debconf/Log.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Log.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing package debconf (--configure):
 installed debconf package post-installation script subprocess returned error exit status 255
Errors were encountered while processing:
 debconf
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by #&amp;thj^% on 2023-01-23
Will this help:
```
sudo dpkg --add-architecture i386 && sudo apt update

```
Also:
```
sudo dpkg --configure -a
```

---

### Post by Impavidus on 2023-01-23
> **luigello2010 said:**
> hi

now i have this error and i dont have bakups from my system:


Then create those backups – of your documents and personal settings; backups of your operating system are useless, as you intend to go the the next LTS release and it's broken already.

This doesn't look like the average messed up package manager and you already planned to move to the next LTS release, so IMHO fixing this isn't worth the effort. Just do a fresh install of 22.04.

---

