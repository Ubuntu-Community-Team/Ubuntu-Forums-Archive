---
title: "Updating 12.04 to 12.10 (commandline) problems..."
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by edwardecl on 2012-11-13
I have a serious problem... while updating via command-line it got stuck at...

Setting up keyboard-configuration (1.70ubuntu6) ...

So I had to force quit DPKG...

So I ran dpkg --configure -a

which finished setting up a load of packages...

then run aptitude dist-upgrade to finish the install and hope that it gets passed the keyboard-configuration thing but not i get a load of dependency problems...

Errors were encountered while processing:
 memtest86+
 libpam-cap:i386
 bridge-utils
 libssl1.0.0:i386
 wpasupplicant
 ucf
 nfs-common
 openssl
 fdutils
 ubuntu-standard
 tftpd-hpa
 libpam-xdg-support:i386
 ntfs-3g
 apcupsd
 libvirtodbc0
 libqca2-plugin-ossl:i386
 libwvstreams4.6-extras
 gconf2-common
 resolvconf
 apcupsd-cgi
 php5-cgi
 python2.7
 vsftpd
 python-gps
 virtuoso-opensource-6.1-common
 php5-gd
 php5-sqlite
 snmp
 virtuoso-opensource-6.1-bin
 sysstat
 php5-xmlrpc
 python-pycurl
 python-appindicator
 ubuntuone-control-panel-qt
 python-cairo
 postfix
 gstreamer0.10-plugins-bad:i386
 python-keyring
 php5-curl
 libpam-gnome-keyring
 gconf-service-backend
 libfreerdp1
 libruby1.8
 cpuburn
 libsnmp15
 irssi
 tcpdump
 setserial
 python-vte
 socat
 python-gobject-2
Processing was halted because there were too many errors.

With errors for each like this one...

dpkg: error processing gconf-service-backend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libfreerdp1:
 libfreerdp1 depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0:i386 is not configured yet.

Any way of fixing this?

---

### Post by edwardecl on 2012-11-13
OK i found out the /var/cache/debconf/ dir was causing the problems...

So i removed everything inside... now when i run...

sudo apt-get install -f

It gets stuck on 

Setting up keyboard-configuration (1.70ubuntu6) ...

like before

how do I fix this problem?

---

### Post by edwardecl on 2012-11-13
Don't worry I figured it out...

For some reason keyboard-configure does not like my keyboard, unplugging my USB keyboard seems to have got around the issue...

Still a strange bug that needs looking at.

---

