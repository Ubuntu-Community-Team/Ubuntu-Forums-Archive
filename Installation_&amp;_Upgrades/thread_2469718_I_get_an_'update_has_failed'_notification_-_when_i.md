---
title: "I get an 'update has failed' notification - when it has actually worked"
date: 2021-12-07
forum: Installation &amp; Upgrades
---

### Post by chrisnd2 on 2021-12-07
I have previously asked this on askubuntu without a solution:
This started with Ubuntu 21.04. I expected it to be sorted out with 21.10 - but the error persists. The scenario is that I get daily notifications of various updates to ubuntu itself or the apps. I click install and the updates are installed but then I get a message to say the updates have failed when in actual fact they have succeeded! I've got used to this, and it doesn't really bother me, but it would be nice to have the correct message appearing. In short, how do I get a 'Success!' message rather than the current 'failure' one? TIA Chris D

---

### Post by rsteinmetz70112 on 2021-12-09
When you do the updates does it show problems with any packages?

I suggest you open a terminal and run the following commands, if you haven't already:

```
sudo apt update
sudo apt full upgrade
sudo apt install -f
sudo dpkg --configure -a
```

Post the output from these commands.

---

### Post by T6&amp;sfpER35% on 2021-12-09
> when in actual fact they have succeeded
how sure are you of this ?

---

### Post by chrisnd2 on 2021-12-10
Firstly, I am not notified of the same updates again and secondly, version/build numbers etc change as anticipated.

---

### Post by chrisnd2 on 2021-12-10
I seem to invariably get an error with 'postfix'...
```
sudo apt update gives:
Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) impish InRelease                     
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) impish-updates InRelease [110 kB]    
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) impish InRelease                     
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security InRelease [110 kB]     
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [114 kB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security/main amd64 DEP-11 Metadata [6,424 B]
Hit:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal InRelease                    
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) impish-backports InRelease [101 kB]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security/universe amd64 DEP-11 Metadata [2,308 B]
Get:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-backports InRelease [108 kB]
Get:12 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) impish-updates/main i386 Packages [88.1 kB]
Get:13 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) impish-updates/main amd64 Packages [180 kB]
Get:14 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) impish-updates/main amd64 DEP-11 Metadata [18.9 kB]
Get:15 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) impish-updates/universe amd64 Packages [64.0 kB]
Get:16 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) impish-updates/universe i386 Packages [34.9 kB]
Get:17 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) impish-updates/universe amd64 DEP-11 Metadata [4,484 B]
Get:18 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) impish-backports/universe amd64 DEP-11 Metadata [9,284 B]
Fetched 1,066 kB in 3s (383 kB/s)            
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
6 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Skipping acquisition of configured file 'multiverse/source/Sources', as repository 'http://archive.canonical.com/ubuntu impish InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquisition of configured file 'multiverse/binary-amd64/Packages', as repository 'http://archive.canonical.com/ubuntu impish InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquisition of configured file 'multiverse/binary-i386/Packages', as repository 'http://archive.canonical.com/ubuntu impish InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquisition of configured file 'multiverse/i18n/Translation-en', as repository 'http://archive.canonical.com/ubuntu impish InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquisition of configured file 'multiverse/i18n/Translation-en_GB', as repository 'http://archive.canonical.com/ubuntu impish InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquisition of configured file 'multiverse/dep11/Components-amd64.yml', as repository 'http://archive.canonical.com/ubuntu impish InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquisition of configured file 'multiverse/dep11/icons-48x48.tar', as repository 'http://archive.canonical.com/ubuntu impish InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquisition of configured file 'multiverse/dep11/icons-64x64.tar', as repository 'http://archive.canonical.com/ubuntu impish InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquisition of configured file 'multiverse/dep11/icons-64x64@2.tar', as repository 'http://archive.canonical.com/ubuntu impish InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquisition of configured file 'multiverse/cnf/Commands-amd64', as repository 'http://archive.canonical.com/ubuntu impish InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
```

---

### Post by ActionParsnip on 2021-12-10
What is the output of:
```

cat -n /etc/apt/sources.list

```
Thanks

---

### Post by chrisnd2 on 2021-12-10
sudo apt full upgrade gives:
E: Invalid operation full

```
sudo apt install -f gives:
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dvd+rw-tools g++-10 gcc-10-base:i386 gir1.2-clutter-1.0
  gir1.2-clutter-gst-3.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gir1.2-gtkclutter-1.0 libarmadillo9 libasn1-8-heimdal
  libboost-date-time1.71.0 libboost-filesystem1.71.0 libboost-iostreams1.71.0
  libboost-locale1.71.0 libboost-regex1.71.0 libboost-thread1.71.0
  libbrlapi0.7 libdap25 libedataserver-1.2-25 libedataserverui-1.2-2
  libfilezilla0 libgdal27 libgeos-3.8.1 libgps26 libgssapi3-heimdal
  libhandy-0.0-0 libhcrypto4-heimdal libheimbase1-heimdal libheimntlm0-heimdal
  libhx509-5-heimdal libisl22 libjs-sizzle libjuh-java libjurt-java
  libkrb5-26-heimdal libldap-2.4-2 liblibreoffice-java libllvm11 libmapnik3.0
  liborcus-0.15-0 liborcus-parser-0.15-0 libpdf-api2-perl libpdf-api2-xs-perl
  libpgm-5.2-0 libphonenumber7 libpoppler102 libpoppler107 libpython2-stdlib
  libpython2.7-minimal libpython2.7-stdlib libpython3.8 libpython3.8-minimal
  libpython3.8-stdlib libqt5concurrent5 libraw19 libridl-java
  libroken18-heimdal libsdl-ttf2.0-0 libstdc++-10-dev libtepl-5-0
  libtracker-control-2.0-0 libtracker-miner-2.0-0 libtracker-sparql-2.0-0
  libunoloader-java libwind0-heimdal libzip5 lz4 node-jquery python-is-python2
  python2 python2-minimal python2.7 python2.7-minimal
  python3-requests-unixsocket python3.8 python3.8-minimal ure-java vino
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 6 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up postfix (3.5.6-1ubuntu2) ...


Postfix (main.cf) configuration was not changed.  If you need to make changes, 
edit /etc/postfix/main.cf (and others) as needed.  To view Postfix 
configuration values, see postconf(1).


After modifying main.cf, be sure to run 'systemctl reload postfix'.


Running newaliases
newaliases: warning: valid_hostname: misplaced delimiter: chrisnd-Latitude-E6520
..
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad paramete
r value: chrisnd-Latitude-E6520..
dpkg: error processing package postfix (--configure):
 installed postfix package post-installation script subprocess returned error ex
it status 75
Processing triggers for libc-bin (2.34-0ubuntu3) ...
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)



sudo dpkg --configure -a  gives:
Setting up postfix (3.5.6-1ubuntu2) ...


Postfix (main.cf) configuration was not changed.  If you need to make changes, 
edit /etc/postfix/main.cf (and others) as needed.  To view Postfix 
configuration values, see postconf(1).


After modifying main.cf, be sure to run 'systemctl reload postfix'.


Running newaliases
newaliases: warning: valid_hostname: misplaced delimiter: chrisnd-Latitude-E6520..
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: chrisnd-Latitude-E6520..
dpkg: error processing package postfix (--configure):
 installed postfix package post-installation script subprocess returned error exit status 75
Processing triggers for libc-bin (2.34-0ubuntu3) ...
Errors were encountered while processing:
 postfix
```

---

### Post by chrisnd2 on 2021-12-10
> **ActionParsnip said:**
> What is the output of:
```

cat -n /etc/apt/sources.list

```
Thanks

This gives:
```
cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731)]/ focal main restricted
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) impish main restricted
     6    # deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) focal main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) impish-updates main restricted
    11    deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) focal-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) impish universe
    17    deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) focal universe multiverse
    18    deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) impish-updates universe
    19    deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) focal-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) impish multiverse
    27    # deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) focal multiverse
    28    deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) impish-updates multiverse
    29    deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) focal-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) impish-backports main restricted universe multiverse
    37    deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse
    38    
    39    ## Uncomment the following two lines to add software from Canonical's
    40    ## 'partner' repository.
    41    ## This software is not part of Ubuntu, but is offered by Canonical and the
    42    ## respective vendors as a service to Ubuntu users.
    43    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) impish partner multiverse
    44    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) impish partner multiverse
    45    
    46    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security main restricted
    47    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
    48    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security universe
    49    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
    50    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security multiverse
    51    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse
    52    
    53    # This system was installed using small removable media
    54    # (e.g. netinst, live or single CD). The matching "deb cdrom"
    55    # entries were disabled at the end of the installation process.
    56    # For information about how to configure apt package sources,
    57    # see the sources.list(5) manual.
    58    # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal main universe restricted multiverse
```

---

### Post by deadflowr on 2021-12-10
You need to remove the multiverse entry from lines 43 and 44.
These two:```
43   deb http://archive.canonical.com/ubuntu impish partner multiverse
44   deb-src http://archive.canonical.com/ubuntu impish partner multiverse
```
the archive.canonical repositories only hold the partner component.

(You can edit the sources.list file with the command
```
sudo apt edit-sources
```

As far as postfix, see if this helps: [https://askubuntu.com/questions/1333199/apt-update-encounters-an-error-configuring-postfix-after-upgrade-to-21-04]("https://askubuntu.com/questions/1333199/apt-update-encounters-an-error-configuring-postfix-after-upgrade-to-21-04")

---

### Post by Impavidus on 2021-12-11
There are several not-so-clean lines in your sources.list:
Line 6: focal should be impish, but as this line is commented out, that doesn't really matter.
Line 11: focal-updates should be impish-updates. If you don't really use the source repositories, you can comment the whole line out.
Line 17: focal should be impish. multiverse is listed again on line 27, so delete it here. If you need the multiverse source repo, uncomment line 27.
Line 19: focal-updates should be impish-updates. If you don't really use the source repositories, you can comment the whole line out.
Line 27: focal should be impish, but as this line is commented out, that doesn't really matter.
Line 29: focal-updates should be impish-updates. If you don't really use the source repositories, you can comment the whole line out.
Line 37: focal-backports should be impish-backports. If you don't really use the source repositories, you can comment the whole line out.
Line 43: remove multiverse from this line.
Line 44: remove multiverse from this line.  If you don't really use the source repositories, you can comment the whole line out.
Line 47: focal-security should be impish-security.  If you don't really use the source repositories, you can comment the whole line out.
Line 49: focal-security should be impish-security.  If you don't really use the source repositories, you can comment the whole line out.
Line 51: focal-security should be impish-security.  If you don't really use the source repositories, you can comment the whole line out.

Lines 43 and 44 are the ones triggering the warnings in from apt update, the other fixes are just nice cleanup, although required if you decide you want to use the source repos.

---

### Post by chrisnd2 on 2021-12-13
> **deadflowr said:**
> You need to remove the multiverse entry from lines 43 and 44.
These two:```
43   deb http://archive.canonical.com/ubuntu impish partner multiverse
44   deb-src http://archive.canonical.com/ubuntu impish partner multiverse
```
the archive.canonical repositories only hold the partner component.

(You can edit the sources.list file with the command
```
sudo apt edit-sources
```

As far as postfix, see if this helps: [https://askubuntu.com/questions/1333199/apt-update-encounters-an-error-configuring-postfix-after-upgrade-to-21-04](https://askubuntu.com/questions/1333199/apt-update-encounters-an-error-configuring-postfix-after-upgrade-to-21-04)

Thanks for this (and to Impavidus) which seem to have (mostly) sorted things out.
Ie, I seem to be getting the correct message now

I haven't looked at the postfix issue yet but will get back to that at a later date when time is in greater availability :-)

Cheers, Chris

---

