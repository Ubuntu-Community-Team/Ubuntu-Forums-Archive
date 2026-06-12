---
title: "Update will not complete"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by theduke0 on 2008-01-20
I just when I try to update my computer, update manager give me the following error:  

E: /var/cache/apt/archives/libdb4.4_4.4.20-8.1ubuntu3.1_i386.deb: files list file for package `psmisc' is missing final newline

When I run the command 'sudo apt-get upgrade' from the terminal window, I get this message:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  avahi-autoipd avahi-daemon cupsys cupsys-bsd cupsys-client cupsys-common deskbar-applet evolution-data-server
  evolution-data-server-common gimp gimp-data gimp-python kdebase-bin kdebase-kio-plugins kdesktop libapache2-mod-php5
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1
  libavahi-qt3-1 libboost-date-time1.34.1 libboost-filesystem1.34.1 libboost-python1.34.1 libboost-thread1.34.1
  libcamel1.2-10 libcupsimage2 libcupsys2 libdb4.4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 libgimp2.0 libkonq4 libpq5
  libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libsnmp-base libsnmp10 libxfont1 libxml2
  libxml2-utils openssh-client php-pear php5 php5-cli php5-common php5-mysql python-libxml2 ssh-askpass-gnome tomboy
  xserver-xorg-core
61 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/33.8MB of archives.
After unpacking 901kB of additional disk space will be used.
Do you want to continue [Y/n]? yes
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libdb4.4_4.4.20-8.1ubuntu3.1_i386.deb (--unpack):
 files list file for package `psmisc' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libdb4.4_4.4.20-8.1ubuntu3.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Any idea what I can do to fix this?

---

### Post by ryza on 2008-06-27
I had similar problem after crash due to bad memory module.
system looked ok, but every time i tried update update manager or synaptic manager and got 
E: /var/cache/apt/archives/libssl0.9.8_0.9.8g-4ubuntu3.3_i386.deb: files list file for package `libegroupwise1.2-13' is missing final newline
same when  tried sudo get-apt -f update.
tried remove package libe.. and same error
solution was here 
[https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html)

for simple went into var/lib/dpkg/info and there was this file "libegroupwise1.2-13.list" tried to edit it and it was corrupt.

 so put in terminal: sudo rm var/lib/dpkg/info/libegroupwise1.213.list to remove it
 after that went into update manager.. got another error 
this time cupsys-common was missing newline.. looked into info and same thing.. removed that and update manager worked.. so then just reinstalled libegroupwise in synaptic..and so far it works..

btw psmics.list is in info and can be edited in editor

hope this helps

---

