---
title: "upgrade error"
date: 2015-10-30
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2015-10-30
I just upgraded to 15.10 on a Dell Precision M50 (32b). I was using gnome-flashback because the poor old machine couldn't handle the unity front end. During the upgrade the system stopped because of an error at the package setting process, so I entered ```
 sudo dpkg -- configure -a
``` and after setting the packages it still gives me an error that is:
```
[sudo] password for daniel: dpkg: dependency problems prevent configuration of kde-telepathy:
 kde-telepathy depends on kde-telepathy-minimal (= 15.04.20ubuntu1); however:
  Version of kde-telepathy-minimal on system is 0.9.0ubuntu1.
 kde-telepathy depends on kde-telepathy-send-file (>= 15.04.0); however:
  Version of kde-telepathy-send-file on system is 0.9.0-0ubuntu1.


dpkg: error processing package kde-telepathy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-telepathy-text-ui:
 kde-telepathy-text-ui depends on libktpotr9 (>= 15.03.80); however:
  Package libktpotr9 is not installed.


dpkg: error processing package kde-telepathy-text-ui (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kde-telepathy
 kde-telepathy-text-ui

```
I'll appreciate any help.

Daniel

I just tried ```

sudo apt-get update && sudo apt-get dist-upgrade -f
```
and got:
```
Do you want to continue? [Y/n] yExtracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 470327 files and directories currently installed.)
Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_i386.deb ...
Unpacking kde-config-telepathy-accounts (4:15.08.2-0ubuntu1) over (0.9.0-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+15.04.20150415.1-0ubuntu2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by danielsender on 2015-10-31
> **danielsender said:**
> I just upgraded to 15.10 on a Dell Precision M50 (32b). I was using gnome-flashback because the poor old machine couldn't handle the unity front end. During the upgrade the system stopped because of an error at the package setting process, so I entered ```
 sudo dpkg -- configure -a
``` and after setting the packages it still gives me an error that is:
```
[sudo] password for daniel: dpkg: dependency problems prevent configuration of kde-telepathy:
 kde-telepathy depends on kde-telepathy-minimal (= 15.04.20ubuntu1); however:
  Version of kde-telepathy-minimal on system is 0.9.0ubuntu1.
 kde-telepathy depends on kde-telepathy-send-file (>= 15.04.0); however:
  Version of kde-telepathy-send-file on system is 0.9.0-0ubuntu1.


dpkg: error processing package kde-telepathy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-telepathy-text-ui:
 kde-telepathy-text-ui depends on libktpotr9 (>= 15.03.80); however:
  Package libktpotr9 is not installed.


dpkg: error processing package kde-telepathy-text-ui (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kde-telepathy
 kde-telepathy-text-ui

```
I'll appreciate any help.

Daniel

I just tried ```

sudo apt-get update && sudo apt-get dist-upgrade -f
```
and got:
```
Do you want to continue? [Y/n] yExtracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 470327 files and directories currently installed.)
Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_i386.deb ...
Unpacking kde-config-telepathy-accounts (4:15.08.2-0ubuntu1) over (0.9.0-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+15.04.20150415.1-0ubuntu2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Is any guru willing to help in finding a solution?

---

### Post by bapoumba on 2015-10-31
Not a guru here :)
```
kde-telepathy-minimal on system is 0.9.0ubuntu1.
```
This is the Vivid package : [http://packages.ubuntu.com/search?suite=vivid&searchon=names&keywords=kde-telepathy-minimal](http://packages.ubuntu.com/search?suite=vivid&searchon=names&keywords=kde-telepathy-minimal)
Wily is 15.04.20ubuntu1

So you probably have a problem with your repos if you cannot install the right package. Please post the outputs to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by danielsender on 2015-10-31
> **bapoumba said:**
> Not a guru here :)
```
kde-telepathy-minimal on system is 0.9.0ubuntu1.
```
This is the Vivid package : [http://packages.ubuntu.com/search?suite=vivid&searchon=names&keywords=kde-telepathy-minimal](http://packages.ubuntu.com/search?suite=vivid&searchon=names&keywords=kde-telepathy-minimal)
Wily is 15.04.20ubuntu1

So you probably have a problem with your repos if you cannot install the right package. Please post the outputs to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

cat -n /etc/apt/sources.list
```

     1    # deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ wily main restricted
     6    deb-src http://us.archive.ubuntu.com/ubuntu/ wily main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://us.archive.ubuntu.com/ubuntu/ wily-updates main restricted
    11    deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://us.archive.ubuntu.com/ubuntu/ wily universe
    17    deb-src http://us.archive.ubuntu.com/ubuntu/ wily universe
    18    deb http://us.archive.ubuntu.com/ubuntu/ wily-updates universe
    19    deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://us.archive.ubuntu.com/ubuntu/ wily multiverse
    27    deb-src http://us.archive.ubuntu.com/ubuntu/ wily multiverse
    28    deb http://us.archive.ubuntu.com/ubuntu/ wily-updates multiverse
    29    deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    
    37    deb http://security.ubuntu.com/ubuntu wily-security main restricted
    38    deb-src http://security.ubuntu.com/ubuntu wily-security main restricted
    39    deb http://security.ubuntu.com/ubuntu wily-security universe
    40    deb-src http://security.ubuntu.com/ubuntu wily-security universe
    41    deb http://security.ubuntu.com/ubuntu wily-security multiverse
    42    deb-src http://security.ubuntu.com/ubuntu wily-security multiverse
    43    
    44    ## Uncomment the following two lines to add software from Canonical's
    45    ## 'partner' repository.
    46    ## This software is not part of Ubuntu, but is offered by Canonical and the
    47    ## respective vendors as a service to Ubuntu users.
    48    deb http://archive.canonical.com/ubuntu wily partner
    49    deb-src http://archive.canonical.com/ubuntu wily partner
    50    
    51    # deb http://packages.mate-desktop.org/repo/ubuntu raring main # disabled on upgrade to raring
    52    # deb-src http://packages.mate-desktop.org/repo/ubuntu raring main # disabled on upgrade to raring
    53    deb http://archive.canonical.com/ wily partner
    54    deb-src http://archive.canonical.com/ wily partner
    55    # deb http://repo.mate-desktop.org/ubuntu saucy main # disabled on upgrade to raring disabled on upgrade to saucy
    56    # deb-src http://repo.mate-desktop.org/ubuntu saucy main # disabled on upgrade to raring disabled on upgrade to saucy
    57    # deb http://mirror1.mate-desktop.org/ubuntu saucy main # disabled on upgrade to raring disabled on upgrade to saucy
    58    # deb-src http://mirror1.mate-desktop.org/ubuntu saucy main # disabled on upgrade to raring disabled on upgrade to saucy

```
ls -la /etc/apt/sources.list.d
```

total 480
drwxr-xr-x 2 root root 12288 Jul  8 01:52 .
drwxr-xr-x 6 root root  4096 Jul  5 23:55 ..
-rw-r--r-- 1 root root   140 Jul  6 23:12 amith-ubuntutools-raring.list
-rw-r--r-- 1 root root   140 Jul  6 23:12 amith-ubuntutools-raring.list.distUpgrade
-rw-r--r-- 1 root root   140 Jul  6 14:24 amith-ubuntutools-raring.list.save
-rw-r--r-- 1 root root   166 Jul  6 23:12 atareao-atareao-raring.list
-rw-r--r-- 1 root root   166 Jul  6 23:12 atareao-atareao-raring.list.distUpgrade
-rw-r--r-- 1 root root   166 Jul  6 14:24 atareao-atareao-raring.list.save
-rw-r--r-- 1 root root   156 Jul  6 23:12 canonical-kernel-team-ppa-trusty.list
-rw-r--r-- 1 root root   156 Jul  6 23:12 canonical-kernel-team-ppa-trusty.list.distUpgrade
-rw-r--r-- 1 root root   156 Jul  6 14:24 canonical-kernel-team-ppa-trusty.list.save
-rw-r--r-- 1 root root   140 Jul  6 23:12 chris-lea-node_js-trusty.list
-rw-r--r-- 1 root root   140 Jul  6 23:12 chris-lea-node_js-trusty.list.distUpgrade
-rw-r--r-- 1 root root   140 Jul  6 14:24 chris-lea-node_js-trusty.list.save
-rw-r--r-- 1 root root   138 Jul  6 23:12 deluge-team-ppa-oneiric.list
-rw-r--r-- 1 root root   138 Jul  6 23:12 deluge-team-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root   138 Jul  6 14:24 deluge-team-ppa-oneiric.list.save
-rw-r--r-- 1 root root   138 Jul  6 23:12 deluge-team-ppa-quantal.list
-rw-r--r-- 1 root root   138 Jul  6 23:12 deluge-team-ppa-quantal.list.distUpgrade
-rw-r--r-- 1 root root   138 Jul  6 14:24 deluge-team-ppa-quantal.list.save
-rw-r--r-- 1 root root   201 Jul  6 23:12 ehoover-compholio-raring.list
-rw-r--r-- 1 root root   201 Jul  6 23:12 ehoover-compholio-raring.list.distUpgrade
-rw-r--r-- 1 root root   201 Jul  6 14:24 ehoover-compholio-raring.list.save
-rw-r--r-- 1 root root   142 Jul  6 23:12 ehoover-compholio-saucy.list
-rw-r--r-- 1 root root   142 Jul  6 23:12 ehoover-compholio-saucy.list.distUpgrade
-rw-r--r-- 1 root root   142 Jul  6 14:24 ehoover-compholio-saucy.list.save
-rw-r--r-- 1 root root   210 Jul  6 23:12 ferramroberto-java-oneiric.list
-rw-r--r-- 1 root root   210 Jul  6 23:12 ferramroberto-java-oneiric.list.distUpgrade
-rw-r--r-- 1 root root   210 Jul  6 14:24 ferramroberto-java-oneiric.list.save
-rw-r--r-- 1 root root   150 Jul  6 23:12 ferramroberto-sopcast-oneiric.list
-rw-r--r-- 1 root root   150 Jul  6 23:12 ferramroberto-sopcast-oneiric.list.distUpgrade
-rw-r--r-- 1 root root   150 Jul  6 14:24 ferramroberto-sopcast-oneiric.list.save
-rw-r--r-- 1 root root   243 Jul  6 23:12 ferramroberto-sopcast-precise.list
-rw-r--r-- 1 root root   243 Jul  6 23:12 ferramroberto-sopcast-precise.list.distUpgrade
-rw-r--r-- 1 root root   243 Jul  6 14:24 ferramroberto-sopcast-precise.list.save
-rw-r--r-- 1 root root   176 Jul  8 01:52 google-chrome.list
-rw-r--r-- 1 root root   176 Jul  6 23:12 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root   176 Jul  6 14:24 google-chrome.list.save
-rw-r--r-- 1 root root   180 Jul  8 01:52 google-talkplugin.list
-rw-r--r-- 1 root root   180 Jul  6 23:12 google-talkplugin.list.distUpgrade
-rw-r--r-- 1 root root   180 Jul  6 14:24 google-talkplugin.list.save
-rw-r--r-- 1 root root   159 Jul  6 23:12 jacob-media-saucy.list
-rw-r--r-- 1 root root   159 Jul  6 23:12 jacob-media-saucy.list.distUpgrade
-rw-r--r-- 1 root root   159 Jul  6 14:24 jacob-media-saucy.list.save
-rw-r--r-- 1 root root   152 Jul  6 23:12 kernel-ppa-pre-proposed-trusty.list
-rw-r--r-- 1 root root   152 Jul  6 23:12 kernel-ppa-pre-proposed-trusty.list.distUpgrade
-rw-r--r-- 1 root root   152 Jul  6 14:24 kernel-ppa-pre-proposed-trusty.list.save
-rw-r--r-- 1 root root   142 Jul  6 23:12 krytarik-tuxgarage-trusty.list
-rw-r--r-- 1 root root   142 Jul  6 23:12 krytarik-tuxgarage-trusty.list.distUpgrade
-rw-r--r-- 1 root root   142 Jul  6 14:24 krytarik-tuxgarage-trusty.list.save
-rw-r--r-- 1 root root   163 Jul  6 23:12 linrunner-tlp-saucy.list
-rw-r--r-- 1 root root   163 Jul  6 23:12 linrunner-tlp-saucy.list.distUpgrade
-rw-r--r-- 1 root root   163 Jul  6 14:24 linrunner-tlp-saucy.list.save
-rw-r--r-- 1 root root   314 Jul  6 23:12 medibuntu.list
-rw-r--r-- 1 root root   314 Jul  6 23:12 medibuntu.list.distUpgrade
-rw-r--r-- 1 root root   314 Jul  6 14:24 medibuntu.list.save
-rw-r--r-- 1 root root   201 Jul  6 23:12 mqchael-pipelight-raring.list
-rw-r--r-- 1 root root   201 Jul  6 23:12 mqchael-pipelight-raring.list.distUpgrade
-rw-r--r-- 1 root root   201 Jul  6 14:24 mqchael-pipelight-raring.list.save
-rw-r--r-- 1 root root   142 Jul  6 23:12 mqchael-pipelight-saucy.list
-rw-r--r-- 1 root root   142 Jul  6 23:12 mqchael-pipelight-saucy.list.distUpgrade
-rw-r--r-- 1 root root   142 Jul  6 14:24 mqchael-pipelight-saucy.list.save
-rw-r--r-- 1 root root   214 Jul  6 23:12 nilarimogard-webupd8-oneiric.list
-rw-r--r-- 1 root root   214 Jul  6 23:12 nilarimogard-webupd8-oneiric.list.distUpgrade
-rw-r--r-- 1 root root   214 Jul  6 14:24 nilarimogard-webupd8-oneiric.list.save
-rw-r--r-- 1 root root   182 Jul  6 23:12 oibaf-graphics-drivers-trusty.list
-rw-r--r-- 1 root root   182 Jul  6 23:12 oibaf-graphics-drivers-trusty.list.distUpgrade
-rw-r--r-- 1 root root   182 Jul  6 14:24 oibaf-graphics-drivers-trusty.list.save
-rw-r--r-- 1 root root   177 Jul  6 23:12 oibaf-ubuntu-graphics-drivers-vivid.list
-rw-r--r-- 1 root root   146 Jul  6 23:12 oibaf-ubuntu-graphics-drivers-vivid.list.distUpgrade
-rw-r--r-- 1 root root   170 Jul  6 23:12 pipelight-stable-trusty.list
-rw-r--r-- 1 root root   170 Jul  6 23:12 pipelight-stable-trusty.list.distUpgrade
-rw-r--r-- 1 root root   170 Jul  6 14:24 pipelight-stable-trusty.list.save
-rw-r--r-- 1 root root   200 Jul  6 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list
-rw-r--r-- 1 root root   200 Jul  6 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list.distUpgrade
-rw-r--r-- 1 root root   200 Jul  6 14:24 private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list.save
-rw-r--r-- 1 root root   164 Jul  6 23:12 team-xbmc-ppa-trusty.list
-rw-r--r-- 1 root root   164 Jul  6 23:12 team-xbmc-ppa-trusty.list.distUpgrade
-rw-r--r-- 1 root root   164 Jul  6 14:24 team-xbmc-ppa-trusty.list.save
-rw-r--r-- 1 root root   134 Jul  6 23:12 tualatrix-ppa-oneiric.list
-rw-r--r-- 1 root root   134 Jul  6 23:12 tualatrix-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root   134 Jul  6 14:24 tualatrix-ppa-oneiric.list.save
-rw-r--r-- 1 root root   156 Jul  6 23:12 ubuntu-tweak-testing-ppa-oneiric.list
-rw-r--r-- 1 root root   156 Jul  6 23:12 ubuntu-tweak-testing-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root   156 Jul  6 14:24 ubuntu-tweak-testing-ppa-oneiric.list.save
-rw-r--r-- 1 root root   204 Jul  6 23:12 ubuntu-wine-ppa-oneiric.list
-rw-r--r-- 1 root root   204 Jul  6 23:12 ubuntu-wine-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root   204 Jul  6 14:24 ubuntu-wine-ppa-oneiric.list.save
-rw-r--r-- 1 root root   200 Jul  6 23:12 ubuntu-wine-ppa-quantal.list
-rw-r--r-- 1 root root   200 Jul  6 23:12 ubuntu-wine-ppa-quantal.list.distUpgrade
-rw-r--r-- 1 root root   200 Jul  6 14:24 ubuntu-wine-ppa-quantal.list.save
-rw-r--r-- 1 root root   216 Jul  6 23:12 ubuntu-x-swat-x-updates-quantal.list
-rw-r--r-- 1 root root   216 Jul  6 23:12 ubuntu-x-swat-x-updates-quantal.list.distUpgrade
-rw-r--r-- 1 root root   216 Jul  6 14:24 ubuntu-x-swat-x-updates-quantal.list.save
-rw-r--r-- 1 root root   198 Jul  6 23:12 venerix-blug-precise.list
-rw-r--r-- 1 root root   198 Jul  6 23:12 venerix-blug-precise.list.distUpgrade
-rw-r--r-- 1 root root   198 Jul  6 14:24 venerix-blug-precise.list.save
-rw-r--r-- 1 root root   179 Jul  6 23:12 videolan-stable-daily-saucy.list
-rw-r--r-- 1 root root   179 Jul  6 23:12 videolan-stable-daily-saucy.list.distUpgrade
-rw-r--r-- 1 root root   179 Jul  6 14:24 videolan-stable-daily-saucy.list.save
-rw-r--r-- 1 root root   168 Jul  6 23:12 webupd8team-java-raring.list
-rw-r--r-- 1 root root   168 Jul  6 23:12 webupd8team-java-raring.list.distUpgrade
-rw-r--r-- 1 root root   168 Jul  6 14:24 webupd8team-java-raring.list.save
-rw-r--r-- 1 root root   241 Jul  6 23:12 webupd8team-java-trusty.list
-rw-r--r-- 1 root root   241 Jul  6 23:12 webupd8team-java-trusty.list.distUpgrade
-rw-r--r-- 1 root root   241 Jul  6 14:24 webupd8team-java-trusty.list.save
-rw-r--r-- 1 root root   184 Jul  6 23:12 webupd8team-popcorntime-trusty.list
-rw-r--r-- 1 root root   184 Jul  6 23:12 webupd8team-popcorntime-trusty.list.distUpgrade
-rw-r--r-- 1 root root   184 Jul  6 14:24 webupd8team-popcorntime-trusty.list.save
-rw-r--r-- 1 root root   186 Jul  6 23:12 webupd8team-y-ppa-manager-raring.list
-rw-r--r-- 1 root root   186 Jul  6 23:12 webupd8team-y-ppa-manager-raring.list.distUpgrade
-rw-r--r-- 1 root root   186 Jul  6 14:24 webupd8team-y-ppa-manager-raring.list.save
-rw-r--r-- 1 root root   168 Jul  6 23:12 xorg-edgers-ppa-trusty.list
-rw-r--r-- 1 root root   168 Jul  6 23:12 xorg-edgers-ppa-trusty.list.distUpgrade
-rw-r--r-- 1 root root   168 Jul  6 14:24 xorg-edgers-ppa-trusty.list.save
-rw-r--r-- 1 root root   184 Jul  6 23:12 zedtux-naturalscrolling-trusty.list
-rw-r--r-- 1 root root   184 Jul  6 23:12 zedtux-naturalscrolling-trusty.list.distUpgrade
-rw-r--r-- 1 root root   184 Jul  6 14:24 zedtux-naturalscrolling-trusty.list.save
```
tail -v -n +1 /etc/apt/sources.list.d/*```

==> /etc/apt/sources.list.d/amith-ubuntutools-raring.list <==
# deb http://ppa.launchpad.net/amith/ubuntutools/ubuntu raring main
# deb-src http://ppa.launchpad.net/amith/ubuntutools/ubuntu raring main


==> /etc/apt/sources.list.d/amith-ubuntutools-raring.list.distUpgrade <==
# deb http://ppa.launchpad.net/amith/ubuntutools/ubuntu raring main
# deb-src http://ppa.launchpad.net/amith/ubuntutools/ubuntu raring main


==> /etc/apt/sources.list.d/amith-ubuntutools-raring.list.save <==
# deb http://ppa.launchpad.net/amith/ubuntutools/ubuntu raring main
# deb-src http://ppa.launchpad.net/amith/ubuntutools/ubuntu raring main


==> /etc/apt/sources.list.d/atareao-atareao-raring.list <==
# deb http://ppa.launchpad.net/atareao/atareao/ubuntu saucy main # disabled on upgrade to saucy
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu raring main


==> /etc/apt/sources.list.d/atareao-atareao-raring.list.distUpgrade <==
# deb http://ppa.launchpad.net/atareao/atareao/ubuntu saucy main # disabled on upgrade to saucy
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu raring main


==> /etc/apt/sources.list.d/atareao-atareao-raring.list.save <==
# deb http://ppa.launchpad.net/atareao/atareao/ubuntu saucy main # disabled on upgrade to saucy
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu raring main


==> /etc/apt/sources.list.d/canonical-kernel-team-ppa-trusty.list <==
# deb http://ppa.launchpad.net/canonical-kernel-team/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/canonical-kernel-team/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/canonical-kernel-team-ppa-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/canonical-kernel-team/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/canonical-kernel-team/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/canonical-kernel-team-ppa-trusty.list.save <==
# deb http://ppa.launchpad.net/canonical-kernel-team/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/canonical-kernel-team/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/chris-lea-node_js-trusty.list <==
# deb http://ppa.launchpad.net/chris-lea/node.js/ubuntu trusty main
# deb-src http://ppa.launchpad.net/chris-lea/node.js/ubuntu trusty main


==> /etc/apt/sources.list.d/chris-lea-node_js-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/chris-lea/node.js/ubuntu trusty main
# deb-src http://ppa.launchpad.net/chris-lea/node.js/ubuntu trusty main


==> /etc/apt/sources.list.d/chris-lea-node_js-trusty.list.save <==
# deb http://ppa.launchpad.net/chris-lea/node.js/ubuntu trusty main
# deb-src http://ppa.launchpad.net/chris-lea/node.js/ubuntu trusty main


==> /etc/apt/sources.list.d/deluge-team-ppa-oneiric.list <==
# deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu oneiric main


==> /etc/apt/sources.list.d/deluge-team-ppa-oneiric.list.distUpgrade <==
# deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu oneiric main


==> /etc/apt/sources.list.d/deluge-team-ppa-oneiric.list.save <==
# deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu oneiric main


==> /etc/apt/sources.list.d/deluge-team-ppa-quantal.list <==
# deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu quantal main
# deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu quantal main


==> /etc/apt/sources.list.d/deluge-team-ppa-quantal.list.distUpgrade <==
# deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu quantal main
# deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu quantal main


==> /etc/apt/sources.list.d/deluge-team-ppa-quantal.list.save <==
# deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu quantal main
# deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu quantal main


==> /etc/apt/sources.list.d/ehoover-compholio-raring.list <==
# deb http://ppa.launchpad.net/ehoover/compholio/ubuntu trusty main # disabled on upgrade to saucy disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu raring main


==> /etc/apt/sources.list.d/ehoover-compholio-raring.list.distUpgrade <==
# deb http://ppa.launchpad.net/ehoover/compholio/ubuntu trusty main # disabled on upgrade to saucy disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu raring main


==> /etc/apt/sources.list.d/ehoover-compholio-raring.list.save <==
# deb http://ppa.launchpad.net/ehoover/compholio/ubuntu trusty main # disabled on upgrade to saucy disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu raring main


==> /etc/apt/sources.list.d/ehoover-compholio-saucy.list <==
# deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu saucy main
# deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu saucy main


==> /etc/apt/sources.list.d/ehoover-compholio-saucy.list.distUpgrade <==
# deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu saucy main
# deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu saucy main


==> /etc/apt/sources.list.d/ehoover-compholio-saucy.list.save <==
# deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu saucy main
# deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu saucy main


==> /etc/apt/sources.list.d/ferramroberto-java-oneiric.list <==
# deb http://ppa.launchpad.net/ferramroberto/java/ubuntu precise main # disabled on upgrade to precise
# deb-src http://ppa.launchpad.net/ferramroberto/java/ubuntu precise main # disabled on upgrade to precise


==> /etc/apt/sources.list.d/ferramroberto-java-oneiric.list.distUpgrade <==
# deb http://ppa.launchpad.net/ferramroberto/java/ubuntu precise main # disabled on upgrade to precise
# deb-src http://ppa.launchpad.net/ferramroberto/java/ubuntu precise main # disabled on upgrade to precise


==> /etc/apt/sources.list.d/ferramroberto-java-oneiric.list.save <==
# deb http://ppa.launchpad.net/ferramroberto/java/ubuntu precise main # disabled on upgrade to precise
# deb-src http://ppa.launchpad.net/ferramroberto/java/ubuntu precise main # disabled on upgrade to precise


==> /etc/apt/sources.list.d/ferramroberto-sopcast-oneiric.list <==
# deb http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu oneiric main


==> /etc/apt/sources.list.d/ferramroberto-sopcast-oneiric.list.distUpgrade <==
# deb http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu oneiric main


==> /etc/apt/sources.list.d/ferramroberto-sopcast-oneiric.list.save <==
# deb http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu oneiric main


==> /etc/apt/sources.list.d/ferramroberto-sopcast-precise.list <==
# deb http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu raring main # disabled on upgrade to raring
# deb-src http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu raring main # disabled on upgrade to quantal disabled on upgrade to raring


==> /etc/apt/sources.list.d/ferramroberto-sopcast-precise.list.distUpgrade <==
# deb http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu raring main # disabled on upgrade to raring
# deb-src http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu raring main # disabled on upgrade to quantal disabled on upgrade to raring


==> /etc/apt/sources.list.d/ferramroberto-sopcast-precise.list.save <==
# deb http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu raring main # disabled on upgrade to raring
# deb-src http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu raring main # disabled on upgrade to quantal disabled on upgrade to raring


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google-talkplugin.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main


==> /etc/apt/sources.list.d/google-talkplugin.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main


==> /etc/apt/sources.list.d/google-talkplugin.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main


==> /etc/apt/sources.list.d/jacob-media-saucy.list <==
# deb http://ppa.launchpad.net/jacob/media/ubuntu trusty main # disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/jacob/media/ubuntu saucy main


==> /etc/apt/sources.list.d/jacob-media-saucy.list.distUpgrade <==
# deb http://ppa.launchpad.net/jacob/media/ubuntu trusty main # disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/jacob/media/ubuntu saucy main


==> /etc/apt/sources.list.d/jacob-media-saucy.list.save <==
# deb http://ppa.launchpad.net/jacob/media/ubuntu trusty main # disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/jacob/media/ubuntu saucy main


==> /etc/apt/sources.list.d/kernel-ppa-pre-proposed-trusty.list <==
# deb http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu trusty main


==> /etc/apt/sources.list.d/kernel-ppa-pre-proposed-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu trusty main


==> /etc/apt/sources.list.d/kernel-ppa-pre-proposed-trusty.list.save <==
# deb http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu trusty main


==> /etc/apt/sources.list.d/krytarik-tuxgarage-trusty.list <==
# deb http://ppa.launchpad.net/krytarik/tuxgarage/ubuntu trusty main
# deb-src http://ppa.launchpad.net/krytarik/tuxgarage/ubuntu trusty main


==> /etc/apt/sources.list.d/krytarik-tuxgarage-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/krytarik/tuxgarage/ubuntu trusty main
# deb-src http://ppa.launchpad.net/krytarik/tuxgarage/ubuntu trusty main


==> /etc/apt/sources.list.d/krytarik-tuxgarage-trusty.list.save <==
# deb http://ppa.launchpad.net/krytarik/tuxgarage/ubuntu trusty main
# deb-src http://ppa.launchpad.net/krytarik/tuxgarage/ubuntu trusty main


==> /etc/apt/sources.list.d/linrunner-tlp-saucy.list <==
# deb http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main # disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/linrunner/tlp/ubuntu saucy main


==> /etc/apt/sources.list.d/linrunner-tlp-saucy.list.distUpgrade <==
# deb http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main # disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/linrunner/tlp/ubuntu saucy main


==> /etc/apt/sources.list.d/linrunner-tlp-saucy.list.save <==
# deb http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main # disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/linrunner/tlp/ubuntu saucy main


==> /etc/apt/sources.list.d/medibuntu.list <==
## Please report any bug on https://bugs.launchpad.net/medibuntu/
# deb http://packages.medibuntu.org/ raring free non-free #Medibuntu - Ubuntu 12.10 "quantal quetzal" disabled on upgrade to raring
# deb-src http://packages.medibuntu.org/ quantal free non-free #Medibuntu (source) - Ubuntu 12.10 "quantal quetzal"


==> /etc/apt/sources.list.d/medibuntu.list.distUpgrade <==
## Please report any bug on https://bugs.launchpad.net/medibuntu/
# deb http://packages.medibuntu.org/ raring free non-free #Medibuntu - Ubuntu 12.10 "quantal quetzal" disabled on upgrade to raring
# deb-src http://packages.medibuntu.org/ quantal free non-free #Medibuntu (source) - Ubuntu 12.10 "quantal quetzal"


==> /etc/apt/sources.list.d/medibuntu.list.save <==
## Please report any bug on https://bugs.launchpad.net/medibuntu/
# deb http://packages.medibuntu.org/ raring free non-free #Medibuntu - Ubuntu 12.10 "quantal quetzal" disabled on upgrade to raring
# deb-src http://packages.medibuntu.org/ quantal free non-free #Medibuntu (source) - Ubuntu 12.10 "quantal quetzal"


==> /etc/apt/sources.list.d/mqchael-pipelight-raring.list <==
# deb http://ppa.launchpad.net/mqchael/pipelight/ubuntu trusty main # disabled on upgrade to saucy disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/mqchael/pipelight/ubuntu raring main


==> /etc/apt/sources.list.d/mqchael-pipelight-raring.list.distUpgrade <==
# deb http://ppa.launchpad.net/mqchael/pipelight/ubuntu trusty main # disabled on upgrade to saucy disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/mqchael/pipelight/ubuntu raring main


==> /etc/apt/sources.list.d/mqchael-pipelight-raring.list.save <==
# deb http://ppa.launchpad.net/mqchael/pipelight/ubuntu trusty main # disabled on upgrade to saucy disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/mqchael/pipelight/ubuntu raring main


==> /etc/apt/sources.list.d/mqchael-pipelight-saucy.list <==
# deb-src http://ppa.launchpad.net/mqchael/pipelight/ubuntu saucy main
# deb-src http://ppa.launchpad.net/mqchael/pipelight/ubuntu saucy main


==> /etc/apt/sources.list.d/mqchael-pipelight-saucy.list.distUpgrade <==
# deb-src http://ppa.launchpad.net/mqchael/pipelight/ubuntu saucy main
# deb-src http://ppa.launchpad.net/mqchael/pipelight/ubuntu saucy main


==> /etc/apt/sources.list.d/mqchael-pipelight-saucy.list.save <==
# deb-src http://ppa.launchpad.net/mqchael/pipelight/ubuntu saucy main
# deb-src http://ppa.launchpad.net/mqchael/pipelight/ubuntu saucy main


==> /etc/apt/sources.list.d/nilarimogard-webupd8-oneiric.list <==
# deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu precise main # disabled on upgrade to precise
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu precise main # disabled on upgrade to precise


==> /etc/apt/sources.list.d/nilarimogard-webupd8-oneiric.list.distUpgrade <==
# deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu precise main # disabled on upgrade to precise
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu precise main # disabled on upgrade to precise


==> /etc/apt/sources.list.d/nilarimogard-webupd8-oneiric.list.save <==
# deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu precise main # disabled on upgrade to precise
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu precise main # disabled on upgrade to precise


==> /etc/apt/sources.list.d/oibaf-graphics-drivers-trusty.list <==
# deb http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu trusty main


==> /etc/apt/sources.list.d/oibaf-graphics-drivers-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu trusty main


==> /etc/apt/sources.list.d/oibaf-graphics-drivers-trusty.list.save <==
# deb http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu trusty main


==> /etc/apt/sources.list.d/oibaf-ubuntu-graphics-drivers-vivid.list <==
# deb http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu vivid main


==> /etc/apt/sources.list.d/oibaf-ubuntu-graphics-drivers-vivid.list.distUpgrade <==
deb http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu vivid main
# deb-src http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu vivid main


==> /etc/apt/sources.list.d/pipelight-stable-trusty.list <==
# deb http://ppa.launchpad.net/pipelight/stable/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu trusty main


==> /etc/apt/sources.list.d/pipelight-stable-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/pipelight/stable/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu trusty main


==> /etc/apt/sources.list.d/pipelight-stable-trusty.list.save <==
# deb http://ppa.launchpad.net/pipelight/stable/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu trusty main


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list <==
# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/master-pdf-editor/ubuntu quantal main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to saucy


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list.distUpgrade <==
# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/master-pdf-editor/ubuntu quantal main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to saucy


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list.save <==
# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/master-pdf-editor/ubuntu quantal main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to saucy


==> /etc/apt/sources.list.d/team-xbmc-ppa-trusty.list <==
# deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/team-xbmc-ppa-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/team-xbmc-ppa-trusty.list.save <==
# deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/tualatrix-ppa-oneiric.list <==
# deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu oneiric main


==> /etc/apt/sources.list.d/tualatrix-ppa-oneiric.list.distUpgrade <==
# deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu oneiric main


==> /etc/apt/sources.list.d/tualatrix-ppa-oneiric.list.save <==
# deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu oneiric main


==> /etc/apt/sources.list.d/ubuntu-tweak-testing-ppa-oneiric.list <==
# deb http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu oneiric main


==> /etc/apt/sources.list.d/ubuntu-tweak-testing-ppa-oneiric.list.distUpgrade <==
# deb http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu oneiric main


==> /etc/apt/sources.list.d/ubuntu-tweak-testing-ppa-oneiric.list.save <==
# deb http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu oneiric main


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list <==
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main # disabled on upgrade to precise
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main # disabled on upgrade to precise


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list.distUpgrade <==
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main # disabled on upgrade to precise
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main # disabled on upgrade to precise


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list.save <==
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main # disabled on upgrade to precise
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main # disabled on upgrade to precise


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-quantal.list <==
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu raring main # disabled on upgrade to raring
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu raring main # disabled on upgrade to raring


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-quantal.list.distUpgrade <==
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu raring main # disabled on upgrade to raring
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu raring main # disabled on upgrade to raring


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-quantal.list.save <==
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu raring main # disabled on upgrade to raring
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu raring main # disabled on upgrade to raring


==> /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-quantal.list <==
# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu raring main # disabled on upgrade to raring
# deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu raring main # disabled on upgrade to raring


==> /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-quantal.list.distUpgrade <==
# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu raring main # disabled on upgrade to raring
# deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu raring main # disabled on upgrade to raring


==> /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-quantal.list.save <==
# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu raring main # disabled on upgrade to raring
# deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu raring main # disabled on upgrade to raring


==> /etc/apt/sources.list.d/venerix-blug-precise.list <==
# deb http://ppa.launchpad.net/venerix/blug/ubuntu quantal main # disabled on upgrade to quantal
# deb-src http://ppa.launchpad.net/venerix/blug/ubuntu quantal main # disabled on upgrade to quantal


==> /etc/apt/sources.list.d/venerix-blug-precise.list.distUpgrade <==
# deb http://ppa.launchpad.net/venerix/blug/ubuntu quantal main # disabled on upgrade to quantal
# deb-src http://ppa.launchpad.net/venerix/blug/ubuntu quantal main # disabled on upgrade to quantal


==> /etc/apt/sources.list.d/venerix-blug-precise.list.save <==
# deb http://ppa.launchpad.net/venerix/blug/ubuntu quantal main # disabled on upgrade to quantal
# deb-src http://ppa.launchpad.net/venerix/blug/ubuntu quantal main # disabled on upgrade to quantal


==> /etc/apt/sources.list.d/videolan-stable-daily-saucy.list <==
# deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu trusty main # disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/videolan/stable-daily/ubuntu saucy main


==> /etc/apt/sources.list.d/videolan-stable-daily-saucy.list.distUpgrade <==
# deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu trusty main # disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/videolan/stable-daily/ubuntu saucy main


==> /etc/apt/sources.list.d/videolan-stable-daily-saucy.list.save <==
# deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu trusty main # disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/videolan/stable-daily/ubuntu saucy main


==> /etc/apt/sources.list.d/webupd8team-java-raring.list <==
# deb http://ppa.launchpad.net/webupd8team/java/ubuntu saucy main # disabled on upgrade to saucy
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu raring main


==> /etc/apt/sources.list.d/webupd8team-java-raring.list.distUpgrade <==
# deb http://ppa.launchpad.net/webupd8team/java/ubuntu saucy main # disabled on upgrade to saucy
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu raring main


==> /etc/apt/sources.list.d/webupd8team-java-raring.list.save <==
# deb http://ppa.launchpad.net/webupd8team/java/ubuntu saucy main # disabled on upgrade to saucy
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu raring main


==> /etc/apt/sources.list.d/webupd8team-java-trusty.list <==
# deb http://ppa.launchpad.net/webupd8team/java/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-java-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/webupd8team/java/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-java-trusty.list.save <==
# deb http://ppa.launchpad.net/webupd8team/java/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-popcorntime-trusty.list <==
# deb http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-popcorntime-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-popcorntime-trusty.list.save <==
# deb http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-y-ppa-manager-raring.list <==
# deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu saucy main # disabled on upgrade to saucy
# deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu raring main


==> /etc/apt/sources.list.d/webupd8team-y-ppa-manager-raring.list.distUpgrade <==
# deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu saucy main # disabled on upgrade to saucy
# deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu raring main


==> /etc/apt/sources.list.d/webupd8team-y-ppa-manager-raring.list.save <==
# deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu saucy main # disabled on upgrade to saucy
# deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu raring main


==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list <==
# deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list.save <==
# deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/zedtux-naturalscrolling-trusty.list <==
# deb http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu trusty main


==> /etc/apt/sources.list.d/zedtux-naturalscrolling-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu trusty main


==> /etc/apt/sources.list.d/zedtux-naturalscrolling-trusty.list.save <==
# deb http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu trusty main
```

Thanks!

---

### Post by bapoumba on 2015-11-01
May be from this repo which is not disabled :
```
deb http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu vivid main
```
Please go to Software Sources and remove it.

You may want to do some cleaning around as most your ppas (but google's) were disabled on upgrade. You can remove everything except the google chrome and talkplugin ones.

If you are using some software from the other repos, you need to get the ones for wily.

---

### Post by danielsender on 2015-11-02
> **bapoumba said:**
> May be from this repo which is not disabled :
```
deb http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu vivid main
```
Please go to Software Sources and remove it.

You may want to do some cleaning around as most your ppas (but google's) were disabled on upgrade. You can remove everything except the google chrome and talkplugin ones.

If you are using some software from the other repos, you need to get the ones for wily.

I followed your directions but unfortunately I still see the same problem. I've tried with
```
sudo rm /var/lib/apt/lists/* -vf

```
but no avail. I also tried with synaptic to fix broken packages (20) and purge kde-telepathy and dependencies and I'm still stuck with the same messages. Any new ideas?

---

### Post by bapoumba on 2015-11-02
Did you reload your sources.list ?
```
sudo apt-get update
```

If you had, please post the output to :
```
apt-cache policy kde-telepathy-minimal
```
Not sure where this package is coming from.

---

### Post by danielsender on 2015-11-02
> **bapoumba said:**
> Did you reload your sources.list ?
```
sudo apt-get update
```

If you had, please post the output to :
```
apt-cache policy kde-telepathy-minimal
```
Not sure where this package is coming from.

Yes, I reloaded, and the output of "apt-cache policy kde-telepathy-minimal" is
```

kde-telepathy-minimal:  Installed: 0.9.0ubuntu1
  Candidate: 15.04.20ubuntu1
  Version table:
     15.04.20ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily/universe i386 Packages
 *** 0.9.0ubuntu1 0
        100 /var/lib/dpkg/status
```

---

### Post by bapoumba on 2015-11-04
OK. Sorry I overlooked one error :
```
trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+15.04.20150415.1-0ubuntu2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
```
Looking around, you can find these bugs :
[https://bugs.launchpad.net/kubuntu-ppa/+bug/1451728](https://bugs.launchpad.net/kubuntu-ppa/+bug/1451728)
[https://bugs.kde.org/show_bug.cgi?id=347219](https://bugs.kde.org/show_bug.cgi?id=347219)

Do you need kde-telepathy ?

---

### Post by danielsender on 2015-11-05
> **bapoumba said:**
> OK. Sorry I overlooked one error :
```
trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+15.04.20150415.1-0ubuntu2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
```
Looking around, you can find these bugs :
[https://bugs.launchpad.net/kubuntu-ppa/+bug/1451728](https://bugs.launchpad.net/kubuntu-ppa/+bug/1451728)
[https://bugs.kde.org/show_bug.cgi?id=347219](https://bugs.kde.org/show_bug.cgi?id=347219)

Do you need kde-telepathy ?

In fact I don't need the whole KDE environment - I installed it long time ago and I made very little use of it - as I remember only the disk burning app. I think I will do a fresh install from the live CD. In any case I appreciate the time you spent on this.

Best,

Daniel

---

