---
title: "Trying to upgrade Lubuntu 20.04 to 22.04 - receiving MULTIPLE errors"
date: 2023-03-27
forum: Installation &amp; Upgrades
---

### Post by 77_GCSX on 2023-03-27
My system = Dell Insipron 15-3552, 4gb ram, 1 tb ssd drive

I am trying to upgrade to the latest version (all using SUDO) but I keep getting the following errors: (**Warning - VERY LONG**). Any help is greatly appreciated!!

P.S. IF the best way to fix this is to do a CLEAN install I'm not against it, just would like to know if I can do it this way at all.

```
Configuring libssl1.1
Configuring tzdata
Configuring grub-efi-amd64
Configuring libpam-systemd
Configuring ubuntu-advantage-tools
Configuring xserver-xorg-legacyPackage operation failed
The installation or removal of a software package failed.
Running post-installation trigger dpkg-exec
Preparing installation of firefox
Unpacking firefox
Installing firefox
Preparing installation of firefox-locale-en
Unpacking firefox-locale-en
Installing firefox-locale-en
Preparing installation of libsnmp-base
Unpacking libsnmp-base
Installing libsnmp-base
Preparing installation of libsnmp35
Unpacking libsnmp35
Installing libsnmp35
Preparing installation of libunwind8
Unpacking libunwind8
Installing libunwind8
Preparing installation of linux-libc-dev
Unpacking linux-libc-dev
Installing linux-libc-dev
Preparing installation of printer-driver-foo2zjs-common
Unpacking printer-driver-foo2zjs-common
Installing printer-driver-foo2zjs-common
Preparing installation of printer-driver-foo2zjs
Unpacking printer-driver-foo2zjs
Installing printer-driver-foo2zjs
Preparing installation of printer-driver-splix
Unpacking printer-driver-splix
Installing printer-driver-splix
Running post-installation trigger dpkg-exec
Preparing configuration of printer-driver-foo2zjs-common
Configuring printer-driver-foo2zjs-common
Installed printer-driver-foo2zjs-common
Preparing configuration of firefox
Configuring firefox
Installed firefox
Preparing configuration of libsnmp-base
Configuring libsnmp-base
Installed libsnmp-base
Preparing configuration of libssl1.1
Configuring libssl1.1
Preparing configuration of linux-libc-dev
Configuring linux-libc-dev
Installed linux-libc-dev
Preparing configuration of libunwind8
Configuring libunwind8
Installed libunwind8
Preparing configuration of tzdata
Configuring tzdata
Preparing configuration of firefox-locale-en
Configuring firefox-locale-en
Installed firefox-locale-en
Preparing configuration of grub-efi-amd64
Configuring grub-efi-amd64
Preparing configuration of printer-driver-foo2zjs
Configuring printer-driver-foo2zjs
Installed printer-driver-foo2zjs
Preparing configuration of printer-driver-splix
Configuring printer-driver-splix
Installed printer-driver-splix
Preparing configuration of libpam-systemd
Configuring libpam-systemd
Preparing configuration of ubuntu-advantage-tools
Configuring ubuntu-advantage-tools
Preparing configuration of xserver-xorg-legacy
Configuring xserver-xorg-legacy
Configuring libssl1.1
Configuring tzdata
Configuring grub-efi-amd64
Configuring libpam-systemd
Configuring ubuntu-advantage-tools
Configuring xserver-xorg-legacy
Error Resume:
Eror Code: error-package-manager-failed
Package operation failed
The installation or removal of a software package failed.
Error Detail:
Package operation failed
The installation or removal of a software package failed.
Eror Code: error-package-manager-failed
Package operation failed
The installation or removal of a software package failed.
Error Detail:
Package operation failed
The installation or removal of a software package failed.
Eror Code: error-package-manager-failed
Package operation failed
The installation or removal of a software package failed.
Error Detail: installArchives() failed: debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ...
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 372377 files and directories currently installed.)
Preparing to unpack .../0-firefox_111.0.1+build2-0ubuntu0.20.04.1_amd64.deb ...
Unpacking firefox (111.0.1+build2-0ubuntu0.20.04.1) over (111.0+build2-0ubuntu0.20.04.1) ...
Preparing to unpack .../1-firefox-locale-en_111.0.1+build2-0ubuntu0.20.04.1_amd64.deb ...
Unpacking firefox-locale-en (111.0.1+build2-0ubuntu0.20.04.1) over (111.0+build2-0ubuntu0.20.04.1) ...
Preparing to unpack .../2-libsnmp-base_5.8+dfsg-2ubuntu2.7_all.deb ...
Unpacking libsnmp-base (5.8+dfsg-2ubuntu2.7) over (5.8+dfsg-2ubuntu2.6) ...
Preparing to unpack .../3-libsnmp35_5.8+dfsg-2ubuntu2.7_amd64.deb ...
Unpacking libsnmp35:amd64 (5.8+dfsg-2ubuntu2.7) over (5.8+dfsg-2ubuntu2.6) ...
Preparing to unpack .../4-libunwind8_1.2.1-9ubuntu0.1_amd64.deb ...
Unpacking libunwind8:amd64 (1.2.1-9ubuntu0.1) over (1.2.1-9build1) ...
Preparing to unpack .../5-linux-libc-dev_5.4.0-146.163_amd64.deb ...
Unpacking linux-libc-dev:amd64 (5.4.0-146.163) over (5.4.0-144.161) ...
Preparing to unpack .../6-printer-driver-foo2zjs-common_20171202dfsg0-4ubuntu0.1_all.deb ...
Unpacking printer-driver-foo2zjs-common (20171202dfsg0-4ubuntu0.1) over (20171202dfsg0-4) ...
Preparing to unpack .../7-printer-driver-foo2zjs_20171202dfsg0-4ubuntu0.1_amd64.deb ...
Unpacking printer-driver-foo2zjs (20171202dfsg0-4ubuntu0.1) over (20171202dfsg0-4) ...
Preparing to unpack .../8-printer-driver-splix_2.0.0+svn315-7fakesync1ubuntu0.1_amd64.deb ...
Unpacking printer-driver-splix (2.0.0+svn315-7fakesync1ubuntu0.1) over (2.0.0+svn315-7fakesync1build1) ...
Setting up printer-driver-foo2zjs-common (20171202dfsg0-4ubuntu0.1) ...
Setting up firefox (111.0.1+build2-0ubuntu0.20.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up libsnmp-base (5.8+dfsg-2ubuntu2.7) ...
Setting up libssl1.1:amd64 (1.1.1f-1ubuntu2.17) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libssl1.1:amd64 (--configure):
installed libssl1.1:amd64 package post-installation script subprocess returned error exit status 1
Setting up linux-libc-dev:amd64 (5.4.0-146.163) ...
dpkg: dependency problems prevent configuration of linux-headers-5.4.0-146-generic:
linux-headers-5.4.0-146-generic depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package linux-headers-5.4.0-146-generic (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
linux-headers-generic depends on linux-headers-5.4.0-146-generic; however:
Package linux-headers-5.4.0-146-generic is not configured yet.
dpkg: error processing package linux-headers-generic (--configure):
dependency problems - leaving unconfigured
Setting up libunwind8:amd64 (1.2.1-9ubuntu0.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Setting up tzdata (2022g-0ubuntu0.20.04.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package tzdata (--configure):
installed tzdata package post-installation script subprocess returned error exit status 1
Setting up firefox-locale-en (111.0.1+build2-0ubuntu0.20.04.1) ...
No apport report written because MaxReports is reached already
Setting up grub-efi-amd64 (2.06-2ubuntu14.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package grub-efi-amd64 (--configure):
installed grub-efi-amd64 package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
Setting up printer-driver-foo2zjs (20171202dfsg0-4ubuntu0.1) ...
Setting up printer-driver-splix (2.0.0+svn315-7fakesync1ubuntu0.1) ...
Setting up libpam-systemd:amd64 (245.4-4ubuntu3.20) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libpam-systemd:amd64 (--configure):
installed libpam-systemd:amd64 package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libcurl4:amd64:
libcurl4:amd64 depends on libssl1.1 (>= 1.1.1); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package libcurl4:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkrb5-3:amd64:
libkrb5-3:amd64 depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package libkrb5-3:amd64 (--configure):
dependency problems - leaving unconfigured
Setting up ubuntu-advantage-tools (27.13.6~20.04.1) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package ubuntu-advantage-tools (--configure):
installed ubuntu-advantage-tools package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of bind9-dnsutils:
bind9-dnsutils depends on libkrb5-3 (>= 1.6.dfsg.2); however:
Package libkrb5-3:amd64 is not configured yet.
bind9-dnsutils depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package bind9-dnsutils (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bind9-host:
bind9-host depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package bind9-host (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-advantage-desktop-daemon:
ubuntu-advantage-desktop-daemon depends on ubuntu-advantage-tools; however:
PackageNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
ubuntu-advantage-tools is not configured yet.
dpkg: error processing package ubuntu-advantage-desktop-daemon (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openssl:
openssl depends on libssl1.1 (>= 1.1.1); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package openssl (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-5.4.0-144-generic:
linux-headers-5.4.0-144-generic depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package linux-headers-5.4.0-144-generic (--configure):
dependency problems - leaving unconfigured
Setting up xserver-xorg-legacy (2:1.20.13-1ubuntu1~20.04.6) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package xserver-xorg-legacy (--configure):
installed xserver-xorg-legacy package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of tcpdump:
tcpdump depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package tcpdump (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmysqlclient21:amd64:
libmysqlclient21:amd64 depends on libssl1.1 (>= 1.1.1); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package libmysqlclient21:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpython3.8-minimal:amd64:
libpython3.8-minimal:amd64 depends on libssl1.1 (>= 1.1.1); however:
Package libssl1.1:amd64 is not configured yet.
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg: error processing package libpython3.8-minimal:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsnmp35:amd64:
libsnmp35:amd64 depends on libmysqlclient21 (>= 8.0.11); however:
Package libmysqlclient21:amd64 is not configured yet.
libsnmp35:amd64 depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package libsnmp35:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-efi-amd64-signed:
grub-efi-amd64-signed depends on grub-efi-amd64 | grub-pc; however:
Package grub-efi-amd64 is not configured yet.
Package grub-pc is not installed.
dpkg: error processing package grub-efi-amd64-signed (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
linux-generic depends on linux-headers-generic (= 5.4.0.146.144); however:
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Package linux-headers-generic is not configured yet.
dpkg: error processing package linux-generic (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bind9-libs:amd64:
bind9-libs:amd64 depends on libkrb5-3 (>= 1.6.dfsg.2); however:
Package libkrb5-3:amd64 is not configured yet.
bind9-libs:amd64 depends on libssl1.1 (>= 1.1.1); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package bind9-libs:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
software-properties-gtk depends on ubuntu-advantage-desktop-daemon; however:
Package ubuntu-advantage-desktop-daemon is not configured yet.
software-properties-gtk depends on ubuntu-advantage-tools (>= 27.11~); however:
Package ubuntu-advantage-tools is not configured yet.
dpkg: error processing package software-properties-gtk (--configure):
dependency probleNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
ms - leaving unconfigured
dpkg: dependency problems prevent configuration of dnsutils:
dnsutils depends on bind9-dnsutils; however:
Package bind9-dnsutils is not configured yet.
dpkg: error processing package dnsutils (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shim-signed:
shim-signed depends on grub-efi-amd64-signed (>= 1.187.2~) | grub-efi-arm64-signed (>= 1.187.2~); however:
Package grub-efi-amd64-signed is not configured yet.
Package grub-efi-arm64-signed is not installed.
dpkg: error processing package shim-signed (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-tz:
python3-tz depends on tzdata; however:
Package tzdata is not configured yet.
dpkg: error processing package python3-tz (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ca-certificates:
ca-certificates depends on oNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
penssl (>= 1.1.1); however:
Package openssl is not configured yet.
dpkg: error processing package ca-certificates (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dbus-user-session:
dbus-user-session depends on libpam-systemd; however:
Package libpam-systemd:amd64 is not configured yet.
dpkg: error processing package dbus-user-session (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-software:
gnome-software depends on software-properties-gtk; however:
Package software-properties-gtk is not configured yet.
dpkg: error processing package gnome-software (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgssapi-krb5-2:amd64:
libgssapi-krb5-2:amd64 depends on libkrb5-3 (= 1.17-6ubuntu4.3); however:
Package libkrb5-3:amd64 is not configured yet.
dpkg: error processing package libgssapi-krb5-2:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:
ubuntu-release-upgrader-core depends on ca-certificates; however:
Package ca-certificates is not configured yet.
dpkg: error processing package ubuntu-release-upgrader-core (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
update-manager-core depends on ubuntu-release-upgrader-core (>= 1:18.04.9); however:
Package ubuntu-release-upgrader-core is not configured yet.
update-manager-core depends on ubuntu-advantage-tools; however:
Package ubuntu-advantage-tools is not configured yet.
dpkg: error processing package update-manager-core (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3.8-minimal:
python3.8-minimal depends on libpython3.8-minimal (= 3.8.10-0ubuntu1~20.04.7); however:
Package libpython3.8-minimal:amd64 is not configured yet.
dpkg: error processing package python3.8-minimal (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-gtk:
ubuntu-release-upgrader-gtk depends on ubuntu-release-upgrader-core (= 1:20.04.41); however:
Package ubuntu-release-upgrader-core is not configured yet.
dpkg: error processing package ubuntu-release-upgrader-gtk (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
update-notifier depends on ubuntu-release-upgrader-gtk; however:
Package ubuntu-release-upgrader-gtk is not configured yet.
dpkg: error processing package update-notifier (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpython3.8-stdlib:amd64:
libpython3.8-stdlib:amd64 depends on libpython3.8-minimal (= 3.8.10-0ubuntu1~20.04.7); however:
Package libpython3.8-minimal:amd64 is not configured yet.
dpkg: error processing package libpython3.8-stdlib:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3.8:
python3.8 depends on python3.8-minimal (= 3.8.10-0ubuntu1~20.04.7); however:
Package python3.8-minimal is not configured yet.
python3.8 depends on libpython3.8-stdlib (= 3.8.10-0ubuntu1~20.04.7); however:
Package libpython3.8-stdlib:amd64 is not configured yet.
dpkg: error processing package python3.8 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of snapd:
snapd depends on ca-certificates; however:
Package ca-certificates is not configured yet.
dpkg: error processing package snapd (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of google-chrome-stable:
google-chrome-stable depends on ca-certificates; however:
Package ca-certificates is not configured yet.
dpkg: error processing package google-chrome-stable (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier-common:
update-notifier-common depends on update-manager-core (>= 1:17.04.2); however:
Package update-manager-core is not configured yet.
dpkg: error processing package update-notifier-common (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
update-manager depends on update-manager-core (= 1:20.04.10.11); however:
Package update-manager-core is not configured yet.
update-manager depends on ubuntu-release-upgrader-gtk; however:
Package ubuntu-release-upgrader-gtk is not configured yet.
update-manager depends on update-notifier; however:
Package update-notifier is not configured yet.
dpkg: error processing package update-manager (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcurl3-gnutls:amd64:
libcurl3-gnutls:amd64 depends on libgssapi-krb5-2 (>= 1.17); however:
Package libgssapi-krb5-2:amd64 is not configured yet.
dpkg: error processing package libcurl3-gnutls:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-common:
software-properties-common depends on ca-certificates; however:
Package ca-certificates is not configured yet.
dpkg: error processing package software-properties-common (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-qt:
ubuntu-release-upgrader-qt depends on ubuntu-release-upgrader-core (= 1:20.04.41); however:
Package ubuntu-release-upgrader-core is not configured yet.
dpkg: error processing package ubuntu-release-upgrader-qt (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpython3.8:amd64:
libpython3.8:amd64 depends on libpython3.8-stdlib (= 3.8.10-0ubuntu1~20.04.7); however:
Package libpython3.8-stdlib:amd64 is not configured yet.
dpkg: error processing package libpython3.8:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-ldb:
python3-ldb depends on libpython3.8 (>= 3.8.2); however:
Package libpython3.8:amd64 is not configured yet.
dpkg: error processing package python3-ldb (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of git:
git depends on libcurl3-gnutls (>= 7.56.1); however:
Package libcurl3-gnutls:amd64 is not configured yet.
dpkg: error processing package git (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lubuntu-update-notifier:
lubuntu-update-notifier depends on update-notifier-common; however:
Package update-notifier-common is not configured yet.
dpkg: error processing package lubuntu-update-notifier (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-qt:
software-properties-qt depends on software-properties-common; however:
Package software-properties-common is not configured yet.
dpkg: error processing package software-properties-qt (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vim:
vim depends on libpython3.8 (>= 3.8.2); however:
Package libpython3.8:amd64 is not configured yet.
dpkg: error processing package vim (--configure):
dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
libssl1.1:amd64
linux-headers-5.4.0-146-generic
linux-headers-generic
tzdata
grub-efi-amd64
libpam-systemd:amd64
libcurl4:amd64
libkrb5-3:amd64
ubuntu-advantage-tools
bind9-dnsutils
bind9-host
ubuntu-advantage-desktop-daemon
openssl
linux-headers-5.4.0-144-generic
xserver-xorg-legacy
tcpdump
libmysqlclient21:amd64
libpython3.8-minimal:amd64
libsnmp35:amd64
grub-efi-amd64-signed
linux-generic
bind9-libs:amd64
software-properties-gtk
dnsutils
shim-signed
python3-tz
ca-certificates
dbus-user-session
gnome-software
libgssapi-krb5-2:amd64
ubuntu-release-upgrader-core
update-manager-core
python3.8-minimal
ubuntu-release-upgrader-gtk
update-notifier
libpython3.8-stdlib:amd64
python3.8
snapd
google-chrome-stable
update-notifier-common
update-manager
libcurl3-gnutls:amd64
software-properties-common
ubuntu-release-upgrader-qt
libpython3.8:amd64
python3-ldb
git
lubuntu-update-notifier
software-properties-qt
vim
Processing was halted because there were too many errors.
Setting up libssl1.1:amd64 (1.1.1f-1ubuntu2.17) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libssl1.1:amd64 (--configure):
installed libssl1.1:amd64 package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of linux-headers-5.4.0-146-generic:
linux-headers-5.4.0-146-generic depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package linux-headers-5.4.0-146-generic (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
linux-headers-generic depends on linux-headers-5.4.0-146-generic; however:
Package linux-headers-5.4.0-146-generic is not configured yet.
dpkg: error processing package linux-headers-generic (--configure):
dependency problems - leaving unconfigured
Setting up tzdata (2022g-0ubuntu0.20.04.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package tzdata (--configure):
installed tzdata package post-installation script subprocess returned error exit status 1
Setting up grub-efi-amd64 (2.06-2ubuntu14.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package grub-efi-amd64 (--configure):
installed grub-efi-amd64 package post-installation script subprocess returned error exit status 1
Setting up libpam-systemd:amd64 (245.4-4ubuntu3.20) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libpam-systemd:amd64 (--configure):
installed libpam-systemd:amd64 package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of libcurl4:amd64:
libcurl4:amd64 depends on libssl1.1 (>= 1.1.1); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package libcurl4:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkrb5-3:amd64:
libkrb5-3:amd64 depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package libkrb5-3:amd64 (--configure):
dependency problems - leaving unconfigured
Setting up ubuntu-advantage-tools (27.13.6~20.04.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package ubuntu-advantage-tools (--configure):
installed ubuntu-advantage-tools package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of bind9-dnsutils:
bind9-dnsutils depends on libkrb5-3 (>= 1.6.dfsg.2); however:
Package libkrb5-3:amd64 is not configured yet.
bind9-dnsutils depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package bind9-dnsutils (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bind9-host:
bind9-host depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package bind9-host (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-advantage-desktop-daemon:
ubuntu-advantage-desktop-daemon depends on ubuntu-advantage-tools; however:
Package ubuntu-advantage-tools is not configured yet.
dpkg: error processing package ubuntu-advantage-desktop-daemon (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openssl:
openssl depends on libssl1.1 (>= 1.1.1); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package openssl (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-5.4.0-144-generic:
linux-headers-5.4.0-144-generic depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package linux-headers-5.4.0-144-generic (--configure):
dependency problems - leaving unconfigured
Setting up xserver-xorg-legacy (2:1.20.13-1ubuntu1~20.04.6) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package xserver-xorg-legacy (--configure):
installed xserver-xorg-legacy package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of tcpdump:
tcpdump depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
Package operation failed
The installation or removal of a software package failed.
Eror Code: error-package-manager-failed
Package operation failed
The installation or removal of a software package failed.
Error Detail: installArchives() failed: debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ...
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 372377 files and directories currently installed.)
Preparing to unpack .../0-firefox_111.0.1+build2-0ubuntu0.20.04.1_amd64.deb ...
Unpacking firefox (111.0.1+build2-0ubuntu0.20.04.1) over (111.0+build2-0ubuntu0.20.04.1) ...
Preparing to unpack .../1-firefox-locale-en_111.0.1+build2-0ubuntu0.20.04.1_amd64.deb ...
Unpacking firefox-locale-en (111.0.1+build2-0ubuntu0.20.04.1) over (111.0+build2-0ubuntu0.20.04.1) ...
Preparing to unpack .../2-libsnmp-base_5.8+dfsg-2ubuntu2.7_all.deb ...
Unpacking libsnmp-base (5.8+dfsg-2ubuntu2.7) over (5.8+dfsg-2ubuntu2.6) ...
Preparing to unpack .../3-libsnmp35_5.8+dfsg-2ubuntu2.7_amd64.deb ...
Unpacking libsnmp35:amd64 (5.8+dfsg-2ubuntu2.7) over (5.8+dfsg-2ubuntu2.6) ...
Preparing to unpack .../4-libunwind8_1.2.1-9ubuntu0.1_amd64.deb ...
Unpacking libunwind8:amd64 (1.2.1-9ubuntu0.1) over (1.2.1-9build1) ...
Preparing to unpack .../5-linux-libc-dev_5.4.0-146.163_amd64.deb ...
Unpacking linux-libc-dev:amd64 (5.4.0-146.163) over (5.4.0-144.161) ...
Preparing to unpack .../6-printer-driver-foo2zjs-common_20171202dfsg0-4ubuntu0.1_all.deb ...
Unpacking printer-driver-foo2zjs-common (20171202dfsg0-4ubuntu0.1) over (20171202dfsg0-4) ...
Preparing to unpack .../7-printer-driver-foo2zjs_20171202dfsg0-4ubuntu0.1_amd64.deb ...
Unpacking printer-driver-foo2zjs (20171202dfsg0-4ubuntu0.1) over (20171202dfsg0-4) ...
Preparing to unpack .../8-printer-driver-splix_2.0.0+svn315-7fakesync1ubuntu0.1_amd64.deb ...
Unpacking printer-driver-splix (2.0.0+svn315-7fakesync1ubuntu0.1) over (2.0.0+svn315-7fakesync1build1) ...
Setting up printer-driver-foo2zjs-common (20171202dfsg0-4ubuntu0.1) ...
Setting up firefox (111.0.1+build2-0ubuntu0.20.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up libsnmp-base (5.8+dfsg-2ubuntu2.7) ...
Setting up libssl1.1:amd64 (1.1.1f-1ubuntu2.17) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libssl1.1:amd64 (--configure):
installed libssl1.1:amd64 package post-installation script subprocess returned error exit status 1
Setting up linux-libc-dev:amd64 (5.4.0-146.163) ...
dpkg: dependency problems prevent configuration of linux-headers-5.4.0-146-generic:
linux-headers-5.4.0-146-generic depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package linux-headers-5.4.0-146-generic (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
linux-headers-generic depends on linux-headers-5.4.0-146-generic; however:
Package linux-headers-5.4.0-146-generic is not configured yet.
dpkg: error processing package linux-headers-generic (--configure):
dependency problems - leaving unconfigured
Setting up libunwind8:amd64 (1.2.1-9ubuntu0.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Setting up tzdata (2022g-0ubuntu0.20.04.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package tzdata (--configure):
installed tzdata package post-installation script subprocess returned error exit status 1
Setting up firefox-locale-en (111.0.1+build2-0ubuntu0.20.04.1) ...
No apport report written because MaxReports is reached already
Setting up grub-efi-amd64 (2.06-2ubuntu14.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package grub-efi-amd64 (--configure):
installed grub-efi-amd64 package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
Setting up printer-driver-foo2zjs (20171202dfsg0-4ubuntu0.1) ...
Setting up printer-driver-splix (2.0.0+svn315-7fakesync1ubuntu0.1) ...
Setting up libpam-systemd:amd64 (245.4-4ubuntu3.20) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libpam-systemd:amd64 (--configure):
installed libpam-systemd:amd64 package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libcurl4:amd64:
libcurl4:amd64 depends on libssl1.1 (>= 1.1.1); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package libcurl4:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkrb5-3:amd64:
libkrb5-3:amd64 depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package libkrb5-3:amd64 (--configure):
dependency problems - leaving unconfigured
Setting up ubuntu-advantage-tools (27.13.6~20.04.1) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package ubuntu-advantage-tools (--configure):
installed ubuntu-advantage-tools package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of bind9-dnsutils:
bind9-dnsutils depends on libkrb5-3 (>= 1.6.dfsg.2); however:
Package libkrb5-3:amd64 is not configured yet.
bind9-dnsutils depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package bind9-dnsutils (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bind9-host:
bind9-host depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package bind9-host (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-advantage-desktop-daemon:
ubuntu-advantage-desktop-daemon depends on ubuntu-advantage-tools; however:
PackageNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
ubuntu-advantage-tools is not configured yet.
dpkg: error processing package ubuntu-advantage-desktop-daemon (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openssl:
openssl depends on libssl1.1 (>= 1.1.1); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package openssl (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-5.4.0-144-generic:
linux-headers-5.4.0-144-generic depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package linux-headers-5.4.0-144-generic (--configure):
dependency problems - leaving unconfigured
Setting up xserver-xorg-legacy (2:1.20.13-1ubuntu1~20.04.6) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package xserver-xorg-legacy (--configure):
installed xserver-xorg-legacy package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of tcpdump:
tcpdump depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package tcpdump (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmysqlclient21:amd64:
libmysqlclient21:amd64 depends on libssl1.1 (>= 1.1.1); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package libmysqlclient21:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpython3.8-minimal:amd64:
libpython3.8-minimal:amd64 depends on libssl1.1 (>= 1.1.1); however:
Package libssl1.1:amd64 is not configured yet.
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg: error processing package libpython3.8-minimal:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsnmp35:amd64:
libsnmp35:amd64 depends on libmysqlclient21 (>= 8.0.11); however:
Package libmysqlclient21:amd64 is not configured yet.
libsnmp35:amd64 depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package libsnmp35:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-efi-amd64-signed:
grub-efi-amd64-signed depends on grub-efi-amd64 | grub-pc; however:
Package grub-efi-amd64 is not configured yet.
Package grub-pc is not installed.
dpkg: error processing package grub-efi-amd64-signed (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
linux-generic depends on linux-headers-generic (= 5.4.0.146.144); however:
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Package linux-headers-generic is not configured yet.
dpkg: error processing package linux-generic (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bind9-libs:amd64:
bind9-libs:amd64 depends on libkrb5-3 (>= 1.6.dfsg.2); however:
Package libkrb5-3:amd64 is not configured yet.
bind9-libs:amd64 depends on libssl1.1 (>= 1.1.1); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package bind9-libs:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
software-properties-gtk depends on ubuntu-advantage-desktop-daemon; however:
Package ubuntu-advantage-desktop-daemon is not configured yet.
software-properties-gtk depends on ubuntu-advantage-tools (>= 27.11~); however:
Package ubuntu-advantage-tools is not configured yet.
dpkg: error processing package software-properties-gtk (--configure):
dependency probleNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
ms - leaving unconfigured
dpkg: dependency problems prevent configuration of dnsutils:
dnsutils depends on bind9-dnsutils; however:
Package bind9-dnsutils is not configured yet.
dpkg: error processing package dnsutils (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shim-signed:
shim-signed depends on grub-efi-amd64-signed (>= 1.187.2~) | grub-efi-arm64-signed (>= 1.187.2~); however:
Package grub-efi-amd64-signed is not configured yet.
Package grub-efi-arm64-signed is not installed.
dpkg: error processing package shim-signed (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-tz:
python3-tz depends on tzdata; however:
Package tzdata is not configured yet.
dpkg: error processing package python3-tz (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ca-certificates:
ca-certificates depends on oNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
penssl (>= 1.1.1); however:
Package openssl is not configured yet.
dpkg: error processing package ca-certificates (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dbus-user-session:
dbus-user-session depends on libpam-systemd; however:
Package libpam-systemd:amd64 is not configured yet.
dpkg: error processing package dbus-user-session (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-software:
gnome-software depends on software-properties-gtk; however:
Package software-properties-gtk is not configured yet.
dpkg: error processing package gnome-software (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgssapi-krb5-2:amd64:
libgssapi-krb5-2:amd64 depends on libkrb5-3 (= 1.17-6ubuntu4.3); however:
Package libkrb5-3:amd64 is not configured yet.
dpkg: error processing package libgssapi-krb5-2:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:
ubuntu-release-upgrader-core depends on ca-certificates; however:
Package ca-certificates is not configured yet.
dpkg: error processing package ubuntu-release-upgrader-core (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
update-manager-core depends on ubuntu-release-upgrader-core (>= 1:18.04.9); however:
Package ubuntu-release-upgrader-core is not configured yet.
update-manager-core depends on ubuntu-advantage-tools; however:
Package ubuntu-advantage-tools is not configured yet.
dpkg: error processing package update-manager-core (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3.8-minimal:
python3.8-minimal depends on libpython3.8-minimal (= 3.8.10-0ubuntu1~20.04.7); however:
Package libpython3.8-minimal:amd64 is not configured yet.
dpkg: error processing package python3.8-minimal (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-gtk:
ubuntu-release-upgrader-gtk depends on ubuntu-release-upgrader-core (= 1:20.04.41); however:
Package ubuntu-release-upgrader-core is not configured yet.
dpkg: error processing package ubuntu-release-upgrader-gtk (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
update-notifier depends on ubuntu-release-upgrader-gtk; however:
Package ubuntu-release-upgrader-gtk is not configured yet.
dpkg: error processing package update-notifier (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpython3.8-stdlib:amd64:
libpython3.8-stdlib:amd64 depends on libpython3.8-minimal (= 3.8.10-0ubuntu1~20.04.7); however:
Package libpython3.8-minimal:amd64 is not configured yet.
dpkg: error processing package libpython3.8-stdlib:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3.8:
python3.8 depends on python3.8-minimal (= 3.8.10-0ubuntu1~20.04.7); however:
Package python3.8-minimal is not configured yet.
python3.8 depends on libpython3.8-stdlib (= 3.8.10-0ubuntu1~20.04.7); however:
Package libpython3.8-stdlib:amd64 is not configured yet.
dpkg: error processing package python3.8 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of snapd:
snapd depends on ca-certificates; however:
Package ca-certificates is not configured yet.
dpkg: error processing package snapd (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of google-chrome-stable:
google-chrome-stable depends on ca-certificates; however:
Package ca-certificates is not configured yet.
dpkg: error processing package google-chrome-stable (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier-common:
update-notifier-common depends on update-manager-core (>= 1:17.04.2); however:
Package update-manager-core is not configured yet.
dpkg: error processing package update-notifier-common (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
update-manager depends on update-manager-core (= 1:20.04.10.11); however:
Package update-manager-core is not configured yet.
update-manager depends on ubuntu-release-upgrader-gtk; however:
Package ubuntu-release-upgrader-gtk is not configured yet.
update-manager depends on update-notifier; however:
Package update-notifier is not configured yet.
dpkg: error processing package update-manager (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcurl3-gnutls:amd64:
libcurl3-gnutls:amd64 depends on libgssapi-krb5-2 (>= 1.17); however:
Package libgssapi-krb5-2:amd64 is not configured yet.
dpkg: error processing package libcurl3-gnutls:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-common:
software-properties-common depends on ca-certificates; however:
Package ca-certificates is not configured yet.
dpkg: error processing package software-properties-common (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-qt:
ubuntu-release-upgrader-qt depends on ubuntu-release-upgrader-core (= 1:20.04.41); however:
Package ubuntu-release-upgrader-core is not configured yet.
dpkg: error processing package ubuntu-release-upgrader-qt (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpython3.8:amd64:
libpython3.8:amd64 depends on libpython3.8-stdlib (= 3.8.10-0ubuntu1~20.04.7); however:
Package libpython3.8-stdlib:amd64 is not configured yet.
dpkg: error processing package libpython3.8:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-ldb:
python3-ldb depends on libpython3.8 (>= 3.8.2); however:
Package libpython3.8:amd64 is not configured yet.
dpkg: error processing package python3-ldb (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of git:
git depends on libcurl3-gnutls (>= 7.56.1); however:
Package libcurl3-gnutls:amd64 is not configured yet.
dpkg: error processing package git (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lubuntu-update-notifier:
lubuntu-update-notifier depends on update-notifier-common; however:
Package update-notifier-common is not configured yet.
dpkg: error processing package lubuntu-update-notifier (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-qt:
software-properties-qt depends on software-properties-common; however:
Package software-properties-common is not configured yet.
dpkg: error processing package software-properties-qt (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vim:
vim depends on libpython3.8 (>= 3.8.2); however:
Package libpython3.8:amd64 is not configured yet.
dpkg: error processing package vim (--configure):
dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
libssl1.1:amd64
linux-headers-5.4.0-146-generic
linux-headers-generic
tzdata
grub-efi-amd64
libpam-systemd:amd64
libcurl4:amd64
libkrb5-3:amd64
ubuntu-advantage-tools
bind9-dnsutils
bind9-host
ubuntu-advantage-desktop-daemon
openssl
linux-headers-5.4.0-144-generic
xserver-xorg-legacy
tcpdump
libmysqlclient21:amd64
libpython3.8-minimal:amd64
libsnmp35:amd64
grub-efi-amd64-signed
linux-generic
bind9-libs:amd64
software-properties-gtk
dnsutils
shim-signed
python3-tz
ca-certificates
dbus-user-session
gnome-software
libgssapi-krb5-2:amd64
ubuntu-release-upgrader-core
update-manager-core
python3.8-minimal
ubuntu-release-upgrader-gtk
update-notifier
libpython3.8-stdlib:amd64
python3.8
snapd
google-chrome-stable
update-notifier-common
update-manager
libcurl3-gnutls:amd64
software-properties-common
ubuntu-release-upgrader-qt
libpython3.8:amd64
python3-ldb
git
lubuntu-update-notifier
software-properties-qt
vim
Processing was halted because there were too many errors.
Setting up libssl1.1:amd64 (1.1.1f-1ubuntu2.17) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libssl1.1:amd64 (--configure):
installed libssl1.1:amd64 package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of linux-headers-5.4.0-146-generic:
linux-headers-5.4.0-146-generic depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package linux-headers-5.4.0-146-generic (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
linux-headers-generic depends on linux-headers-5.4.0-146-generic; however:
Package linux-headers-5.4.0-146-generic is not configured yet.
dpkg: error processing package linux-headers-generic (--configure):
dependency problems - leaving unconfigured
Setting up tzdata (2022g-0ubuntu0.20.04.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package tzdata (--configure):
installed tzdata package post-installation script subprocess returned error exit status 1
Setting up grub-efi-amd64 (2.06-2ubuntu14.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package grub-efi-amd64 (--configure):
installed grub-efi-amd64 package post-installation script subprocess returned error exit status 1
Setting up libpam-systemd:amd64 (245.4-4ubuntu3.20) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libpam-systemd:amd64 (--configure):
installed libpam-systemd:amd64 package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of libcurl4:amd64:
libcurl4:amd64 depends on libssl1.1 (>= 1.1.1); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package libcurl4:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkrb5-3:amd64:
libkrb5-3:amd64 depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package libkrb5-3:amd64 (--configure):
dependency problems - leaving unconfigured
Setting up ubuntu-advantage-tools (27.13.6~20.04.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package ubuntu-advantage-tools (--configure):
installed ubuntu-advantage-tools package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of bind9-dnsutils:
bind9-dnsutils depends on libkrb5-3 (>= 1.6.dfsg.2); however:
Package libkrb5-3:amd64 is not configured yet.
bind9-dnsutils depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package bind9-dnsutils (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bind9-host:
bind9-host depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package bind9-host (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-advantage-desktop-daemon:
ubuntu-advantage-desktop-daemon depends on ubuntu-advantage-tools; however:
Package ubuntu-advantage-tools is not configured yet.
dpkg: error processing package ubuntu-advantage-desktop-daemon (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openssl:
openssl depends on libssl1.1 (>= 1.1.1); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package openssl (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-5.4.0-144-generic:
linux-headers-5.4.0-144-generic depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
dpkg: error processing package linux-headers-5.4.0-144-generic (--configure):
dependency problems - leaving unconfigured
Setting up xserver-xorg-legacy (2:1.20.13-1ubuntu1~20.04.6) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package xserver-xorg-legacy (--configure):
installed xserver-xorg-legacy package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of tcpdump:
tcpdump depends on libssl1.1 (>= 1.1.0); however:
Package libssl1.1:amd64 is not configured yet.
Package operation failed
The installation or removal of a software package failed.
```

---

### Post by Bashing-om on 2023-03-27
77_GCSX; Hello

Sure - it is ubuntu and always fixable - but the road may be long and hard .. and we can be expected to be "put away wet, may times".

Let the package manager do its job. We must get the install into a stable condition.
In terminal run:
```

sudo apt autoclean # only removes files that cannot be downloaded anymore (obsolete files)
sudo apt autoremove
sudo apt clean
sudo apt update #resync package index
sudo apt upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,A dist-upgrade will install new dependencies for packages already installed and may remove packages if they are no longer needed. This will not bring you to a new release of ubuntu. 
sudo apt-get dist-upgrade
sudo apt -f install
sudo dpkg --configure -a #where here we can expect to see what the package manager is unhappy about and the advise to try and resolve.

```

reboot to see the effect and again run
```

sudo apt update
sudo apt upgrade

```
to see how stable we are.
we strive to see:
> 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

If errors reported - time to also start reading logs :D 

[INDENT]here; patience is the virtue
[/INDENT]

---

### Post by guiverc on 2023-03-27
I'd have appreciated it if your *long paste* had included the command you executed that resulted in that output.

It's long and I wondered if it was from a [subsequent] `apt full-upgrade` OR the initial `do-release-upgrade`, but you didn't say.  Rather than us *guess*, it's best if we're told, just in case we *guess* wrongly.

I agree with @Bashing-om in that with some effort, almost all problems can be fixed. I'll suggest you follow his advice, as I'd want to know if you've rebooted; what command you executed etc. before I offered advice.


FYI:   I performed a couple of *release-upgrades* of a system I'd ignored (*rarely used thus was forgotten*), and on after the second (*or third*) LTS to LTS *release-upgrade* (*I'm skipping the reboot, test etc step*s) it looked like I had problems... as the *local* time was >2345 (*approaching midnight*) I decided I didn't want to deal with it then (*I'd also not miss the box anyway; I only used it as a media-player*), so I turned it off  and was going to look later.  In my case, my planned *fix* for the box I was expecting to be a *non-destructive re-install *so I ensured I wrote the ISO of the release I wanted on the box to thumb-drive, then booted box to explore how 'broken' it was, before my re-install. On this cold boot I could find nothing wrong... None of the 'breakage' I recall seeing before it was turned off.

Anyway the point of my *'story**'* was not the story in itself... but my planned ***fallback*** to the fix was going to be a non-destructive re-install, or as I like thinking it, an *upgrade via re-install*. In Lubuntu it's called "*upgrade using existing partition*" in their QA testcases/checklist ; refer [https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743](https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743) (*and search *"Install using existing partition:").  

This [*non-destructive re-install*] would be what I'd keep as your *fallback/backup* if you *give-up* trying to fix the issues, decide you don't have the time & need it work etc, or are just lazy. It's only *QA-tested* to work with Ubuntu packages (*ie. from official Ubuntu repositories; not third party*), so if you've many 3rd party packages it may or may not work as well (*it'll depend on what packages, whom created them & if they packaged with intention to upgrade or not*).

I was tempted to use that method anyway as it would have allowed me to perform the multi-*release-upgrade* steps in a single far faster/clean step, taking less than 1/10th of the total time... The only reason I didn't was my box was originally *xenial* or 16.04 & included Ubuntu Desktop (ie. Unity 7) as well as other DEs (inc. Xubuntu, Lubuntu..) and I wanted to see the Unity 7 -> GNOME DE change suspicious it'll be the last time I ever see it.

Addendum:  [I]Did you read the release notes & note changes - [https://lubuntu.me/jammy-2-released/](https://lubuntu.me/jammy-2-released/)
I'm not saying this is your issue, but there are some differences documented [/I]

---

### Post by xinuzi on 2023-03-28
Here (Toshiba Satellite, 8 Gb ram, yr 2013), Lubuntu, the upgrade 20.04 to 22.04 LTS took looong but went very well in the end.
Confirming some install-questions along the way. 

Fancy animated Lubuntulogo @ startup + amazing jellyfish in clear, sparkling bright waters :-)
Fonts etc, clear/sharp.

Astonishing how fluently the newer system integrated applications and settings from the older one.

The only thing I had to do afterwards was to restore the previous mountpoint of an external NTFS drive that I had left attached (see other post) + some sound settings.

Maybe a few other configurations/settings will turn up as I go along.

But, everything looks and feels great for the moment.

---

### Post by Bashing-om on 2023-03-28
Thanks xinuz :D

For the confirmation and the good words.

[INDENT]behold - the process works
[/INDENT]

---

### Post by MAFoElffen on 2023-03-28
Just a sidenote. Please go to your first post and select "Edit Post" > Select "Go Advanced" > Select the text of your raw output (the error messages) to highlight them. > Select the "#" Icon to wrap the output with CODE Tags.

Raw Output and commands, not wrapped within code tags, do strange things to the forums software, and is hard for members to read. When I was a Moderator here, I spent a lot of time edtting and reformatting user posts that didn't do that. No longer a Moderator here, but feel for the current Moderators who still have to do that. Please save them from unnecessarily causing them more work. They will usually warn you the first time. Everyone here is volunteers. 

I am happy that everything went well for you... Please remember to mark this as "Solved" so that other may find what worked for you, to help resolve their own challenges.

---

### Post by xinuzi on 2023-03-30
> **MAFoElffen said:**
> 
I am happy that everything went well for you... Please remember to mark this as "Solved" so that other may find what worked for you, to help resolve their own challenges.

In general, us ordinary freepeoples, mark things 'solved' as we see them 'fit' so.
Not, on command ;)

Did the original poster get releave. That may be the Question in the End. ,)

---

### Post by 77_GCSX on 2023-04-05
> **guiverc said:**
> I'd have appreciated it if your *long paste* had included the command you executed that resulted in that output.

It's long and I wondered if it was from a [subsequent] `apt full-upgrade` OR the initial `do-release-upgrade`, but you didn't say.  Rather than us *guess*, it's best if we're told, just in case we *guess* wrongly.



Sorry about this...It was indeed the 'do-release-upgrade' as was as the apt-full-upgrade. As a matter of fact I can't really install (or uninstall) anything without receiving a LONG list of errors.

I am going to try looking into this tonight.

Fingers crossed.....

---

### Post by 77_GCSX on 2023-04-06
> **Bashing-om said:**
> 77_GCSX; Hello

Sure - it is ubuntu and always fixable - but the road may be long and hard .. and we can be expected to be "put away wet, may times".

Let the package manager do its job. We must get the install into a stable condition.
In terminal run:
```

sudo apt autoclean # only removes files that cannot be downloaded anymore (obsolete files)
sudo apt autoremove
sudo apt clean
sudo apt update #resync package index
sudo apt upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,A dist-upgrade will install new dependencies for packages already installed and may remove packages if they are no longer needed. This will not bring you to a new release of ubuntu. 
sudo apt-get dist-upgrade
sudo apt -f install
sudo dpkg --configure -a #where here we can expect to see what the package manager is unhappy about and the advise to try and resolve.

```

reboot to see the effect and again run
```

sudo apt update
sudo apt upgrade

```
to see how stable we are.
we strive to see:

If errors reported - time to also start reading logs :D [INDENT]here; patience is the virtue
[/INDENT]



Soooo, how's THIS output:

sudo apt update

[COLOR=#FF0000]Hit:1 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease[/COLOR]
[COLOR=#FF0000]Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]                  [/COLOR]
[COLOR=#FF0000]Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease                                                                  [/COLOR]
[COLOR=#FF0000]Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease[/COLOR]
[COLOR=#FF0000]Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease [108 kB][/COLOR]
[COLOR=#FF0000]Fetched 218 kB in 16s (13.3 kB/s) [/COLOR]
[COLOR=#FF0000]Reading package lists... Done[/COLOR]
[COLOR=#FF0000]Building dependency tree... Done[/COLOR]
[COLOR=#FF0000]Reading state information... Done[/COLOR]
[COLOR=#FF0000]All packages are up to date.[/COLOR]


sudo apt upgrade

[COLOR=#FF0000]Reading package lists... Done[/COLOR]
[COLOR=#FF0000]Building dependency tree... Done[/COLOR]
[COLOR=#FF0000]Reading state information... Done[/COLOR]
[COLOR=#FF0000]Calculating upgrade... Done[/COLOR]
[COLOR=#FF0000]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


[/COLOR]I'd say we're good for a little while now!:D

---

### Post by Bashing-om on 2023-04-06
77_GCSX; Yeah >>

So far so good :D

So now what release are you showing:
post back - between code tags - the result of:
```

lsb_release -a

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]see where we go from here
[/INDENT]

---

