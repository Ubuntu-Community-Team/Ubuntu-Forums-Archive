---
title: "Updates cannot access internet"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by triplemaya on 2010-11-03
Hi. Just did a fresh install of karmic due to problems with 10.04 and then 10.10. The new install sees the net ok, firefox and thunderbird work perfectly. however, updates not working. When i do sudo apt-get update it just hangs. When i open the ubuntu software center, nothing is available.
Help urgently required, as I can't operate without a number of software packages I now cannot install

---

### Post by triplemaya on 2010-11-03
well, sudo apt-get update doesn't hang forever, it produces a very long list of things it could not do, and cannot reach

---

### Post by Elfy on 2010-11-03
Try changing the server in sys -admin - software sources - ubuntu software tab - download from

It'd also be useful to see the errors ...

---

### Post by triplemaya on 2010-11-03
Thanks

"Try changing the server in sys -admin - software sources - ubuntu software tab - download from"

changed it from  server for uk
to main server



Errors

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_GB.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_GB.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_GB.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_GB.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_GB.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_GB.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_GB.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_GB.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_GB.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_GB.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_GB.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_GB.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Some index files failed to download, they have been ignored, or old ones used instead.




changed back to server for uk

errors were then

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_GB.bz2)  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_GB.bz2)  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_GB.bz2)  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_GB.bz2)  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_GB.bz2)  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_GB.bz2)  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_GB.bz2)  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_GB.bz2)  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_GB.bz2)  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_GB.bz2)  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_GB.bz2)  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_GB.bz2)  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Elfy on 2010-11-03
Are you using a proxy?

Post your sources list please.

```
cat /etc/apt/sources.list
```

---

### Post by triplemaya on 2010-11-03
I am not using a proxy as far as I know.

$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security multiverse

---

### Post by Elfy on 2010-11-03
Have a look in Synaptic - Settings - Preferences - Networks

It certainly looked like a proxy was involved to me.

You can change the server back if you wish - nothing wrong with the UK one as far as I can see.

---

### Post by triplemaya on 2010-11-03
Looked in Synaptic - Settings - Preferences - Networks
it says 'direct connection to the internet.

---

### Post by Elfy on 2010-11-03
Try getting a new clean sources.list - you can create on here

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

I am not sure what is going on there. 

This leads me to believe it's looking at a proxy. 
> Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...ic/Release.gpg](http://archive.ubuntu.com/ubuntu/dis...ic/Release.gpg) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)

Have you installed anything recently that deals with apt - I am sure I have seen similar - but can't get a sensible search result nor remember ...

---

### Post by sikander3786 on 2010-11-03
Probably a stupid question but are you actually able to browse the web?

Might be your gateway/router is not configured properly. Please post the output of

```
ip route
```

Might also be a proxy problem as forestpiskie mentioned above. Post the output of this one also.

```
cat /etc/apt/apt.conf
```

---

### Post by triplemaya on 2010-11-03
Thanks forestpiskie. I got a clean souces.list as you suggested. The error messages for update are now:

Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://uk.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_GB.bz2](http://uk.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_GB.bz2](http://uk.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_GB.bz2](http://uk.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_GB.bz2](http://uk.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://uk.archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_GB.bz2](http://uk.archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_GB.bz2](http://uk.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_GB.bz2](http://uk.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_GB.bz2](http://uk.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://uk.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_GB.bz2](http://uk.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_GB.bz2](http://uk.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_GB.bz2](http://uk.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_GB.bz2](http://uk.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg](http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg)  
Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_GB.bz2](http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_GB.bz2)  
Some index files failed to download, they have been ignored, or old ones used instead.


I have no recollection of installing anything to do with apt, certainly nothing recently.

---

### Post by triplemaya on 2010-11-03
Thanks sikander3786. 

$ ip route
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.3  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0  proto static 

$ cat /etc/apt/apt.conf
cat: /etc/apt/apt.conf: No such file or directory

---

### Post by triplemaya on 2010-11-03
ps, yes, can browse normally, no problem with firefox or thunderbird

---

### Post by sikander3786 on 2010-11-03
As the error message seems to me, now switching to some other Server preferably the Main server from System > Administration > Software Sources should sort out the issue.

And my ignorance, there is no apt.conf in Lucid so its output is abviously out of question.

---

### Post by triplemaya on 2010-11-03
ok. Did that, set it to Main Server, and it immediately downloaded a slew of files, which looked really good. However, these are the error messages at the end:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_GB.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
... etc for about 40 lines
Some index files failed to download, they have been ignored, or old ones used instead.

when I came to it the server was a new line I had not seen before, with a series of /s in. I went to try it again, but it was no longer available.

I then switched server to SErver for United Kingdom, many more files were downloaded successfully, and this time the errors were:


Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/karmic/Release.gpg](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/karmic/Release.gpg)  Could not connect to ppa.launchpad.net:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/karmic/main/i18n/Translation-en_GB.bz2](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/karmic/main/i18n/Translation-en_GB.bz2)  Could not connect to ppa.launchpad.net:80 (1.0.0.0). - connect (113: No route to host)
Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  Could not connect to ppa.launchpad.net:80 (1.0.0.0). - connect (113: No route to host)
Some index files failed to download, they have been ignored, or old ones used instead.


This time, though, the software centre sprang into action, which it did not before with the Main Server.
However, the software update manager now shows 323 files it would like to download, but none are successfully downloaded. instead, errors are:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.0-2ubuntu1.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.0-2ubuntu1.1_i386.deb)
  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]

for about , maybe, 323 messages!


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.97~beta4-1ubuntu4.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.97~beta4-1ubuntu4.1_i386.deb)
  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]

---

### Post by Elfy on 2010-11-03
Ok - try this - go to the software source thing again - change the server again - this time though go other and select best server.

I'm going to bow out though. Not helping much here.

I editd your post to add code tags.

---

### Post by sikander3786 on 2010-11-03
If you are unable to connect to any Server, try Google DNS.

[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)

ipv6 can also cause problems like that (??). You can set ipv6 to ignore by Right Clicking the Network Applet > Edit Connections, select your interface > Edit > ipv6 Settings > Method = Ignore.

---

### Post by triplemaya on 2010-11-03
Well, I did that forestpiskie, and just about everything is working. The update went fine, except for the repostory for ununtu tweak.

After that, the updates went ok, and all was updated.

Many Thanks. You have been a big help.

---

### Post by triplemaya on 2010-11-03
Thanks sikander3786

I seem to be connecting to a server now. (I tried everything under the sun to decomission spv6 earlier, but didn't seem to make any difference.)

My new, rather considerable problem is that open office now will not run!? It shows in the system monitor, but produces no windows. 
Originally it was working. Then, after the updates, synaptic reported it as not installed. I installed it, only to have it reported as running. This also happened before during the updates. Once again, went to system monitor and killed it. restarted. it is running, but silently. I'm looking to use it more as a GUI application.

---

### Post by triplemaya on 2010-11-03
uninstalled it all and resintalled. Problem seemed to be associated with a previous profile. This was resolved by deleting ~/.openoffice

Thanks for all the help.

---

