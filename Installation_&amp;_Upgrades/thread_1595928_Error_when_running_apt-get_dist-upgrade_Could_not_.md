---
title: "Error when running apt-get dist-upgrade: Could not perform immediate configuration..."
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by udito on 2010-10-13
Hello,

Everything works well when executing:
```
sudo apt-get update
sudo apt-get upgrade
```

When executing
[LIST]
[*]sudo apt-get dist-upgrade
[/LIST]
I get this
```
root@X100e:~# sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  adduser apt apt-utils base-files base-passwd bash bash-completion bsdmainutils bsdutils busybox-initramfs consolekit coreutils cpio
  cpp cpp-4.4 dash dbus debconf debconf-i18n debianutils diffutils dpkg e2fslibs e2fsprogs file findutils gawk gcc-4.4-base gcc-4.5-base
  gpgv grep gzip hostname ifupdown initramfs-tools initramfs-tools-bin initscripts insserv klibc-utils libacl1 libattr1 libblkid1
  libbz2-1.0 libc-bin libc6 libck-connector0 libcomerr2 libdb4.8 libdbus-1-3 libdbus-glib-1-2 libdconf0 libdrm-intel1 libdrm-nouveau1
  libdrm-radeon1 libdrm2 libeggdbus-1-0 libexpat1 libgcc1 libgdbm3 libglib2.0-0 libglib2.0-data libgmp3c2 libgpm2 libklibc
  liblocale-gettext-perl liblzma2 libmagic1 libmpfr4 libncurses5 libncursesw5 libnih-dbus1 libnih1 libpam-ck-connector libpam-modules
  libpam-runtime libpam0g libpcre3 libplymouth2 libpng12-0 libpolkit-gobject-1-0 libreadline6 libselinux1 libsepol1 libslang2
  libsqlite3-0 libss2 libssl0.9.8 libstdc++6 libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libudev0 libusb-0.1-4
  libuuid1 libx11-6 libx11-data libxau6 libxcb1 libxdmcp6 libxml2 login lsb-base make makedev mime-support module-init-tools mount
  mountall ncurses-base ncurses-bin net-tools netbase passwd perl perl-base perl-modules plymouth plymouth-theme-ubuntu-text procps
  psmisc python python-minimal python2.6 python2.6-minimal readline-common sed sensible-utils sgml-base shared-mime-info sysv-rc
  sysvinit-utils tar tzdata ubuntu-keyring udev upstart util-linux uuid-runtime xml-core xz-utils zlib1g
0 upgraded, 141 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/49.7MB of archives.
After this operation, 177MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
E: Could not perform immediate configuration on 'libbz2-1.0'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
```
At this point I'm stucked... Any clues?

Thanks, Udo

---

### Post by udito on 2010-10-16
Hello,

I was able to solve the issue. See [http://superuser.com/questions/199582/apt-error-could-not-perform-immediate-configuration-on]("http://superuser.com/questions/199582/apt-error-could-not-perform-immediate-configuration-on") for solution.

Note: I had to open this duplicate thread because my original post was "hijacked" multiple times -> the result was a big mess: [http://ubuntuforums.org/showthread.php?t=1594803](http://ubuntuforums.org/showthread.php?t=1594803) -> sory about this.

---

### Post by Dr Widdleguy on 2012-03-12
That didn't solve my issue. :/

---

### Post by oldos2er on 2012-03-13
Closed. Please start a new thread for your question or problem.

---

