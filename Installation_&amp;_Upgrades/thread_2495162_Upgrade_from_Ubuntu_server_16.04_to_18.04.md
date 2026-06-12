---
title: "Upgrade from Ubuntu server 16.04 to 18.04"
date: 2024-02-09
forum: Installation &amp; Upgrades
---

### Post by batuman on 2024-02-09
I am trying to upgrade to Ubuntu16.04.

Update

(base) user@m40g3:~$ sudo apt update
Hit:1 [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) xenial-updates InRelease
Hit:3 [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) xenial-backports InRelease
Get:4 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) xenial InRelease [66.2 kB]
Hit:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Fetched 66.2 kB in 1s (50.3 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
3 packages can be upgraded. Run 'apt list --upgradable' to see them.


Upgrade

(base) user@m40g3:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following security updates require Ubuntu Pro with 'esm-infra' enabled:
  libpam0g libgssapi3-heimdal libxdmcp6 libcairo-script-interpreter2
  libpcre16-3 perl-base libpolkit-gobject-1-0 libdjvulibre-text bluez
  libhttp-daemon-perl screen libcroco3 libwebp5 libdns-export162 libqpdf21
  fuse libcomerr2 libkrb5-3 libgssapi-krb5-2 python2.7-dev libjpeg-turbo8-dev
  poppler-utils dbus-x11 gstreamer1.0-alsa libisccfg140 libcups2
  intel-microcode libdbus-1-3 libwind0-heimdal uuid-runtime
  printer-driver-splix libfdisk1 libice-dev libpcre3-dev libsasl2-modules-db
  linux-libc-dev xserver-common python3-mako vim-common libx11-xcb-dev
  libnss3-nssdb libcurl3 libxml2-utils gnupg-agent libprotobuf-lite9v5
  libgrilo-0.2-1 openjdk-8-jdk gstreamer1.0-plugins-base-apps libldap-2.4-2
  openjdk-8-jre libpam-modules openssl bluez-cups libc6-dbg libssh-4 libc6-dev
  imagemagick libcairo-gobject2 libgnutls-openssl27 libopenexr-dev ntfs-3g
  libxv-dev libwbclient0 git-man libcairo2-dev libsystemd0 gstreamer1.0-tools
  linux-image-generic-hwe-16.04 libexpat1-dev libgd3 libheimntlm0-heimdal
  liblouis9 libksba8 libavahi-glib1 gstreamer1.0-plugins-good libgs9
  python-imaging dbus libpixman-1-0 python2.7-minimal libmount1 tcpdump snapd
  printer-driver-foo2zjs libsqlite3-0 libxrender1 libprotoc9v5 libcdio13
  libicu55 libelf1 python3-urllib3 binutils libmagickwand-6.q16-2
  libharfbuzz-gobject0 squashfs-tools libsnmp-base bind9-host e2fsprogs zlib1g
  gnupg-curl linux-generic-hwe-16.04 libavahi-common-data dnsutils libgmp10
  perl-modules-5.22 libavahi-common3 sudo libpython2.7 libncurses5 python2.7
  dnsmasq-base libcdio-cdda1 python3-pil libheimbase1-heimdal libc6 util-linux
  libpython3.5 python3.5 git openssh-sftp-server libyajl2 python3.5-minimal
  python3-louis libsepol1 libpolkit-agent-1-0 libk5crypto3 libharfbuzz-icu0
  libisc160 libvorbisfile3 libpython2.7-dev udev locales libxrandr-dev
  libfribidi-dev gstreamer1.0-plugins-base cups-server-common libpcre32-3
  passwd procps libsasl2-2 zlib1g-dev libklibc libpam-runtime e2fslibs
  isc-dhcp-common amd64-microcode python3.5-dev cups-common libwavpack1
  libncursesw5 libprocps4 libx11-6 python3-requests libexpat1
  libgstreamer-plugins-good1.0-0 libudev1 libvpx3 rsyslog libwebpdemux1
  gstreamer1.0-pulseaudio libpng12-dev krb5-locales libtiff5-dev dirmngr
  libss2 mount libavahi-ui-gtk3-0 openjdk-8-jdk-headless libperl5.22
  libaspell15 samba-libs libcdio-paranoia1 apport protobuf-compiler gdisk
  libharfbuzz-dev libblkid1 dpkg cups-filters imagemagick-6.q16 libtiff5
  libvorbis-dev libsnmp30 libmagickcore-6.q16-2-extra libisc-export160
  busybox-static libc-bin man-db libsasl2-modules libudev-dev cups-ppdc
  libcupsmime1 libtinfo5 libcaca0 python3-apport libxi6 libkrb5support0
  libjbig2dec0 libjbig-dev libpcre3 libxv1 avahi-daemon libvorbisenc2 libcap2
  libfuse2 libcupsfilters1 libfreetype6-dev tar systemd-sysv libcap2-bin
  libspeex1 libuuid1 libavahi-core7 libxdmcp-dev libgcrypt20 liblwres141
  libjack-jackd2-0 libhcrypto4-heimdal libglib2.0-bin python-pkg-resources
  vim-runtime libdbus-1-dev liblz4-1 gpgv ubuntu-core-launcher vim
  libpam-systemd libgstreamer-plugins-base1.0-0 libxrandr2 distro-info-data
  libsndfile1 xz-utils ncurses-term libglib2.0-dev gstreamer1.0-x
  python3-pkg-resources ghostscript systemd libpython3.5-dev libsmartcols1
  login libfontembed1 libssh-gcrypt-4 gir1.2-gst-plugins-base-1.0 libxfixes3
  libpolkit-backend-1-0 libwebpmux1 ncurses-bin python-setuptools
  libpam-modules-bin openssh-server libx11-data ghostscript-x aspell
  libxrender-dev libopenexr22 libsmbclient unzip libspeexdsp1 openssh-client
  libmagickcore-6.q16-2 libgs9-common avahi-autoipd bsdutils libxfixes-dev
  libgraphite2-3 libdns162 libx11-dev xserver-xorg-core-hwe-16.04
  libjpeg-turbo8 qpdf libx11-doc libglib2.0-data bluez-obexd ncurses-base
  gnupg2 openjdk-8-jre-headless cups-filters-core-drivers bash policykit-1
  libdjvulibre21 apport-gtk libjbig0 libc-dev-bin libxml2 libcupsppdc1
  libflac8 libpython2.7-minimal multiarch-support cpio libgnutls30 libnss3
  libroken18-heimdal libfreetype6 ca-certificates liblouis-data libicu-dev
  perl rsync vim-tiny imagemagick-common libasn1-8-heimdal libzstd1
  libisccc140 libkrb5-26-heimdal gir1.2-gstreamer-1.0 cups-bsd avahi-utils
  linux-headers-generic-hwe-16.04 cron libxpm4 xserver-xorg-legacy-hwe-16.04
  libpython3.5-stdlib cups-core-drivers libvorbis0a libbind9-140 cups-daemon
  gzip libpixman-1-dev python3-jinja2 accountsservice libharfbuzz0b libtasn1-6
  gnupg icu-devtools libpcrecpp0v5 libbluetooth3 libice6 libcairo2
  libcupsimage2 libpython2.7-stdlib libexiv2-14 libpoppler-glib8 liblzma5
  python3-lxml libpython3.5-minimal libpoppler58 libxi-dev libavahi-client3
  libprotobuf9v5 cups curl libdpkg-perl libhx509-5-heimdal isc-dhcp-client
  libcupscgi1 libprotobuf-dev cups-client klibc-utils git-core
  libgstreamer1.0-0 python3-problem-report libsamplerate0 libpng12-0
  libglib2.0-0 liblzma-dev python-pil libcurl3-gnutls
  printer-driver-foo2zjs-common libx11-xcb1 libfribidi0 libaccountsservice0
  libtiffxx5 python3-setuptools cups-browsed libxslt1.1 libssl1.0.0 dpkg-dev
  tzdata busybox-initramfs
Learn more about Ubuntu Pro for 16.04 at [https://ubuntu.com/16-04](https://ubuntu.com/16-04)
The following packages have been kept back:
  linux-generic-hwe-16.04 linux-headers-generic-hwe-16.04 linux-image-generic-hwe-16.04
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

Then
(base) user@m40g3:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic-hwe-16.04 linux-headers-generic-hwe-16.04 linux-image-generic-hwe-16.04
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

(base) user@m40g3:~$ sudo do-release-upgradeChecking for a new Ubuntu release
Please install all available updates for your release before upgrading.


Upgradable gives me

(base) user@m40g3:~$ sudo apt list --upgradable
Listing... Done
linux-generic-hwe-16.04/xenial-updates,xenial-security 4.15.0.142.137 amd64 [upgradable from: 4.13.0.45.64]
linux-headers-generic-hwe-16.04/xenial-updates,xenial-security 4.15.0.142.137 amd64 [upgradable from: 4.13.0.45.64]
linux-image-generic-hwe-16.04/xenial-updates,xenial-security 4.15.0.142.137 amd64 [upgradable from: 4.13.0.45.64]

How can I upgrade to 18.04

---

### Post by ian-weisser on 2024-02-09
Why bother? Ubuntu 18.04 is also past EOL. Then you must release-upgrade to 20.04.
Your system has not received security updates for almost three years. Not a good candidate for release-upgrade.
You are asking for support on a release that we no longer provide support for.

For most users, it is much simpler and less fraught to just install 22.04.

If you really want to go the upgrade route, run the following and show us the complete output:

```
apt policy linux-image-generic-hwe-16.04
```

---

### Post by TheFu on 2024-02-09
I'm with Ian.

Standard supported for 18.04 ended mid-last year.  It isn't worth your time if you are running 16.04 to install anything except 22.04 at this point.  Not an upgrade - a fresh install to clean out all the cruft.  There have been huge changes since 2016 with my subsystems being completely replaced in this time.

Take the hit. Backup any data and configs you need. Make a list of manually installed packages for reference, then install 22.04, fresh.  Put your data back where it was, selectively put the config files where they were (don't do that for anything related to drivers!), then feed the list of manually installed packages into APT and install those.

Next August, make a calendar entry now, while all this is fresh in your mind, do it again with 24.04.1 when that gets released.  Then you can sit back and coast until 2029 running it.

I did something like that with 18.04 last year, just before support ended. Turns out that migrating to a newer release is much easier BEFORE regular support ends.  After that EOL date, there are just a bunch of little issues. If you aren't a huge Ubuntu nerd, best to avoid issues.

But it is your box. Just beware that without ESM, there are remote take-over attacks in the wild today for that OS.  If you do have to run 18.04, don't put it on any network. This is for your safety and all ours too.

---

