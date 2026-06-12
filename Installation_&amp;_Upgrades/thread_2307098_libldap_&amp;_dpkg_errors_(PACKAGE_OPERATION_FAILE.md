---
title: "libldap &amp; dpkg errors (PACKAGE OPERATION FAILED)"
date: 2015-12-21
forum: Installation &amp; Upgrades
---

### Post by steven-misshula on 2015-12-21
I removed Wine 1.8 and have crashed the install.

I've tried:

```
 sudo apt-get --fix-broken install  
```
```
 sudo apt-get -f install
```
```
 sudo apt-get clean
```
```
 sudo apt-get update
```
```
 sudo apt-get dist-upgrade
```

all to no avail...

And I still get the following error:

```

installArchives() failed: (Reading database ... 
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
(Reading database ... 227273 files and directories currently installed.) 
Preparing to unpack .../libldap-2.4-2_2.4.41+dfsg-1ubuntu2_amd64.deb ... 
Unpacking libldap-2.4-2:amd64 (2.4.41+dfsg-1ubuntu2) ... 
dpkg: error processing archive /var/cache/apt/archives/libldap-2.4-2_2.4.41+dfsg-1ubuntu2_amd64.deb (--unpack): 
 trying to overwrite shared '/etc/ldap/ldap.conf', which is different from other instances of package libldap-2.4-2:amd64 
Processing triggers for man-db (2.7.4-1) ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/libldap-2.4-2_2.4.41+dfsg-1ubuntu2_amd64.deb 
Error in function:  
dpkg: dependency problems prevent configuration of evolution-data-server: 
 evolution-data-server depends on libldap-2.4-2 (>= 2.4.7); however: 
  Package libldap-2.4-2:amd64 is not installed. 
 
dpkg: error processing package evolution-data-server (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of samba-libs:amd64: 
 samba-libs:amd64 depends on libldap-2.4-2 (>= 2.4.7); however: 
  Package libldap-2.4-2:amd64 is not installed. 
 
dpkg: error processing package samba-libs:amd64 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libcurl3:amd64: 
 libcurl3:amd64 depends on libldap-2.4-2 (>= 2.4.7); however: 
  Package libldap-2.4-2:amd64 is not installed. 
 
dpkg: error processing package libcurl3:amd64 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libcurl3-gnutls:amd64: 
 libcurl3-gnutls:amd64 depends on libldap-2.4-2 (>= 2.4.7); however: 
  Package libldap-2.4-2:amd64 is not installed. 
 
dpkg: error processing package libcurl3-gnutls:amd64 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libldb1:amd64: 
 libldb1:amd64 depends on libldap-2.4-2 (>= 2.4.7); however: 
  Package libldap-2.4-2:amd64 is not installed. 
 
dpkg: error processing package libldb1:amd64 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of python-samba: 
 python-samba depends on libldb1 (>= 0.9.21); however: 
  Package libldb1:amd64 is not configured yet. 
 python-samba depends on samba-libs (= 2:4.1.17+dfsg-4ubuntu3); however: 
  Package samba-libs:amd64 is not configured yet. 
 
dpkg: error processing package python-samba (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libfolks-eds25:amd64: 
 libfolks-eds25:amd64 depends on evolution-data-server (>= 3.2.0); however: 
  Package evolution-data-server is not configured yet. 
 
dpkg: error processing package libfolks-eds25:amd64 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-core: 
 libreoffice-core depends on libcurl3-gnutls (>= 7.16.2); however: 
  Package libcurl3-gnutls:amd64 is not configured yet. 
 libreoffice-core depends on libldap-2.4-2 (>= 2.4.7); however: 
  Package libldap-2.4-2:amd64 is not installed. 
 
dpkg: error processing package libreoffice-core (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-calc: 
 libreoffice-calc depends on libreoffice-core (= 1:5.0.2-0ubuntu1); however: 
  Package libreoffice-core is not configured yet. 
 
dpkg: error processing package libreoffice-calc (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of whoopsie: 
 whoopsie depends on libcurl3 (>= 7.16.2); however: 
  Package libcurl3:amd64 is not configured yet. 
 
dpkg: error processing package whoopsie (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libsmbclient:amd64: 
 libsmbclient:amd64 depends on samba-libs (= 2:4.1.17+dfsg-4ubuntu3); however: 
  Package samba-libs:amd64 is not configured yet. 
 
dpkg: error processing package libsmbclient:amd64 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnome-contacts: 
 gnome-contacts depends on libfolks-eds25 (>= 0.7.3); however: 
  Package libfolks-eds25:amd64 is not configured yet. 
 
dpkg: error processing package gnome-contacts (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of liboauth0:amd64: 
```


This question also asked (accidentally) at:  [http://askubuntu.com/questions/712211/libldap-dpkg-errors](http://askubuntu.com/questions/712211/libldap-dpkg-errors)  (under different login...grr...please consolidate here...)

Many thanks to the Hero Sys Admin who will save me....

Thanks,
Steve

---

### Post by matt_symes on 2015-12-22
Hi

Firstly, can we have a look at your sources please.

From the terminal

```
grep "^[^#]" /etc/apt/sources.list{,.d/*}
```

and

```
apt-cache policy libldap-2.4-2 "libldap-2.4-2_2.4.41*"
```

```
dpkg -l libldap-2.4-2 "libldap-2.4-2_2.4.41*"
```

Let's see where that gets us as far as package state goes.

Kind regards

---

### Post by steven-misshula on 2015-12-22
Hi Matt:

In order, we get the following - From:
```
 grep "^[^#]" /etc/apt/sources.list{,.d/*} 
```

we get:
```

/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ wily main restricted
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ wily main restricted
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ wily-updates main restricted
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates main restricted
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ wily universe
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ wily universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ wily-updates universe
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ wily multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ wily multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ wily-updates multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ wily-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ wily-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu wily-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu wily-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu wily-security universe
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu wily-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu wily-security multiverse
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu wily-security multiverse
/etc/apt/sources.list.d/ubuntu-wine-ubuntu-ppa-vivid.list.distUpgrade:deb-src  http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu vivid main
/etc/apt/sources.list.d/wine-ubuntu-wine-builds-wily.list.save:deb http://ppa.launchpad.net/wine/wine-builds/ubuntu wily main

```

From:
```
 apt-cache policy libldap-2.4-2 "libldap-2.4-2_2.4.41*" 
```

We get:
```

libldap-2.4-2:
  Installed: (none)
  Candidate: 2.4.41+dfsg-1ubuntu2
  Version table:
     2.4.41+dfsg-1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily/main amd64 Packages
        100 /var/lib/dpkg/status
N: Unable to locate package libldap-2.4-2_2.4.41*
N: Couldn't find any package by regex 'libldap-2.4-2_2.4.41*'

```

And finally - from 

```
   dpkg -l libldap-2.4-2 "libldap-2.4-2_2.4.41*" 
```

We get:
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ic  libldap-2.4-2: 2.4.41+dfsg- amd64        OpenLDAP libraries
rc  libldap-2.4-2: 2.4.41+dfsg- i386         OpenLDAP libraries
dpkg-query: no packages found matching libldap-2.4-2_2.4.41*


```

---

### Post by matt_symes on 2015-12-22
Hi

It looks like it's trying to install the package libldap-2.4-2 using the deb archive libldap-2.4-2_2.4.41+dfsg-1ubuntu2_amd64.deb.

This is failing though due to the file...

```
/etc/ldap/ldap.conf
```

How come you have an ldap configuration file if libldap is not installed ? I'm no expert with ldap so it would be really useful if you could answer this question for me.

Anyway, in the first instance i recommend we move the existing ldap file aside, fix the package manager and the see what's in that ldap file.

If you have any concerns about this resolution then don't do the steps below as, like i said, i'm no ldap expert. Post back if you have concerns.

```
sudo mv /etc/ldap/ldap.conf{,.old}
```

```
sudo apt-get -f install
```

Post back if you perform the above steps and then we'll see what we can do about that ldap.conf file.

Kind regards

---

### Post by steven-misshula on 2015-12-22
Hmmmmm.....  :-(

This:
```
/etc/ldap/ldap.conf
```

Gets me the following:
```
/etc/ldap/ldap.conf
```

> How come you have an ldap configuration file if libldap is not installed ? 

I am pretty sure that this happened when I was trying to fix things on my own...i.e. I saw that I have an ldap file and I did a, "sudo apt-get install....."  For whatever it is worth, I had problems before I loaded that...

I also suppose at this point I should confess I have slightly more than no idea of what the heck I'm doing and a comparable amount of patience...and thus I'm in this situation..  But hey, if we don't do, do we learn?

>  Anyway, in the first instance i recommend we move the existing ldap file aside, fix the package manager and the see what's in that ldap file.
If you have any concerns about this resolution then don't do the steps below as, like i said, i'm no ldap expert. Post back if you have concerns.


No Concerns.... coding:
```
sudo mv /etc/ldap/ldap.conf{,.old}
```

gets me no output.

coding:
```
sudo apt-get -f install
```

gets me the following:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libldap-2.4-2
The following NEW packages will be installed:
  libldap-2.4-2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
81 not fully installed or removed.
Need to get 0 B/162 kB of archives.
After this operation, 521 kB of additional disk space will be used.
Do you want to continue? [Y/n

```

to which I have said "Y"

and the update seems to be taking its sweet time....I'll post shortly.

Humbly yours,
Steve

---

### Post by steven-misshula on 2015-12-22
Having responded to the prompt yields:

```

(Reading database ... 227273 files and directories currently installed.)
Preparing to unpack .../libldap-2.4-2_2.4.41+dfsg-1ubuntu2_amd64.deb ...
Unpacking libldap-2.4-2:amd64 (2.4.41+dfsg-1ubuntu2) ...
Processing triggers for man-db (2.7.4-1) ...
Setting up libldap-2.4-2:amd64 (2.4.41+dfsg-1ubuntu2) ...
Setting up libldb1:amd64 (2:1.1.20-2) ...
Setting up libcurl3-gnutls:amd64 (7.43.0-1ubuntu2) ...
Setting up liboauth0:amd64 (1.0.1-1) ...
Setting up libraptor2-0:amd64 (2.0.14-1) ...
Setting up librasqal3:amd64 (0.9.32-1) ...
Setting up librdf0:amd64 (1.0.17-1) ...
Setting up python-ldb (2:1.1.20-2) ...
Setting up libcurl3:amd64 (7.43.0-1ubuntu2) ...
Setting up whoopsie (0.2.49.1) ...
Setting up libquvi7:amd64 (0.4.1-3) ...
Setting up samba-libs:amd64 (2:4.1.17+dfsg-4ubuntu3) ...
Setting up libsmbclient:amd64 (2:4.1.17+dfsg-4ubuntu3) ...
Setting up python3-pycurl (7.19.5.1-1ubuntu2) ...
Setting up python3-software-properties (0.96.13.1) ...
Setting up software-properties-common (0.96.13.1) ...
Setting up software-properties-gtk (0.96.13.1) ...
Setting up libtotem-plparser18:amd64 (3.10.5-1) ...
Setting up libbrasero-media3-1 (3.12.1-0ubuntu2) ...
Setting up brasero-cdrkit (3.12.1-0ubuntu2) ...
Setting up brasero (3.12.1-0ubuntu2) ...
Setting up libgdata22:amd64 (0.17.3-1) ...
Setting up gir1.2-gdata-0.0:amd64 (0.17.3-1) ...
Setting up librhythmbox-core9 (3.2.1-1ubuntu3.1) ...
Setting up gir1.2-rb-3.0 (3.2.1-1ubuntu3.1) ...
Setting up gir1.2-totem-plparser-1.0:amd64 (3.10.5-1) ...
Setting up libgrilo-0.2-1:amd64 (0.2.14-1) ...
Setting up libtotem0 (3.16.4-0ubuntu2) ...
Setting up gir1.2-totem-1.0 (3.16.4-0ubuntu2) ...
Setting up grilo-plugins-0.2-base:amd64 (0.2.14-5ubuntu1) ...
Setting up gvfs-backends (1.24.2-0ubuntu4) ...
Setting up kerneloops-daemon (0.12+git20090217-3ubuntu8) ...
Setting up libcmis-0.5-5v5 (0.5.0-3ubuntu1) ...
Setting up libreoffice-core (1:5.0.2-0ubuntu1) ...
Setting up libreoffice-pdfimport (1:5.0.2-0ubuntu1) ...
Setting up libreoffice-avmedia-backend-gstreamer (1:5.0.2-0ubuntu1) ...
Setting up libreoffice-base-core (1:5.0.2-0ubuntu1) ...
Setting up libreoffice-calc (1:5.0.2-0ubuntu1) ...
Setting up libreoffice-draw (1:5.0.2-0ubuntu1) ...
Setting up libreoffice-gtk (1:5.0.2-0ubuntu1) ...
Setting up libreoffice-impress (1:5.0.2-0ubuntu1) ...
Setting up libreoffice-math (1:5.0.2-0ubuntu1) ...
Setting up libreoffice-writer (1:5.0.2-0ubuntu1) ...
Setting up python-samba (2:4.1.17+dfsg-4ubuntu3) ...
Setting up samba-common-bin (2:4.1.17+dfsg-4ubuntu3) ...
Setting up python3-smbc (1.0.15.4-0ubuntu1) ...
Setting up rhythmbox (3.2.1-1ubuntu3.1) ...
Setting up rhythmbox-plugins (3.2.1-1ubuntu3.1) ...
Setting up rhythmbox-plugin-zeitgeist (3.2.1-1ubuntu3.1) ...
Setting up rhythmbox-plugin-cdrecorder (3.2.1-1ubuntu3.1) ...
Setting up rhythmbox-plugin-magnatune (3.2.1-1ubuntu3.1) ...
Setting up seahorse (3.16.0-1ubuntu1) ...
Setting up software-center (13.10-0ubuntu12) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.
Setting up system-config-printer-common (1.5.7+20150819-0ubuntu4) ...
Setting up system-config-printer-gnome (1.5.7+20150819-0ubuntu4) ...
Setting up totem (3.16.4-0ubuntu2) ...
Setting up totem-plugins (3.16.4-0ubuntu2) ...
Setting up transmission-gtk (2.84-1ubuntu1) ...
Setting up unity-lens-photos (1.0+14.04.20140318-0ubuntu1) ...
Setting up unity-scope-musicstores (6.9.0+15.04.20141219-0ubuntu1) ...
Setting up libreoffice-ogltrans (1:5.0.2-0ubuntu1) ...
Setting up unity-scope-gdrive (0.9+13.10.20130723-0ubuntu1) ...
Setting up gconf-service (3.2.6-3ubuntu5) ...
Setting up gnome-terminal (3.16.2-1ubuntu4) ...
update-alternatives: using /usr/bin/gnome-terminal.wrapper to provide /usr/bin/x-terminal-emulator (x-terminal-emulator) in auto mode
Setting up network-manager-gnome (0.9.10.1-0ubuntu7) ...
Setting up gconf-service-backend (3.2.6-3ubuntu5) ...
Setting up gconf2 (3.2.6-3ubuntu5) ...
Setting up aisleriot (1:3.16.2-0ubuntu1) ...
Setting up apturl (0.5.2ubuntu9) ...
Setting up unity-control-center (15.04.0+15.10.20150923-0ubuntu1) ...
Setting up compiz-gnome (1:0.9.12.2+15.10.20151015-0ubuntu1) ...
Setting up compiz (1:0.9.12.2+15.10.20151015-0ubuntu1) ...
Setting up evolution-data-server (3.16.5-1ubuntu3) ...
Setting up libedata-book-1.2-25 (3.16.5-1ubuntu3) ...
Setting up libebook-1.2-16 (3.16.5-1ubuntu3) ...
Setting up libfolks-eds25:amd64 (0.11.1-2build1) ...
Setting up gnome-contacts (3.16.2-1ubuntu1) ...
Setting up libreoffice-gnome (1:5.0.2-0ubuntu1) ...
Setting up nautilus-share (0.7.3-1ubuntu5) ...
Setting up unity (7.3.2+15.10.20151016-0ubuntu1) ...
Setting up ubuntu-desktop (1.341) ...
Setting up indicator-bluetooth (0.0.6+15.10.20150929-0ubuntu1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...


```

Also, I had a little warning symbol at the top of my screen (next to the network connection icon) which seems to have gone away!  Yay!  

Restarting to install updates.
double yay!

---

### Post by matt_symes on 2015-12-22
Hi

> **steven-misshula said:**
> Hmmmmm.....  :-(

This:
```
/etc/ldap/ldap.conf
```

Gets me the following:
```
/etc/ldap/ldap.conf
```


That wasn't a command for you to run. I was just highlighting the problem file :)

Kind regards

---

### Post by steven-misshula on 2015-12-22
Matt -

KUDOS to you!!!  

Many thanks for the help - I'm calling this resolved from what I can see...

Many thanks!!

Steve

---

### Post by matt_symes on 2015-12-22
Hi

> **steven-misshula said:**
> Matt -

KUDOS to you!!!  

Many thanks for the help - I'm calling this resolved from what I can see...

Many thanks!!

Steve

Do you want to see what was in that old ldap.conf file ?

If not then please mark this thread as SOLVED using the thread tools link.

Kind regards

---

### Post by steven-misshula on 2015-12-22
ya - sure...

what is an ldap file anyway....?  (hate to sound naive, but I'm more of a newb than anything...)

anything to code...?

Steve

---

### Post by matt_symes on 2015-12-22
Hi

> **steven-misshula said:**
> ya - sure...

what is an ldap file anyway....?  (hate to sound naive, but I'm more of a newb than anything...)

anything to code...?

Steve

ldap is an active directory like system for Linux.

Please post the output of

```
cat /etc/ldap/ldap.conf.old
```

If there is nothing useful in the file then we can delete it and mark this thread as totally SOLVED.

Kind regards

---

### Post by steven-misshula on 2015-12-22
So....I think i noticed a problem....we are not completely resolved...

In this mess, I lost my ability to use wiFi .... I thought it would be corrected with that package...but it is not...should I open a new string?


As for the LDAP:

```

cat /etc/ldap/ldap.conf.old 
```

gets the following:

```


#
# LDAP Defaults
#

# See ldap.conf(5) for details
# This file should be world readable but not world writable.

#BASE    dc=example,dc=com
#URI    ldap://ldap.example.com ldap://ldap-master.example.com:666

#SIZELIMIT    12
#TIMELIMIT    15
#DEREF        never

# TLS certificates (needed for GnuTLS)
TLS_CACERT    /etc/ssl/certs/ca-certificates.crt


```

---

### Post by matt_symes on 2015-12-22
Hi

> **steven-misshula said:**
> So....I think i noticed a problem....we are not completely resolved...

In this mess, I lost my ability to use wiFi .... I thought it would be corrected with that package...but it is not...should I open a new string?


You'll need to open a new thread for that issue in the "Wireless and Networking" forum. 

Reboot first though, just in case it needs it.

> 
As for the LDAP:

```

cat /etc/ldap/ldap.conf.old 
```

gets the following:

```


#
# LDAP Defaults
#

# See ldap.conf(5) for details
# This file should be world readable but not world writable.

#BASE    dc=example,dc=com
#URI    ldap://ldap.example.com ldap://ldap-master.example.com:666

#SIZELIMIT    12
#TIMELIMIT    15
#DEREF        never

# TLS certificates (needed for GnuTLS)
TLS_CACERT    /etc/ssl/certs/ca-certificates.crt


```

Well that file has content. Can we compare it with the new file. Please post the output of

```
cat /etc/ldap/ldap.conf
``` 

Kind regards

---

### Post by steven-misshula on 2015-12-22
No problem - coding:
```
cat /etc/ldap/ldap.conf 
```
gets me this:

```

cat: /etc/ldap/ldap.conf: No such file or directory
```

Steve

---

### Post by matt_symes on 2015-12-22
Hi

> **steven-misshula said:**
> No problem - coding:
```
cat /etc/ldap/ldap.conf 
```
gets me this:

```

cat: /etc/ldap/ldap.conf: No such file or directory
```

Steve

Oh ! Alright then..

```
sudo rm /etc/ldap/ldap.conf.old
```

Then please mark this thread as solved :)

Is your wireless still not working ?

Kind regards

---

### Post by steven-misshula on 2015-12-22
Coded:

```
sudo rm /etc/ldap/ldap.conf.old
```

which i think removed the file...? no?  i.e. - no great interesting output in the terminal....  

WiFi is still hosed...opening a string...

---

### Post by matt_symes on 2015-12-22
Hi

I just checked the contents of libldap-2.4-2 and it looks like it should have installed an ldap.conf file.

I thought that was a bit odd so i double checked.

Here's the contents of the package libldap-2.4-2.

```

matthew-xu-16-04:/home/matthew:0 % apt-file list libldap-2.4-2
**libldap-2.4-2: /etc/ldap/ldap.conf**
libldap-2.4-2: /usr/lib/x86_64-linux-gnu/liblber-2.4.so.2
libldap-2.4-2: /usr/lib/x86_64-linux-gnu/liblber-2.4.so.2.10.4
libldap-2.4-2: /usr/lib/x86_64-linux-gnu/libldap-2.4.so.2
libldap-2.4-2: /usr/lib/x86_64-linux-gnu/libldap_r-2.4.so.2
libldap-2.4-2: /usr/lib/x86_64-linux-gnu/libldap_r-2.4.so.2.10.4
libldap-2.4-2: /usr/share/doc/libldap-2.4-2/README.Debian
libldap-2.4-2: /usr/share/doc/libldap-2.4-2/changelog.Debian.gz
libldap-2.4-2: /usr/share/doc/libldap-2.4-2/copyright
libldap-2.4-2: /usr/share/lintian/overrides/libldap-2.4-2
libldap-2.4-2: /usr/share/man/man5/ldap.conf.5.gz
libldap-2.4-2-dbg: /usr/lib/debug/.build-id/8e/3004a119737d5140179e1629fdf9813cf76969.debug
libldap-2.4-2-dbg: /usr/lib/debug/.build-id/e7/c7f6a38fb86ada77c7a49e1c5d78d04bad8d67.debug
libldap-2.4-2-dbg: /usr/share/doc/libldap-2.4-2-dbg/changelog.Debian.gz
libldap-2.4-2-dbg: /usr/share/doc/libldap-2.4-2-dbg/copyright
matthew-xu-16-04:/home/matthew:0
```

You did not get that file installed for some reason when apt-get -f install was run.

There may still be problems with your system. The wifi would hint at that as well.

Can you run 

```
sudo apt-get check
```

```
dpkg -l libldap-2.4-2
```

```
apt-cache policy libldap-2.4-2
```

and 

```
sudo dpkg -C
```

If there is any output the commands above then please post it back here.

Kind regards

---

### Post by steven-misshula on 2015-12-23
Hi Matt- I don't have access to the laptop right now...(I'm at the office).  When I get home I will post.

Thanks for the follow through and Merry X-mas!
Steve

---

### Post by steven-misshula on 2015-12-23
Hi Matt,

Thanks for the patience - hope your holiday prep is going well...

1.  ```

sudo apt-get check
```

Yields nothing...or close to nothing...see below:

1a.```
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```


2.```
dpkg -l libldap-2.4-2
```

yields the following:

2a.```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libldap-2.4-2: 2.4.41+dfsg- amd64        OpenLDAP libraries
rc  libldap-2.4-2: 2.4.41+dfsg- i386         OpenLDAP libraries
estelle@estelle-Satellite-C675:~$ ^C
```

3. ```

apt-cache policy libldap-2.4-2
```

yields the following:



3a.```
  Installed: 2.4.41+dfsg-1ubuntu2
  Candidate: 2.4.41+dfsg-1ubuntu2
  Version table:
 *** 2.4.41+dfsg-1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily/main amd64 Packages
        100 /var/lib/dpkg/status
```

4. ```

sudo dpkg -C
```

Yields nothing....

---

### Post by matt_symes on 2015-12-24
Hi

Sorry for the late reply. Too many things to get ready.

> **steven-misshula said:**
> 
2a.```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libldap-2.4-2: 2.4.41+dfsg- amd64        OpenLDAP libraries
**rc  libldap-2.4-2: 2.4.41+dfsg- i386         OpenLDAP libraries**
estelle@estelle-Satellite-C675:~$ ^C
```


That explains where the file /etc/ldap/ldap.conf file came from then. It's the 32 bit version of the package.

Let's see if anything you have installed reverse depends on it; if it has reverse dependencies. Run this command in the terminal.

```
apt-cache rdepends --installed libldap-2.4-2:i386
```

** If it returns **no** reserve dependencies (no entries under *Reverse Depends:*, *the same as this below*)
 
```

matthew-xu-16-04:/home/matthew:0 % apt-cache rdepends --installed libldap-2.4-2:i386 
libldap-2.4-2:i386
Reverse Depends:
matthew-xu-16-04:/home/matthew:0 %
```

...then run this command 

```
sudo touch /etc/ldap/ldap.conf
```

and this to remove the remains of that package

```
sudo apt-get purge libldap-2.4-2:i386
```

and then copy and paste the whole of this block into the terminal. Hit <enter> and then, if you are asked, enter your password as usual. It'll recreate you ldap.conf file for you.

```

cat<<EOF | sudo tee /etc/ldap/ldap.conf
#
# LDAP Defaults
#

# See ldap.conf(5) for details
# This file should be world readable but not world writable.

#BASE   dc=example,dc=com
#URI    ldap://ldap.example.com ldap://ldap-master.example.com:666

#SIZELIMIT      12
#TIMELIMIT      15
#DEREF          never

# TLS certificates (needed for GnuTLS)
TLS_CACERT      /etc/ssl/certs/ca-certificates.crt
EOF
```

and then could you post the output of this command so we can check the packages files.

```
while read f; do [[ ! -e "$f" ]] && echo "$f"; done < <(dpkg -L libldap-2.4-2:amd64)
```

** If it **does return** reverse dependencies then don't run the above four commands but post back the output of that reverse dependencies command and we'll take a further look to see what is dependent upon it. 

Apart from that, your package manager looks in a good state.

BTW: How's the wifi on the laptop ?

Kind regards

---

### Post by steven-misshula on 2015-12-24
Hi - this was simple...only b/c it has the reverse depends... see below.


```

apt-cache rdepends --installed libldap-2.4-2:i386
```

yields the following:
```

libldap-2.4-2:i386
Reverse Depends:
  libldap-2.4-2
  libldap-2.4-2
```


As for the wi-fi still stuck on that...ran the "wifi" script...and posted my output / tar file (it was too big).  Now just waiting on the next input from my Linux overlords... :-P  my attempt at humor.

If you are curious in so much as it may apply here... the link for that issue:  [http://ubuntuforums.org/showthread.php?t=2307217&p=13411322#post13411322](http://ubuntuforums.org/showthread.php?t=2307217&p=13411322#post13411322) 

Merry X-mas!
Steve

---

### Post by matt_symes on 2015-12-24
Hi

> **steven-misshula said:**
> 

```

apt-cache rdepends --installed libldap-2.4-2:i386
```

yields the following:
```

libldap-2.4-2:i386
Reverse Depends:
  libldap-2.4-2
  libldap-2.4-2
```

It depends on itself. Hmm. It shouldn't.

Alright. Go back to my last post and run the commands i asked you not to run and run them anyway :)

Post back any errors and the results of the last command if the others don't error.

Kind regards

---

### Post by steven-misshula on 2015-12-24
hmmmmm....
```

sudo touch /etc/ldap/ldap.conf
```

gets me nothing....
```

sudo apt-get purge libldap-2.4-2:i386
```

gets the following (to which i chose YES):

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libldap-2.4-2:i386*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 234270 files and directories currently installed.)
Removing libldap-2.4-2:i386 (2.4.41+dfsg-1ubuntu2) ...
Purging configuration files for libldap-2.4-2:i386 (2.4.41+dfsg-1ubuntu2) ...

```

and from:

```

cat<<EOF | sudo tee /etc/ldap/ldap.conf
#
# LDAP Defaults
#

# See ldap.conf(5) for details
# This file should be world readable but not world writable.

#BASE   dc=example,dc=com
#URI    ldap://ldap.example.com ldap://ldap-master.example.com:666

#SIZELIMIT      12
#TIMELIMIT      15
#DEREF          never

# TLS certificates (needed for GnuTLS)
TLS_CACERT      /etc/ssl/certs/ca-certificates.crt
EOF
```



I get:

```
# LDAP Defaults
#

# See ldap.conf(5) for details
# This file should be world readable but not world writable.

#BASE   dc=example,dc=com
#URI    ldap://ldap.example.com ldap://ldap-master.example.com:666

#SIZELIMIT      12
#TIMELIMIT      15
#DEREF          never

# TLS certificates (needed for GnuTLS)
TLS_CACERT      /etc/ssl/certs/ca-certificates.crt


```

finally, from
```

while read f; do [[ ! -e "$f" ]] && echo "$f"; done < <(dpkg -L libldap-2.4-2:amd64)
```


i get no output...


UPDATE:  The WiFi is resolved....turns out it was Hardware Blocked (i.e. - Function Key + F8 Key; and it is resolved).

Best,
Steve

---

### Post by matt_symes on 2015-12-24
Hi

> **steven-misshula said:**
> hmmmmm....
```

sudo touch /etc/ldap/ldap.conf
```

gets me nothing....
```

sudo apt-get purge libldap-2.4-2:i386
```

gets the following (to which i chose YES):

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libldap-2.4-2:i386*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 234270 files and directories currently installed.)
Removing libldap-2.4-2:i386 (2.4.41+dfsg-1ubuntu2) ...
Purging configuration files for libldap-2.4-2:i386 (2.4.41+dfsg-1ubuntu2) ...

```

and from:

```

cat<<EOF | sudo tee /etc/ldap/ldap.conf
#
# LDAP Defaults
#

# See ldap.conf(5) for details
# This file should be world readable but not world writable.

#BASE   dc=example,dc=com
#URI    ldap://ldap.example.com ldap://ldap-master.example.com:666

#SIZELIMIT      12
#TIMELIMIT      15
#DEREF          never

# TLS certificates (needed for GnuTLS)
TLS_CACERT      /etc/ssl/certs/ca-certificates.crt
EOF
```



I get:

```
# LDAP Defaults
#

# See ldap.conf(5) for details
# This file should be world readable but not world writable.

#BASE   dc=example,dc=com
#URI    ldap://ldap.example.com ldap://ldap-master.example.com:666

#SIZELIMIT      12
#TIMELIMIT      15
#DEREF          never

# TLS certificates (needed for GnuTLS)
TLS_CACERT      /etc/ssl/certs/ca-certificates.crt


```

finally, from
```

while read f; do [[ ! -e "$f" ]] && echo "$f"; done < <(dpkg -L libldap-2.4-2:amd64)
```


i get no output...


UPDATE:  The WiFi is resolved....turns out it was Hardware Blocked (i.e. - Function Key + F8 Key; and it is resolved).

Best,
Steve

Excellent ! The output you described is exactly what i was looking for.

No output after a command is usually a success and not failure unless the command naturally produces output (like apt-get).

That should have fixed your libldap problem (64 bit).

To be honest, we had the information to fix it after post #5 but i didn't realise. It's been a busy couple of days as you may understand; my only excuse.

I cannot guarantee that your package manager is totally fixed as I'm not sure why you had the 32 bit version of libldap on your system.

You now don't have the 32 bit version of that library on your system and i don't know if you need it.

If you post the output of the command below, it'll give me an idea of whether you do or not and we can run some final commands after to finish this thread off.

```
dpkg -l "*:i386" | wc -l
```

Kind regards

---

### Post by steven-misshula on 2015-12-25
Hey - no worries - I've enjoyed the learning process....it teaches me I know nothing and hey, ignorance is bliss...right?
```

dpkg -l "*:i386" | wc -l
```

gets me the following:

```
149

```

Does that mean anything...?

Best,
Steve

---

### Post by matt_symes on 2015-12-25
Hi

> **steven-misshula said:**
> Hey - no worries - I've enjoyed the learning process....it teaches me I know nothing and hey, ignorance is bliss...right?
```

dpkg -l "*:i386" | wc -l
```

gets me the following:

```
149

```

Does that mean anything...?

It means you have 149 32-bit libraries installed on your system. I don't know if you need them as i don;t know what is dependent upon them but i shouldn't do any harm (hopefully) to reinstall the 32 bit version of libldap.

```
sudo apt-get install libldap-2.4-2:i386
```

If there are no errors then you should be good to go.

Kind regards

---

### Post by steven-misshula on 2015-12-25
Hi Matt-
Many thanks again for taking the time on this one.    And now I have all the steps to follow when I try Wine again....!!!!  :p

```

sudo apt-get install libldap-2.4-2:i386
```
 

gets me the following (no errors that I could see...):

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libasn1-8-heimdal:i386 libffi6:i386 libgmp10:i386 libgnutls-deb0-28:i386
  libgssapi3-heimdal:i386 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhogweed4:i386 libhx509-5-heimdal:i386
  libkrb5-26-heimdal:i386 libnettle6:i386 libp11-kit0:i386
  libroken18-heimdal:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsasl2-modules-db:i386 libsqlite3-0:i386 libssl1.0.0:i386 libtasn1-6:i386
  libwind0-heimdal:i386
Suggested packages:
  gnutls-bin:i386 libsasl2-modules-otp:i386 libsasl2-modules-ldap:i386
  libsasl2-modules-sql:i386 libsasl2-modules-gssapi-mit:i386
  libsasl2-modules-gssapi-heimdal:i386
The following NEW packages will be installed:
  libasn1-8-heimdal:i386 libffi6:i386 libgmp10:i386 libgnutls-deb0-28:i386
  libgssapi3-heimdal:i386 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhogweed4:i386 libhx509-5-heimdal:i386
  libkrb5-26-heimdal:i386 libldap-2.4-2:i386 libnettle6:i386 libp11-kit0:i386
  libroken18-heimdal:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsasl2-modules-db:i386 libsqlite3-0:i386 libssl1.0.0:i386 libtasn1-6:i386
  libwind0-heimdal:i386
0 upgraded, 22 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,670 kB of archives.
After this operation, 11.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ wily/main libffi6 i386 3.2.1-3 [16.9 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ wily/main libgmp10 i386 2:6.0.0+dfsg-7 [244 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ wily/main libnettle6 i386 3.1.1-4 [110 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ wily/main libhogweed4 i386 3.1.1-4 [137 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ wily/main libp11-kit0 i386 0.23.1-3 [110 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ wily/main libtasn1-6 i386 4.5-2 [44.6 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ wily/main libgnutls-deb0-28 i386 3.3.15-5ubuntu2 [539 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ wily/main libroken18-heimdal i386 1.6~rc2+dfsg-10ubuntu1 [43.9 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ wily/main libasn1-8-heimdal i386 1.6~rc2+dfsg-10ubuntu1 [184 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ wily/main libhcrypto4-heimdal i386 1.6~rc2+dfsg-10ubuntu1 [89.9 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ wily/main libheimbase1-heimdal i386 1.6~rc2+dfsg-10ubuntu1 [32.0 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ wily/main libwind0-heimdal i386 1.6~rc2+dfsg-10ubuntu1 [48.8 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ wily/main libhx509-5-heimdal i386 1.6~rc2+dfsg-10ubuntu1 [118 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ wily/main libsqlite3-0 i386 3.8.11.1-1 [408 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ wily/main libkrb5-26-heimdal i386 1.6~rc2+dfsg-10ubuntu1 [226 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ wily/main libheimntlm0-heimdal i386 1.6~rc2+dfsg-10ubuntu1 [16.7 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ wily/main libgssapi3-heimdal i386 1.6~rc2+dfsg-10ubuntu1 [104 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ wily/main libsasl2-modules-db i386 2.1.26.dfsg1-14 [15.5 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ wily/main libsasl2-2 i386 2.1.26.dfsg1-14 [52.2 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ wily/main libldap-2.4-2 i386 2.4.41+dfsg-1ubuntu2 [174 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu/ wily-updates/main libssl1.0.0 i386 1.0.2d-0ubuntu1.2 [908 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu/ wily/main libsasl2-modules i386 2.1.26.dfsg1-14 [50.9 kB]
Fetched 3,670 kB in 12s (284 kB/s)                                             
Preconfiguring packages ...
Selecting previously unselected package libffi6:i386.
(Reading database ... 234087 files and directories currently installed.)
Preparing to unpack .../libffi6_3.2.1-3_i386.deb ...
Unpacking libffi6:i386 (3.2.1-3) ...
Selecting previously unselected package libgmp10:i386.
Preparing to unpack .../libgmp10_2%3a6.0.0+dfsg-7_i386.deb ...
Unpacking libgmp10:i386 (2:6.0.0+dfsg-7) ...
Selecting previously unselected package libnettle6:i386.
Preparing to unpack .../libnettle6_3.1.1-4_i386.deb ...
Unpacking libnettle6:i386 (3.1.1-4) ...
Selecting previously unselected package libhogweed4:i386.
Preparing to unpack .../libhogweed4_3.1.1-4_i386.deb ...
Unpacking libhogweed4:i386 (3.1.1-4) ...
Selecting previously unselected package libp11-kit0:i386.
Preparing to unpack .../libp11-kit0_0.23.1-3_i386.deb ...
Unpacking libp11-kit0:i386 (0.23.1-3) ...
Selecting previously unselected package libtasn1-6:i386.
Preparing to unpack .../libtasn1-6_4.5-2_i386.deb ...
Unpacking libtasn1-6:i386 (4.5-2) ...
Selecting previously unselected package libgnutls-deb0-28:i386.
Preparing to unpack .../libgnutls-deb0-28_3.3.15-5ubuntu2_i386.deb ...
Unpacking libgnutls-deb0-28:i386 (3.3.15-5ubuntu2) ...
Selecting previously unselected package libroken18-heimdal:i386.
Preparing to unpack .../libroken18-heimdal_1.6~rc2+dfsg-10ubuntu1_i386.deb ...
Unpacking libroken18-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Selecting previously unselected package libasn1-8-heimdal:i386.
Preparing to unpack .../libasn1-8-heimdal_1.6~rc2+dfsg-10ubuntu1_i386.deb ...
Unpacking libasn1-8-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Selecting previously unselected package libhcrypto4-heimdal:i386.
Preparing to unpack .../libhcrypto4-heimdal_1.6~rc2+dfsg-10ubuntu1_i386.deb ...
Unpacking libhcrypto4-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Selecting previously unselected package libheimbase1-heimdal:i386.
Preparing to unpack .../libheimbase1-heimdal_1.6~rc2+dfsg-10ubuntu1_i386.deb ...
Unpacking libheimbase1-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Selecting previously unselected package libwind0-heimdal:i386.
Preparing to unpack .../libwind0-heimdal_1.6~rc2+dfsg-10ubuntu1_i386.deb ...
Unpacking libwind0-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Selecting previously unselected package libhx509-5-heimdal:i386.
Preparing to unpack .../libhx509-5-heimdal_1.6~rc2+dfsg-10ubuntu1_i386.deb ...
Unpacking libhx509-5-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Selecting previously unselected package libsqlite3-0:i386.
Preparing to unpack .../libsqlite3-0_3.8.11.1-1_i386.deb ...
Unpacking libsqlite3-0:i386 (3.8.11.1-1) ...
Selecting previously unselected package libkrb5-26-heimdal:i386.
Preparing to unpack .../libkrb5-26-heimdal_1.6~rc2+dfsg-10ubuntu1_i386.deb ...
Unpacking libkrb5-26-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Selecting previously unselected package libheimntlm0-heimdal:i386.
Preparing to unpack .../libheimntlm0-heimdal_1.6~rc2+dfsg-10ubuntu1_i386.deb ...
Unpacking libheimntlm0-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Selecting previously unselected package libgssapi3-heimdal:i386.
Preparing to unpack .../libgssapi3-heimdal_1.6~rc2+dfsg-10ubuntu1_i386.deb ...
Unpacking libgssapi3-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Selecting previously unselected package libsasl2-modules-db:i386.
Preparing to unpack .../libsasl2-modules-db_2.1.26.dfsg1-14_i386.deb ...
Unpacking libsasl2-modules-db:i386 (2.1.26.dfsg1-14) ...
Selecting previously unselected package libsasl2-2:i386.
Preparing to unpack .../libsasl2-2_2.1.26.dfsg1-14_i386.deb ...
Unpacking libsasl2-2:i386 (2.1.26.dfsg1-14) ...
Selecting previously unselected package libldap-2.4-2:i386.
Preparing to unpack .../libldap-2.4-2_2.4.41+dfsg-1ubuntu2_i386.deb ...
Unpacking libldap-2.4-2:i386 (2.4.41+dfsg-1ubuntu2) ...
Selecting previously unselected package libssl1.0.0:i386.
Preparing to unpack .../libssl1.0.0_1.0.2d-0ubuntu1.2_i386.deb ...
Unpacking libssl1.0.0:i386 (1.0.2d-0ubuntu1.2) ...
Selecting previously unselected package libsasl2-modules:i386.
Preparing to unpack .../libsasl2-modules_2.1.26.dfsg1-14_i386.deb ...
Unpacking libsasl2-modules:i386 (2.1.26.dfsg1-14) ...
Processing triggers for man-db (2.7.4-1) ...
Setting up libffi6:i386 (3.2.1-3) ...
Setting up libgmp10:i386 (2:6.0.0+dfsg-7) ...
Setting up libnettle6:i386 (3.1.1-4) ...
Setting up libhogweed4:i386 (3.1.1-4) ...
Setting up libp11-kit0:i386 (0.23.1-3) ...
Setting up libtasn1-6:i386 (4.5-2) ...
Setting up libgnutls-deb0-28:i386 (3.3.15-5ubuntu2) ...
Setting up libroken18-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Setting up libasn1-8-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Setting up libhcrypto4-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Setting up libheimbase1-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Setting up libwind0-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Setting up libhx509-5-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Setting up libsqlite3-0:i386 (3.8.11.1-1) ...
Setting up libkrb5-26-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Setting up libheimntlm0-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Setting up libgssapi3-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Setting up libsasl2-modules-db:i386 (2.1.26.dfsg1-14) ...
Setting up libsasl2-2:i386 (2.1.26.dfsg1-14) ...
Setting up libldap-2.4-2:i386 (2.4.41+dfsg-1ubuntu2) ...
Setting up libssl1.0.0:i386 (1.0.2d-0ubuntu1.2) ...
Setting up libsasl2-modules:i386 (2.1.26.dfsg1-14) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...


```

---

### Post by matt_symes on 2015-12-25
Hi

It looks good :) Enjoy.

Kind regards

---

