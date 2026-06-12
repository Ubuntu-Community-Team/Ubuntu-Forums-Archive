---
title: "Natty upgrade -- gnome-panel-data won't install -- seems corrupted"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by jeffsf on 2011-05-04
On upgrade from Maverick to Natty, gnome-panel-data did not install properly. It appears that things are pretty well mucked up, as dpkg seemingly won't remove it.

```
jeff@fx:~$ sudo apt-get install --reinstall gnome-panel-data
[sudo] password for jeff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfolks0 libicu42 quadrapassel libdbusmenu-glib1 msr-tools gcc-4.4-multilib libdns66 libedata-cal1.2-7 openoffice.org-l10n-common libexiv2-6 gcj-4.4-jre-lib
  libgcj10 cpu-checker libfolks-telepathy0 libx264-98 gcj-4.4-base libkprintutils4 libgwibber0 libdbusmenu-gtk1 libtelepathy-logger1 libkrossui4 libgluezilla
  libpoppler7 docbook-xsl-doc-html python2.6-dev fancontrol libgdata7 libxdot4 libisccfg60 openoffice.org-l10n-en-gb libindicate4 firefox-branding libisc60
  libebml2 libvala-0.10-0 libesmtp5 libmatroska2 libkutils4 libpoppler-glib5
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  gnome-panel-data
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
8 not fully installed or removed.
Need to get 0 B/266 kB of archives.
After this operation, 496 kB disk space will be freed.
(Reading database ... 373478 files and directories currently installed.)
Preparing to replace gnome-panel-data 1:2.30.2-1ubuntu3 (using .../gnome-panel-data_1%3a2.32.1-0ubuntu6.4_all.deb) ...
Unpacking replacement gnome-panel-data ...
dpkg (subprocess): unable to execute old post-removal script (/var/lib/dpkg/info/gnome-panel-data.postrm): Permission denied
dpkg: warning: subprocess old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
dpkg: error processing /var/cache/apt/archives/gnome-panel-data_1%3a2.32.1-0ubuntu6.4_all.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/preinst': Is a directory
Processing triggers for gconf2 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-panel-data_1%3a2.32.1-0ubuntu6.4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

``````
jeff@fx:~$ sudo dpkg --purge --force-depends gnome-panel-data
dpkg: error processing gnome-panel-data (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 gnome-panel-data

```It may be that /var/lib/dpkg/info/gnome-panel-data* has gotten corrupted:

```
jeff@fx:~$ ls -lR /var/lib/dpkg/info/gnome-panel-data*
-rw-r--r-- 1 root root  19529 2011-05-04 08:52 /var/lib/dpkg/info/gnome-panel-data.list
-rw-r--r-- 1 root root  11157 2011-04-21 06:23 /var/lib/dpkg/info/gnome-panel-data.md5sums
-rw-r--r-- 1 root root 154628 2010-12-20 09:40 /var/lib/dpkg/info/gnome-panel-data.postinst

/var/lib/dpkg/info/gnome-panel-data.conffiles:
total 456
-rw-r--r-- 2 root root 154628 2011-01-25 21:08 signal_noise.rrd
-rw-r--r-- 2 root root 154628 2011-01-25 21:08 signal_power.rrd
-rw-r--r-- 2 root root 154628 2011-01-25 21:08 signal_quality.rrd

/var/lib/dpkg/info/gnome-panel-data.postrm:
total 12
-rw-r--r-- 1 root root 1116 2010-11-22 01:31 audio-call.png
-rw-r--r-- 1 root root 1824 2010-11-22 01:31 select-avatar.png
-rw-r--r-- 1 root root 1641 2010-11-22 01:31 video-call.png

/var/lib/dpkg/info/gnome-panel-data.preinst:
total 16
drwxr-xr-x 2 root root 4096 2010-12-17 15:11 interface
drwxr-xr-x 2 root root 4096 2010-12-17 15:11 load
drwxr-xr-x 2 root root 4096 2010-12-17 15:11 wireless-mon.wlan0
drwxr-xr-x 2 root root 4096 2010-12-17 15:11 wireless-wlan0

/var/lib/dpkg/info/gnome-panel-data.preinst/interface:
total 1824
-rw-r--r-- 1 root root 307452 2011-01-25 21:08 if_errors-br-lan.rrd
-rw-r--r-- 1 root root 307452 2011-01-25 21:08 if_errors-wlan0.rrd
-rw-r--r-- 1 root root 307452 2011-01-25 21:08 if_octets-br-lan.rrd
-rw-r--r-- 1 root root 307452 2011-01-25 21:08 if_octets-wlan0.rrd
-rw-r--r-- 1 root root 307452 2011-01-25 21:08 if_packets-br-lan.rrd
-rw-r--r-- 1 root root 307452 2011-01-25 21:08 if_packets-wlan0.rrd

/var/lib/dpkg/info/gnome-panel-data.preinst/load:
total 452
-rw-r--r-- 1 root root 460276 2011-01-25 21:08 load.rrd

/var/lib/dpkg/info/gnome-panel-data.preinst/wireless-mon.wlan0:
total 456
-rw-r--r-- 2 root root 154628 2011-01-25 21:08 signal_noise.rrd
-rw-r--r-- 2 root root 154628 2011-01-25 21:08 signal_power.rrd
-rw-r--r-- 2 root root 154628 2011-01-25 21:08 signal_quality.rrd

/var/lib/dpkg/info/gnome-panel-data.preinst/wireless-wlan0:
total 456
-rw-r--r-- 2 root root 154628 2011-01-25 21:08 signal_noise.rrd
-rw-r--r-- 2 root root 154628 2011-01-25 21:08 signal_power.rrd
-rw-r--r-- 2 root root 154628 2011-01-25 21:08 signal_quality.rrd

```Any suggestions on how to proceed here to get things straightened out so that I can complete the upgrade?

---

