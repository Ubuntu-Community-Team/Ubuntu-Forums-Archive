---
title: "W: Failure trying to run: chroot /mnt/lfs mount -t proc proc /proc"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by realdreams on 2010-07-22
I am trying to remote install Ubuntu lucid amd64 on Red Hat Enterprise Linux AS release 4 (Nahant Update 5) i386.

Here is the tutorial I am following.

[http://www.underhanded.org/papers/debian-conversion/remotedeb.html](http://www.underhanded.org/papers/debian-conversion/remotedeb.html)


debootstrap (1.0.20ubuntu1)
[http://packages.ubuntu.com/lucid/debootstrap](http://packages.ubuntu.com/lucid/debootstrap)

I use alien_8.81 to convert the deb package to rpm and install it.


[root@localhost mnt]# df -ah
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              18G  3.6G   14G  22% /
none                     0     0     0   -  /proc
none                     0     0     0   -  /sys
none                     0     0     0   -  /dev/pts
/dev/sda1              99M   12M   82M  13% /boot
none                 1014M     0 1014M   0% /dev/shm
none                     0     0     0   -  /proc/sys/fs/binfmt_misc
sunrpc                   0     0     0   -  /var/lib/nfs/rpc_pipefs


I don't know why sda2 doesn't show up.

I did this to mount sda2 to lfs.

# export LFS=/mnt/lfs
# mkdir -p $LFS
# mount /dev/sda5 $LFS
-------------------------------------------------------
fdisk

Command (m for help): p

Disk /dev/sda: 21.4 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14         274     2096482+  83  Linux
/dev/sda3             275        2610    18763920   83  Linux


sda2 was the swap partition and now I use it store ubuntu install files.
-------------------------------------------------------

debootstrap --arch amd64 lucid /mnt/lfs [http://ubuntu.uestc.edu.cn/ubuntu](http://ubuntu.uestc.edu.cn/ubuntu)

[root@localhost mnt]# debootstrap --arch amd64 lucid /mnt/lfs [http://ubun](http://ubun)
I: Retrieving Release
I: Validating Packages
I: Resolving dependencies of required packages...
I: Resolving dependencies of base packages...
I: Checking component main on [http://ubuntu.uestc.edu.cn/ubuntu](http://ubuntu.uestc.edu.cn/ubuntu)...
I: Validating adduser
I: Validating apt
I: Validating apt-utils
I: Validating aptitude
I: Validating base-files
I: Validating base-passwd
I: Validating bash
I: Validating bsdutils
I: Validating busybox-initramfs
I: Validating bzip2
I: Validating ca-certificates
I: Validating console-setup
I: Validating console-terminus
I: Validating coreutils
I: Validating cpio
I: Validating cron
I: Validating dash
I: Validating debconf
I: Validating debconf-i18n
I: Validating debianutils
I: Validating dhcp3-client
I: Validating dhcp3-common
I: Validating diffutils
I: Validating dmidecode
I: Validating dmsetup
I: Validating dpkg
I: Validating e2fslibs
I: Validating e2fsprogs
I: Validating eject
I: Validating file
I: Validating findutils
I: Validating gcc-4.4-base
I: Validating gnupg
I: Validating gnupg-curl
I: Validating gpgv
I: Validating grep
I: Validating gzip
I: Validating hostname
I: Validating ifupdown
I: Validating initramfs-tools
I: Validating initramfs-tools-bin
I: Validating initscripts
I: Validating insserv
I: Validating iproute
I: Validating iputils-ping
I: Validating kbd
I: Validating klibc-utils
I: Validating laptop-detect
I: Validating less
I: Validating libacl1
I: Validating libatm1
I: Validating libattr1
I: Validating libblkid1
I: Validating libbz2-1.0
I: Validating libc-bin
I: Validating libc6
I: Validating libcap2
I: Validating libclass-accessor-perl
I: Validating libcomerr2
I: Validating libcurl3-gnutls
I: Validating libcwidget3
I: Validating libdb4.8
I: Validating libdbus-1-3
I: Validating libdevmapper1.02.1
I: Validating libdrm-intel1
I: Validating libdrm-nouveau1
I: Validating libdrm-radeon1
I: Validating libdrm2
I: Validating libept0
I: Validating libfribidi0
I: Validating libgcc1
I: Validating libgcrypt11
I: Validating libgdbm3
I: Validating libglib2.0-0
I: Validating libgnutls26
I: Validating libgpg-error0
I: Validating libgpm2
I: Validating libgssapi-krb5-2
I: Validating libidn11
I: Validating libio-string-perl
I: Validating libk5crypto3
I: Validating libkeyutils1
I: Validating libklibc
I: Validating libkrb5-3
I: Validating libkrb5support0
I: Validating libldap-2.4-2
I: Validating liblocale-gettext-perl
I: Validating liblockfile1
I: Validating libmagic1
I: Validating libncurses5
I: Validating libncursesw5
I: Validating libnewt0.52
I: Validating libnih-dbus1
I: Validating libnih1
I: Validating libpam-modules
I: Validating libpam-runtime
I: Validating libpam0g
I: Validating libparse-debianchangelog-perl
I: Validating libpcre3
I: Validating libplymouth2
I: Validating libpng12-0
I: Validating libpopt0
I: Validating libreadline6
I: Validating libsasl2-2
I: Validating libsasl2-modules
I: Validating libselinux1
I: Validating libsepol1
I: Validating libsigc++-2.0-0c2a
I: Validating libslang2
I: Validating libsqlite3-0
I: Validating libss2
I: Validating libssl0.9.8
I: Validating libstdc++6
I: Validating libsub-name-perl
I: Validating libtasn1-3
I: Validating libtext-charwidth-perl
I: Validating libtext-iconv-perl
I: Validating libtext-wrapi18n-perl
I: Validating libtimedate-perl
I: Validating libudev0
I: Validating libusb-0.1-4
I: Validating libuuid1
I: Validating libxapian15
I: Validating locales
I: Validating lockfile-progs
I: Validating login
I: Validating logrotate
I: Validating lsb-base
I: Validating lsb-release
I: Validating lzma
I: Validating make
I: Validating makedev
I: Validating mawk
I: Validating mime-support
I: Validating module-init-tools
I: Validating mount
I: Validating mountall
I: Validating ncurses-base
I: Validating ncurses-bin
I: Validating net-tools
I: Validating netbase
I: Validating netcat-openbsd
I: Validating ntpdate
I: Validating openssl
I: Validating passwd
I: Validating perl
I: Validating perl-base
I: Validating perl-modules
I: Validating plymouth
I: Validating procps
I: Validating python
I: Validating python-central
I: Validating python-minimal
I: Validating python2.6
I: Validating python2.6-minimal
I: Validating readline-common
I: Validating rsyslog
I: Validating sed
I: Validating sensible-utils
I: Validating sudo
I: Validating sysv-rc
I: Validating sysvinit-utils
I: Validating tar
I: Validating tasksel
I: Validating tasksel-data
I: Validating tzdata
I: Validating ubuntu-keyring
I: Validating ubuntu-minimal
I: Validating ucf
I: Validating udev
I: Validating upstart
I: Validating ureadahead
I: Validating util-linux
I: Validating vim-common
I: Validating vim-tiny
I: Validating whiptail
I: Validating xkb-data
I: Validating zlib1g
I: Extracting adduser...
I: Extracting base-files...
I: Extracting base-passwd...
I: Extracting bash...
I: Extracting bsdutils...
I: Extracting busybox-initramfs...
I: Extracting coreutils...
I: Extracting cpio...
I: Extracting dash...
I: Extracting debconf...
I: Extracting debconf-i18n...
I: Extracting debianutils...
I: Extracting diffutils...
I: Extracting dpkg...
I: Extracting e2fslibs...
I: Extracting e2fsprogs...
I: Extracting findutils...
I: Extracting gcc-4.4-base...
I: Extracting grep...
I: Extracting gzip...
I: Extracting hostname...
I: Extracting ifupdown...
I: Extracting initramfs-tools...
I: Extracting initramfs-tools-bin...
I: Extracting initscripts...
I: Extracting insserv...
I: Extracting klibc-utils...
I: Extracting libacl1...
I: Extracting libattr1...
I: Extracting libblkid1...
I: Extracting libc-bin...
I: Extracting libc6...
I: Extracting libcomerr2...
I: Extracting libdb4.8...
I: Extracting libdbus-1-3...
I: Extracting libdrm-intel1...
I: Extracting libdrm-nouveau1...
I: Extracting libdrm-radeon1...
I: Extracting libdrm2...
I: Extracting libgcc1...
I: Extracting libglib2.0-0...
I: Extracting libklibc...
I: Extracting liblocale-gettext-perl...
I: Extracting libncurses5...
I: Extracting libnih-dbus1...
I: Extracting libnih1...
I: Extracting libpam-modules...
I: Extracting libpam-runtime...
I: Extracting libpam0g...
I: Extracting libpcre3...
I: Extracting libplymouth2...
I: Extracting libpng12-0...
I: Extracting libselinux1...
I: Extracting libsepol1...
I: Extracting libslang2...
I: Extracting libss2...
I: Extracting libssl0.9.8...
I: Extracting libstdc++6...
I: Extracting libtext-charwidth-perl...
I: Extracting libtext-iconv-perl...
I: Extracting libtext-wrapi18n-perl...
I: Extracting libudev0...
I: Extracting libusb-0.1-4...
I: Extracting libuuid1...
I: Extracting locales...
I: Extracting login...
I: Extracting lsb-base...
I: Extracting lzma...
I: Extracting makedev...
I: Extracting mawk...
I: Extracting module-init-tools...
I: Extracting mount...
I: Extracting mountall...
I: Extracting ncurses-base...
I: Extracting ncurses-bin...
I: Extracting net-tools...
I: Extracting netbase...
I: Extracting passwd...
I: Extracting perl-base...
I: Extracting plymouth...
I: Extracting procps...
I: Extracting python-minimal...
I: Extracting python2.6-minimal...
I: Extracting sed...
I: Extracting sensible-utils...
I: Extracting sysv-rc...
I: Extracting sysvinit-utils...
I: Extracting tar...
I: Extracting tzdata...
I: Extracting udev...
I: Extracting upstart...
I: Extracting util-linux...
I: Extracting zlib1g...
**W: Failure trying to run: chroot /mnt/lfs mount -t proc proc /proc**
[root@localhost mnt]#

Then I try
[root@localhost mnt]# chroot /mnt/lfs /bin/bash
chroot: cannot run command `/bin/bash': Exec format error


It fails after Extracting zlib1g every time. I did a search and some people says it's a issue when installing x64 os on a i386 os, but I tried --arch i386 and had the same problem.

So my questions are
1. Is the file downloading done?
2. what's wrong w/ it?
3. any fix?

I know I have a really old os(chroot needs to be updated, and gblic,gcc ?) and atm I can only access the server via ssh. Is there any way I can remote install Ubuntu to this server?

Thanks.

---

### Post by tijs14tijs on 2011-12-09
I have exactly the same problem on my Android. I am trying to install but I get this error every time. 

I also want a fix.:(

---

