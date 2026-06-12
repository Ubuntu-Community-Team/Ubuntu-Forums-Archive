---
title: "dpkg error when upgrading likewise-opn"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by kayvee on 2011-04-19
I recently upgraded from Maverick to Natty. The upgrade process went fine and I am able to log in to Natty and use my computer fine. However, during the installation there was an error upgrading likewise-open from 5.0.xx to 6.0.xx. I thought perhaps removing likewise-open 5.0.xx and installing 6.0.xx (instead of upgrading) may fix the problem. Alas, that did not work. This what I get: 
```

(Reading database ... 475957 files and directories currently installed.)
Unpacking likewise-open (from .../likewise-open_6.0.0.53010-4ubuntu5_amd64.deb) ...
Warning: /etc/init.d/lsassd stop returned 1
/etc/init.d/lsassd: line 24: /usr/lib/likewise-open/init-lwsm.sh: No such file or directory

/var/lib/dpkg/tmp.ci/preinst: line 155: return: can only `return' from a function or sourced script
dpkg: error processing /var/cache/apt/archives/likewise-open_6.0.0.53010-4ubuntu5_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/likewise-open_6.0.0.53010-4ubuntu5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please help me fix it...

---

### Post by Dutch70 on 2011-04-19
Have you tried running these 2 commands? 
```
sudo dpkg --configure -a
```
```
sudo apt-get install -f
```

---

### Post by kayvee on 2011-04-19
I just did. Here's the output
```

vamsi@cistron:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of amazonmp3:i386:
 amazonmp3:i386 depends on libgtkmm-2.4-1c2a.
 amazonmp3:i386 depends on libglademm-2.4-1c2a.
 amazonmp3:i386 depends on libboost-filesystem1.34.1.
 amazonmp3:i386 depends on libboost-regex1.34.1.
 amazonmp3:i386 depends on libboost-thread1.34.1.
 amazonmp3:i386 depends on libboost-iostreams1.34.1.
 amazonmp3:i386 depends on libboost-signals1.34.1.
 amazonmp3:i386 depends on libboost-date-time1.34.1.
 amazonmp3:i386 depends on libcurl3.
 amazonmp3:i386 depends on libssl0.9.8.
 amazonmp3:i386 depends on xdg-utils.
dpkg: error processing amazonmp3:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amazonmp3:i386

```

I believe those errors concerning amazonmp3 are unrelated to my likewise-open issue. Am I right? 

```

vamsi@cistron:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ada-reference-manual libdb-je-java krb5-user libfolks0 libdb4.7-java
  libgcj-bc gcj-4.4-base libknewstuff2-4 libicu42 libjtidy-java libkipi7
  libicu4j-java libdb4.7-java-gcj libcommons-beanutils-java msr-tools g++-4.4
  libtelepathy-logger1 krb5-config libpvm3 libdns66 libedata-cal1.2-7
  gcj-4.4-jre-lib libkexiv2-8 libexiv2-6 libcommons-compress-java
  firefox-branding libfolks-telepathy0 libgcj10 libgcj11 cpu-checker
  libgssrpc4 libindicate4 libzltext0.10 libx264-98 libdbusmenu-glib1
  libgwibber0 libqt4-mendeley-svg libindicate0.1-cil libmatroska2 libkrossui4
  libdbusmenu-gtk1 libpoppler7 libiptcdata0 lm-sensors gcj-4.5-base
  libpoppler-glib5 libpano13-1 libwildmidi0 pvm fancontrol gcj-4.5-jre-lib
  docbook-xsl-doc-html libgdata7 libgdata1.4-cil libkadm5clnt-mit7
  libregexp-java libxdot4 biosquid libisccfg60 libsoundtouch1c2
  liblucene2-java libgcj-common libisc60 libcommons-digester-java libebml2
  libzlcore0.10 libjline-java libkdcraw8 autopano-sift python-kde4
  libstdc++6-4.4-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Dutch70 on 2011-04-19
Maybe these links will bring up some info.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=692590[/COLOR]]("http://ubuntuforums.org/showthread.php?t=692590")
[[COLOR="RoyalBlue"]http://www.likewise.com/community/index.php/forums/viewthread/824/[/COLOR]]("http://www.likewise.com/community/index.php/forums/viewthread/824/")

---

### Post by kayvee on 2011-04-20
Thanks for the links. Even after going through them and trying solutions proposed therein, I have the same problem. In fact, now I have an additional issue with the installation of apport and apport-gtk. 

```

Setting up apport (1.20.1-0ubuntu4) ...
start: Job failed to start
invoke-rc.d: initscript apport, action "start" failed.
dpkg: error processing apport (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured

```

---

### Post by lucasrangit on 2011-08-02
> **kayvee said:**
> I recently upgraded from Maverick to Natty. The upgrade process went fine and I am able to log in to Natty and use my computer fine. However, during the installation there was an error upgrading likewise-open from 5.0.xx to 6.0.xx. I thought perhaps removing likewise-open 5.0.xx and installing 6.0.xx (instead of upgrading) may fix the problem. Alas, that did not work. This what I get: 
```

(Reading database ... 475957 files and directories currently installed.)
Unpacking likewise-open (from .../likewise-open_6.0.0.53010-4ubuntu5_amd64.deb) ...
Warning: /etc/init.d/lsassd stop returned 1
/etc/init.d/lsassd: line 24: /usr/lib/likewise-open/init-lwsm.sh: No such file or directory

/var/lib/dpkg/tmp.ci/preinst: line 155: return: can only `return' from a function or sourced script
dpkg: error processing /var/cache/apt/archives/likewise-open_6.0.0.53010-4ubuntu5_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/likewise-open_6.0.0.53010-4ubuntu5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please help me fix it...

According to [https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/771773](https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/771773) the solution is to use dash instead of bash. This worked for me using Ubuntu 11.04

```
sudo dpkg-reconfigure dash
```

---

