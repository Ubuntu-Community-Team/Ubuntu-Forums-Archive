---
title: "apt-get fails on cupsys, tzdata, and others"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by kuantum_fizax on 2008-02-19
So, i've had this problem since last December or so, but no one could help me then. I figured I'd give it another go.

When I try to execute apt-get upgrade (or try to install any new package using apt-get), it fails. This started with it failing on the package cupsys-bsd, and eventually other packages started being listed as failing.  

I've previously been directed to some old problem in which tzdata causes a problem, in which the solution was to change your timezone to london. This never worked for me. I've also tried changing my mirror and clearing the cache in the synaptic package manager. No luck. I haven't been able to install a new package in months. I would prefer not to need to reinstall ubuntu, but its getting to that point.

Thanks for any help!

When running apt-get update and then apt-get upgrade, I get:
```
sudo apt-get upgrade |tee upgrade.log
Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be upgraded:
  app-install-data-commercial avahi-autoipd avahi-daemon bind9-host comerr-dev
  cupsys cupsys-bsd cupsys-client cupsys-common deskbar-applet dnsutils
  e2fslibs e2fsprogs evolution-data-server evolution-data-server-common
  findutils firefox firefox-gnome-support flashplugin-nonfree ghostscript
  ghostscript-x gimp gimp-data gimp-python kdelibs-data kdelibs4c2a
  libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1 libavahi-qt3-1
  libbind9-30 libblkid1 libboost-signals1.34.1 libcairo2 libcamel1.2-10
  libcomerr2 libcupsimage2 libcupsys2 libcupsys2-dev libdb4.4 libdns32
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13
  libexchange-storage1.2-3 libgd2-xpm libgimp2.0 libgs8 libisc32 libisccc30
  libisccfg30 libkpathsea4 liblwres30 libmono-cairo1.0-cil
  libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil
  libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil
  libmono-system2.0-cil libmono0 libmono2.0-cil libpt-1.10.0
  libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libpulse0
  libsmbclient libsnmp-base libsnmp10 libss2 libuuid1 libxfont1 libxml2
  libxml2-utils linux-headers-2.6.22-14 linux-headers-2.6.22-14-generic
  linux-image-2.6.22-14-generic linux-libc-dev mono-common mono-gac mono-jit
  mono-runtime openssh-client python-libxml2 samba-common smbclient
  ssh-askpass-gnome tomboy xserver-xorg-core xserver-xorg-video-intel
102 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
10 not fully installed or removed.
Need to get 0B/101MB of archives.
After unpacking 950kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Extracting templates from packages: 100%
Preconfiguring packages ...
cupsys failed to preconfigure, with exit status 1
flashplugin-nonfree failed to preconfigure, with exit status 1
samba-common failed to preconfigure, with exit status 1
cupsys-bsd failed to preconfigure, with exit status 1
Setting up tzdata (2007k-0ubuntu0.7.10) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by benfindlay on 2008-02-19
Have you tried ```
sudo apt-get -f install
``` or ```
sudo dpkg --configure --pending
``` or```
sudo dpkg --configure --a
``` just to make sure nothing is still pending installation? If you get a result from this, try reinstalling those pacakges again!

Hope this helps!

---

### Post by kuantum_fizax on 2008-02-20
I'm not really familiar with dpkg, so I hadn't tried those two.  I also don't know how to reinstall by the command line. It always fails when I try to reinstall anything with the gui package manager, giving similar errors to when I try to do an update.

When I do apt-get install, I get:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 102 not upgraded.
10 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up tzdata (2007k-0ubuntu0.7.10) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 1
Setting up cupsys (1.3.2-1ubuntu7.1) ...
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gdm (2.20.1-0ubuntu1) ...
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 1
Setting up nethack-common (3.4.3-10.1ubuntu3) ...
dpkg: error processing nethack-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nethack-gnome:
 nethack-gnome depends on nethack-common (= 3.4.3-10.1ubuntu3); however:
  Package nethack-common is not configured yet.
dpkg: error processing nethack-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nethack-qt:
 nethack-qt depends on nethack-common (= 3.4.3-10.1ubuntu3); however:
  Package nethack-common is not configured yet.
dpkg: error processing nethack-qt (--configure):
 dependency problems - leaving unconfigured
Setting up samba-common (3.0.26a-1ubuntu2.2) ...
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 3.0.26a-1ubuntu2.2); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
Setting up cupsys-bsd (1.3.2-1ubuntu7.1) ...
dpkg: error processing cupsys-bsd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tzdata
 cupsys
 flashplugin-nonfree
 gdm
 nethack-common
 nethack-gnome
 nethack-qt
 samba-common
 smbclient
 cupsys-bsd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

when doing 
dpkg --configure --pending
```

Setting up gdm (2.20.1-0ubuntu1) ...
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 1
Setting up tzdata (2007k-0ubuntu0.7.10) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 1
Setting up cupsys-bsd (1.3.2-1ubuntu7.1) ...
dpkg: error processing cupsys-bsd (--configure):
 subprocess post-installation script returned error exit status 1
Setting up samba-common (3.0.26a-1ubuntu2.2) ...
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 3.0.26a-1ubuntu2.2); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Setting up nethack-common (3.4.3-10.1ubuntu3) ...
dpkg: error processing nethack-common (--configure):
 subprocess post-installation script returned error exit status 1
Setting up cupsys (1.3.2-1ubuntu7.1) ...
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nethack-gnome:
 nethack-gnome depends on nethack-common (= 3.4.3-10.1ubuntu3); however:
  Package nethack-common is not configured yet.
dpkg: error processing nethack-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nethack-qt:
 nethack-qt depends on nethack-common (= 3.4.3-10.1ubuntu3); however:
  Package nethack-common is not configured yet.
dpkg: error processing nethack-qt (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gdm
 tzdata
 cupsys-bsd
 samba-common
 smbclient
 flashplugin-nonfree
 nethack-common
 cupsys
 nethack-gnome
 nethack-qt

```

And with the  sudo dpkg --reconfigure --a, it doesn't seem to recognize the command.
```

[dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

```
and it doesn't seem to recognize that last one

---

### Post by benfindlay on 2008-02-20
sorry that should have been ```
sudo dpkg --configure -a
```

Any joy?

---

### Post by kuantum_fizax on 2008-02-20
Thanks for the help. It says it doesn't recognize the option --a.

```

~$ sudo dpkg --configure --a 
dpkg: unknown option --a

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

```

---

### Post by Partyboi2 on 2008-02-20
the correct one is
```
sudo dpkg --configure -a
```

---

### Post by kuantum_fizax on 2008-02-21
Heh, okay sorry. Silly error. 

Anyways, it looks like that produces the same errors as doing dpkg --configure -pending.

 It seems the problem originates from tzdata or cupsys-bsd. Forcing an uninstall, then reinstalling, seems like a good idea. However, it says these are core packages when in package manager, and that it would be bad to uninstall them...

Thanks for all the suggestions so far guys. Any other suggestions?

---

### Post by kuantum_fizax on 2008-02-26
No other help? :(.

I guess I'll need to reinstall from scratch. Maybe I'll try red hat since ubuntu didn't work for me...

---

### Post by Partyboi2 on 2008-02-26
> **kuantum_fizax said:**
> No other help? :(.

I guess I'll need to reinstall from scratch. Maybe I'll try red hat since ubuntu didn't work for me...
A reinstall should fix the problem. You could move your home folder to its own partition then reinstall ubuntu. That way what ever is in your home partition will not be deleted. 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by djmaxmalta on 2008-02-27
hey guys i don't know if this should be here i am on ubuntu 6.06.01 nad i have the source code for amsn, pidgin, ff2.12, etc... but how can i install them? my pc can take hemm

---

### Post by Partyboi2 on 2008-02-28
> **djmaxmalta said:**
> hey guys i don't know if this should be here i am on ubuntu 6.06.01 nad i have the source code for amsn, pidgin, ff2.12, etc... but how can i install them? my pc can take hemm[this]("http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually") will explain how to install them from source. Or you can use add/remove under "Applications" to install the current one that is available in the dapper repo's

---

