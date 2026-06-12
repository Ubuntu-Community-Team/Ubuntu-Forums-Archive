---
title: "libglib2.0-0: 64 and 32 bit versions blocking each other in 12.04"
date: 2012-08-09
forum: Installation &amp; Upgrades
---

### Post by AdrianMay on 2012-08-09
Hi folks,

Take a look at this:

```

root@bluefin:/home/ad# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libxrandr-dev libxdamage-dev libxfixes-dev x11proto-xinerama-dev libxi-dev libpixman-1-dev x11proto-randr-dev libxinerama-dev libpcrecpp0 libpcrecpp0:i386 x11proto-fixes-dev libcairo-script-interpreter2 x11proto-damage-dev zlib1g-dev:i386 libxcb-shm0-dev libxml2-dev
  libc6-dev:i386 libxcomposite-dev libxcb-render0-dev libpcre3-dev x11proto-composite-dev linux-libc-dev:i386 libxcursor-dev libpng12-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libglib2.0-0:i386 libglib2.0-bin
The following packages will be upgraded:
  libglib2.0-0:i386 libglib2.0-bin
2 upgraded, 0 newly installed, 0 to remove and 493 not upgraded.
3 not fully installed or removed.
Need to get 0 B/1,227 kB of archives.
After this operation, 16.4 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: error processing libglib2.0-0 (--configure):
 libglib2.0-0:amd64 2.32.3-0ubuntu1 cannot be configured because libglib2.0-0:i386 is in a different version (2.32.1-0ubuntu2)
dpkg: error processing libglib2.0-0:i386 (--configure):
 libglib2.0-0:i386 2.32.1-0ubuntu2 cannot be configured because libglib2.0-0:amd64 is in a different version (2.32.3-0ubuntu1)
dpkg: dependency problems prevent configuration of libglib2.0-bin:
 libglib2.0-bin depends on libglib2.0-0 (= 2.32.1-0ubuntu2); however:
  Version of libglib2.0-0 on system is 2.32.3-0ubuntu1.
dpkg: error processing libglib2.0-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Errors were encountered while processing:
 libglib2.0-0
 libglib2.0-0:i386
 libglib2.0-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The interesting bit is:


```

dpkg: error processing libglib2.0-0 (--configure):
 libglib2.0-0:amd64 2.32.3-0ubuntu1 cannot be configured because libglib2.0-0:i386 is in a different version (2.32.1-0ubuntu2)
dpkg: error processing libglib2.0-0:i386 (--configure):
 libglib2.0-0:i386 2.32.1-0ubuntu2 cannot be configured because libglib2.0-0:amd64 is in a different version (2.32.3-0ubuntu1)

```

I've tried everything imaginable to fix this and nothing helps. For instance:

```

apt-get -f install libglib2.0-bin=2.32.1-0ubuntu2 libglib2.0-0=2.32.1-0ubuntu2 libglib2.0-0:i386=2.32.1-0ubuntu2 libglib2.0-0:amd64=2.32.1-0ubuntu2

```
and
```

apt-get -f install libglib2.0-bin=2.32.3-0ubuntu1 libglib2.0-0=2.32.3-0ubuntu1 libglib2.0-0:i386=2.32.3-0ubuntu1 libglib2.0-0:amd64=2.32.3-0ubuntu1

```

but it always comes back to the same problem. I'd try aptitude but I can't install it anymore than I can install anything else right now. Here are some other bits of possibly relevant info:

```

> apt-cache policy libglib2.0-0                                                                                                                                                                                                                    
libglib2.0-0:
  Installed: 2.32.3-0ubuntu1
  Candidate: 2.32.3-0ubuntu1
  Version table:
 *** 2.32.3-0ubuntu1 0
        500 http://ftp.iinet.net.au/linux/ubuntu/ precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2.32.1-0ubuntu2 0
        500 http://ftp.iinet.net.au/linux/ubuntu/ precise/main amd64 Packages

> apt-cache policy libglib2.0-0:i386                                                                                                                                                                                                               
libglib2.0-0:i386:
  Installed: 2.32.1-0ubuntu2
  Candidate: 2.32.3-0ubuntu1
  Version table:
     2.32.3-0ubuntu1 0
        500 http://ftp.iinet.net.au/linux/ubuntu/ precise-updates/main i386 Packages
 *** 2.32.1-0ubuntu2 0
        500 http://ftp.iinet.net.au/linux/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status

```

/etc/apt/sources.list:

```

deb http://ftp.iinet.net.au/linux/ubuntu/ precise main restricted
deb-src http://ftp.iinet.net.au/linux/ubuntu/ precise main restricted
deb http://ftp.iinet.net.au/linux/ubuntu/ precise-updates main restricted
deb-src http://ftp.iinet.net.au/linux/ubuntu/ precise-updates main restricted
deb http://ftp.iinet.net.au/linux/ubuntu/ precise universe
deb-src http://ftp.iinet.net.au/linux/ubuntu/ precise universe
deb http://ftp.iinet.net.au/linux/ubuntu/ precise-updates universe
deb-src http://ftp.iinet.net.au/linux/ubuntu/ precise-updates universe
deb http://ftp.iinet.net.au/linux/ubuntu/ precise multiverse
deb-src http://ftp.iinet.net.au/linux/ubuntu/ precise multiverse
deb http://ftp.iinet.net.au/linux/ubuntu/ precise-updates multiverse
deb-src http://ftp.iinet.net.au/linux/ubuntu/ precise-updates multiverse
deb http://ftp.iinet.net.au/linux/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://ftp.iinet.net.au/linux/ubuntu/ precise-backports main restricted universe multiverse
deb http://ftp.iinet.net.au/linux/ubuntu precise-security main restricted
deb-src http://ftp.iinet.net.au/linux/ubuntu precise-security main restricted
deb http://ftp.iinet.net.au/linux/ubuntu precise-security universe
deb-src http://ftp.iinet.net.au/linux/ubuntu precise-security universe
deb http://ftp.iinet.net.au/linux/ubuntu precise-security multiverse
deb-src http://ftp.iinet.net.au/linux/ubuntu precise-security multiverse
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu karmic main

```

Please help. I'm desperate.
Adrian.

---

### Post by rwabel on 2012-08-21
I'm on 12.10, but get a very similar error

> Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of libglib2.0-bin:
 libglib2.0-bin depends on libglib2.0-0 (= 2.33.8-1ubuntu1); however:
  Version of libglib2.0-0:amd64 on system is 2.33.8-1+svn2.

dpkg: error processing libglib2.0-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 libglib2.0-bin


I hope the dependency gets fixed soon

---

