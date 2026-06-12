---
title: "Apt unable to install, upgrade or remove"
date: 2015-07-29
forum: Installation &amp; Upgrades
---

### Post by jrg010381 on 2015-07-29
Hello,

When attempting to upgrade, install or purge snmpd (or anything for that matter) I receive the following from apt:

```
root@:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up snmpd (5.7.2~dfsg-8.1ubuntu3) ...
update-rc.d: warning:  stop runlevel arguments (1) do not match snmpd Default-Stop values (0 1 6)
 * Starting network management services:                                                                                                                                                                                                  /usr/sbin/snmpd: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
invoke-rc.d: initscript snmpd, action "start" failed.
dpkg: error processing package snmpd (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 snmpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I searched around for possible fixes here and using Google, but nothing has worked. Here's what I've tried:
```
1946  dpkg --configure -a
1947  apt-get clean

1948  apt-get autoclean
1949  apt-get -f install

1951  pgrep dpkg | xargs kill -9
1952  pgrep apt-get | xargs kill -9
1954  dpkg --purge snmpd
1955  apt-get update
1956  apt-get install snmpd



```

Any ideas on how apt can be fixed?


Here's my sources.list
```
user@:~$ cat -n /etc/apt/sources.list
     1  #
     2
     3  # deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/main/binary-i386/
     4  # deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/restricted/binary-i386/
     5  # deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ precise main restricted
     6
     7  # deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/main/binary-i386/
     8  # deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/restricted/binary-i386/
     9  # deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ precise main restricted
    10
    11  # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
    12  # newer versions of the distribution.
    13  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
    14  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
    15
    16  ## Major bug fix updates produced after the final release of the
    17  ## distribution.
    18  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    19  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    20
    21  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    22  ## team. Also, please note that software in universe WILL NOT receive any
    23  ## review or updates from the Ubuntu security team.
    24  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
    25  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
    26  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
    27  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
    28
    29  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    30  ## team, and may not be under a free licence. Please satisfy yourself as to
    31  ## your rights to use the software. Also, please note that software in
    32  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    33  ## security team.
    34  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
    35  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
    36  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    37  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    38
    39  ## N.B. software from this repository may not have been tested as
    40  ## extensively as that contained in the main release, although it includes
    41  ## newer versions of some applications which may provide useful features.
    42  ## Also, please note that software in backports WILL NOT receive any review
    43  ## or updates from the Ubuntu security team.
    44  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    45  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    46
    47  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    48  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    49  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    50  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    51  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    52  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    53
    54  # Partner repository
    55  # deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
    56
    57  ## Uncomment the following two lines to add software from Canonical's
    58  ## 'partner' repository.
    59  ## This software is not part of Ubuntu, but is offered by Canonical and the
    60  ## respective vendors as a service to Ubuntu users.
    61  # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    62  # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    63
    64  ## Uncomment the following two lines to add software from Ubuntu's
    65  ## 'extras' repository.
    66  ## This software is not part of Ubuntu, but is offered by third-party
    67  ## developers who want to ship their latest software.
    68  # deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    69  # deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main



user@:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/webupd8team-java-precise.list <==


==> /etc/apt/sources.list.d/webupd8team-java-precise.list.distUpgrade <==
deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main


==> /etc/apt/sources.list.d/webupd8team-java-precise.list.save <==


```

****UPDATE****
```
I did the following:
1985  apt-get purge snmpd
1986  apt-get install -f
1987  apt-get autoremove
1988  apt-get autoclean
1989  dpkg --configure -a
1990  apt-get update
1991  apt-get upgrade
```

I can now successfully complete update and I assume install other packages. However, I still cannot install SNMPD. It still fails with the above error. This has now morphed into an issue where SNMPD appears to think it is installed, but isn't. See below:

```

user@:~$ snmpd
snmpd: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
user@:~$ sudo apt-get purge snmpd
[sudo] password for jgeremia:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'snmpd' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Bashing-om on 2015-07-29
jrg010381; Hello;

My thought after taking a look:
```

apt show snmpd

```
I see:
> 
Source: net-snmp


maybe try :
```

sudo apt-get install net-snmp

```

See what results ?

[INDENT][INDENT]maybe yes 
[/INDENT][/INDENT]

---

### Post by jrg010381 on 2015-07-29
Thanks for the reply!

I see the same thing as your for source, but unfortunately installing net-snmp is not located.
```

root@:~# apt show snmpd
Package: snmpd
Priority: optional
Section: net
Installed-Size: 232 kB
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Net-SNMP Packaging Team <pkg-net-snmp-devel@lists.alioth.debian.org>
Source: net-snmp
Version: 5.7.2~dfsg-8.1ubuntu3
Depends: libc6 (>= 2.4), libmysqlclient18 (>= 5.5.24+dfsg-1), libsnmp30 (>= 5.7.2~dfsg), libwrap0 (>= 7.6-4~), debconf (>= 0.5) | debconf-2.0, adduser, debconf, lsb-base (>= 3.2-13), libsnmp-base
Download-Size: 73.3 kB
Homepage: [http://net-snmp.sourceforge.net/](http://net-snmp.sourceforge.net/)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 5y
APT-Sources: [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
Description: SNMP (Simple Network Management Protocol) agents
 The Simple Network Management Protocol (SNMP) provides a framework
 for the exchange of management information between agents (servers)
 and clients.
 .
 The Net-SNMP agent is a daemon which listens for incoming SNMP
 requests from clients and provides responses.


root@:~# apt-get install net-snmp
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package net-snmp

```

---

### Post by Bashing-om on 2015-07-29
jrg010381; My bad !

In that I failed to follow through, I "assumed" 'net-snmp' was the proper package.
However: 
> 
sysop@1404mini:~$ apt-cache show net-snmp
N: Unable to locate package net-snmp
E: No packages found
sysop@1404mini:~$

tells me I am out there in left field, all alone.

Doing:
```

apt-cache search net-snmp

```
tells me the reverse is true.

So what have we ?
> 
Depends: libc6 (>= 2.4), libmysqlclient18 (>= 5.5.24+dfsg-1), libsnmp30 (>= 5.7.2~dfsg), libwrap0 (>= 7.6-4~), debconf (>= 0.5) | debconf-2.0, adduser, debconf, lsb-base (>= 3.2-13), libsnmp-base

let's make sure all of 'snmpd' dependencies are met ;
For each item see what is installed starting as for this example:
```

dpkg -l libc6
dpkg -l libmysqlclient18

```

As I do not have 'snmpd' nor 'mysql' installed, I can not test and verify your results.

we try and find the reason that the package manager
[INDENT][INDENT][INDENT]is UNhappy
[/INDENT][/INDENT][/INDENT]

---

### Post by PaulW2U on 2015-07-29
jrg010381, please use code tags when posting terminal output as they make long listings easier to read. 

If you are using New Reply button - highlight text and use the # button in the text box header. If you are using Quick Reply then add [noparse]```
 at the beginning of the section and 
```[/noparse] at the end.

---

### Post by ian-weisser on 2015-07-29
Looking at the most interesting part of the error message:
> **jrg010381 said:**
> /snmpd: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
invoke-rc.d: initscript snmpd, action "start" failed.

THAT's interesting, because Perl in **12.04** uses libperl.so.5.14. You seem to be using **14.04**, which uses libperl.so.5.18.

Could you please show us the output of:
```
apt-cache policy snmpd
apt-cache policy libsnmp30
```

---

### Post by jrg010381 on 2015-07-30
```
user@:~$ apt-cache policy snmpd
snmpd:
  Installed: 5.7.2~dfsg-8.1ubuntu3
  Candidate: 5.7.2~dfsg-8.1ubuntu3
  Version table:
 *** 5.7.2~dfsg-8.1ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
user@:~$ apt-cache policy libsnmp30
libsnmp30:
  Installed: 5.7.2~dfsg-8.1ubuntu3
  Candidate: 5.7.2~dfsg-8.1ubuntu3
  Version table:
 *** 5.7.2~dfsg-8.1ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by ian-weisser on 2015-07-30
Apt seems to think you have snmpd installed already. See the 'Installed' line.

If you try to run smnpd, does it work?

---

### Post by jrg010381 on 2015-07-30
It's weird!! 
```

user@:~$ snmpd
snmpd: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
```

---

### Post by jrg010381 on 2015-07-30
> **Bashing-om said:**
> jrg010381; My bad !

In that I failed to follow through, I "assumed" 'net-snmp' was the proper package.
However: 

tells me I am out there in left field, all alone.

Doing:
```

apt-cache search net-snmp

```
tells me the reverse is true.

So what have we ?

let's make sure all of 'snmpd' dependencies are met ;
For each item see what is installed starting as for this example:
```

dpkg -l libc6
dpkg -l libmysqlclient18

```

As I do not have 'snmpd' nor 'mysql' installed, I can not test and verify your results.

we try and find the reason that the package manager[INDENT][INDENT][INDENT]is UNhappy
[/INDENT]
[/INDENT]
[/INDENT]


```

user@:~$ apt-cache search net-snmp
libnet-snmp-perl - Script SNMP connections
libsnmp-base - SNMP configuration script, MIBs and documentation
libsnmp-dev - SNMP (Simple Network Management Protocol) development files
libsnmp30 - SNMP (Simple Network Management Protocol) library
libsnmp30-dbg - SNMP (Simple Network Management Protocol) library debug
snmp - SNMP (Simple Network Management Protocol) applications
snmpd - SNMP (Simple Network Management Protocol) agents
libgsnmp0 - SNMP library implementation based on glib and gnet
libgsnmp0-dbg - SNMP library implementation based on glib and gnet (debug files)
libgsnmp0-dev - SNMP library implementation based on glib and gnet (development files)
libsnmp-extension-passpersist-perl - Generic pass/pass_persist extension framework for Net-SNMP
libsnmp-perl - SNMP (Simple Network Management Protocol) Perl5 support
python-netsnmp - SNMP (Simple Network Management Protocol) Python support
python-pynetsnmp - Python ctypes bindings for NET-SNMP with Twisted integration
ruby-snmp - simple network management protocol bindings for ruby
snmptt - SNMP trap handler for use with snmptrapd
tkmib - SNMP (Simple Network Management Protocol) MIB browser



user@:~$ dpkg -l libc6
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                 Version                         Architecture                    Description
+++-====================================================-===============================-===============================-==============================================================================================================
ii  libc6:amd64                                          2.19-0ubuntu6.6                 amd64                           Embedded GNU C Library: Shared libraries
ii  libc6:i386                                           2.19-0ubuntu6.6                 i386                            Embedded GNU C Library: Shared libraries


user@:~$ dpkg -l libmysqlclient18
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                 Version                         Architecture                    Description
+++-====================================================-===============================-===============================-==============================================================================================================
ii  libmysqlclient18:amd64                               5.5.44-0ubuntu0.14.04.1         amd64                           MySQL database client library

```

---

### Post by Bashing-om on 2015-07-30
jrg010381; Hey;

@ ian-weisser; :) So pleased to have your insight into this matter . 

So far so good, but we do not know that state of the remainder of the dependencies.
This last however:
> 
 snmpd: error while loading shared libraries: libperl.so.5.14: cannot open shared object file:

makes me question if there is a broken symbolic link.
What also returns from terminal command:
```

ls -al /usr/lib/libperl.so.5.14

```
And does the file exist that the link points to ?

[INDENT][INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT][/INDENT]

---

### Post by jrg010381 on 2015-07-30
```
user@:~$ ls -al /usr/lib/libperl.so.5.14
ls: cannot access /usr/lib/libperl.so.5.14: No such file or directory
```

I did find the following though:
```
user@:~$ ls -al /usr/lib/ | grep libp
lrwxrwxrwx   1 root root           26 Sep 30  2014 libpanel-applet-4.so.0 -> libpanel-applet-4.so.0.1.1
-rw-r--r--   1 root root        69656 Sep 30  2014 libpanel-applet-4.so.0.1.1
lrwxrwxrwx   1 root root           20 Dec  4  2014 libpathplan.so.4 -> libpathplan.so.4.0.0
-rw-r--r--   1 root root        30840 Dec  4  2014 libpathplan.so.4.0.0
drwxr-xr-x   3 root root         4096 Jan  7  2013 libpeas-1.0
lrwxrwxrwx   1 root root           22 Feb 19  2014 libpeas-1.0.so.0 -> libpeas-1.0.so.0.801.0
-rw-r--r--   1 root root        81440 Feb 19  2014 libpeas-1.0.so.0.801.0
lrwxrwxrwx   1 root root           26 Feb 19  2014 libpeas-gtk-1.0.so.0 -> libpeas-gtk-1.0.so.0.801.0
-rw-r--r--   1 root root        56944 Feb 19  2014 libpeas-gtk-1.0.so.0.801.0
-rw-r--r--   1 root root     13112294 Mar 27  2014 libperl.a
lrwxrwxrwx   1 root root           15 Mar 27  2014 libperl.so -> libperl.so.5.18
lrwxrwxrwx   1 root root           17 Mar 27  2014 libperl.so.5.18 -> libperl.so.5.18.2
-rw-r--r--   1 root root      1608280 Mar 27  2014 libperl.so.5.18.2



```

Why does snmpd still want [COLOR=#000000]* libperl.so.5.14???*[/COLOR]

---

### Post by Bashing-om on 2015-07-30
jrg010381; OK !

I have an inkling of what is going on here.
If you look at the source packaging:
[http://packages.ubuntu.com/search?searchon=contents&keywords=libperl.so.5.14&mode=exactfilename&suite=precise-updates&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libperl.so.5.14&mode=exactfilename&suite=precise-updates&arch=any)
That version is for 'precise'

So we look at the sources, and lo and behold:
> 
==> /etc/apt/sources.list.d/webupd8team-java-precise.list.distUpgrade <==
deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main

We have a 'precise' source for a 'trusty' install !

webupd8team does support 'trusty', so the 1st thing is to update all sources to trusty.
Now see what results:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install

```

Maybe we will not have to manage this situation manually (?).

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by jrg010381 on 2015-07-30
I commented out the webupd8team entries from [COLOR=#000000]*/etc/apt/sources.list.d/webupd8team-java-precise.list.distUpgrade then did the following:*[/COLOR]

```

user@:~$ sudo apt-get update ; sudo apt-get upgrade
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://us.archive.ubuntu.com trusty-updates InRelease
Ign http://us.archive.ubuntu.com trusty-backports InRelease
Ign http://security.ubuntu.com trusty-security InRelease
Hit http://us.archive.ubuntu.com trusty Release.gpg
Hit http://us.archive.ubuntu.com trusty-updates Release.gpg
Hit http://security.ubuntu.com trusty-security Release.gpg
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg
Hit http://us.archive.ubuntu.com trusty Release
Hit http://security.ubuntu.com trusty-security Release
Hit http://us.archive.ubuntu.com trusty-updates Release
Hit http://us.archive.ubuntu.com trusty-backports Release
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://security.ubuntu.com trusty-security/main Sources
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://security.ubuntu.com trusty-security/restricted Sources
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://security.ubuntu.com trusty-security/universe Sources
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://security.ubuntu.com trusty-security/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://security.ubuntu.com trusty-security/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/main Sources
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/main Sources
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

user@:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

user@:~$ sudo apt-get install snmpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  snmpd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/73.3 kB of archives.
After this operation, 232 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package snmpd.
(Reading database ... 179782 files and directories currently installed.)
Preparing to unpack .../snmpd_5.7.2~dfsg-8.1ubuntu3_amd64.deb ...
Unpacking snmpd (5.7.2~dfsg-8.1ubuntu3) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up snmpd (5.7.2~dfsg-8.1ubuntu3) ...
update-rc.d: warning:  stop runlevel arguments (1) do not match snmpd Default-Stop values (0 1 6)
 * Starting network management services:                                                                                                                                                                                                  /usr/sbin/snmpd: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
invoke-rc.d: initscript snmpd, action "start" failed.
dpkg: error processing package snmpd (--configure):
 subprocess installed post-installation script returned error exit status 127
Processing triggers for ureadahead (0.100.0-16) ...
Errors were encountered while processing:
 snmpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2015-07-30
jrg010381; Well ...

Progress.

What is it going to hurt if we purge snmpd ?
As the error indicates a problem with a config file (upstart). As I do not have snmpd installed I can not look at what might be;
Maybe by purging, and then (RE-)installing the config issue will be resolved ??

I can accept that there is a much cleaner way to handle this; addressing the actual root of the configuration, but !


[INDENT][INDENT]poor folks
[INDENT][INDENT][INDENT]have poor ways
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jrg010381 on 2015-07-31
I did run apt-get purge snmpd. For some reason, I can still attempt to run snmpd, but it never runs.

---

### Post by Bashing-om on 2015-07-31
jrg010381; Humm ......

Recon that snmpd is running ? Such that as the app is in use, the system can not remove it .
What returns:
```

ps aux | grep snmpd
dpkg -l snmpd

```

We are in that process of learning.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by jrg010381 on 2015-08-01
Thanks again for your help! 

```

user@:~$ ps aux | grep snmpd
user 11055  0.0  0.1  10468  2164 pts/12   S+   20:32   0:00 grep --color=auto snmpd
user@:~$ dpkg -l snmpd
dpkg-query: no packages found matching snmpd
```

So clearly it is not running or installed. However, when I tab complete snmp, snmpd shows up...```

user@:~$ snmp
snmp-bridge-mib  snmpconf         snmpget          snmpnetstat      snmptest         snmpusm
snmpbulkget      snmpd            snmpgetnext      snmpset          snmptranslate    snmpvacm
snmpbulkwalk     snmpdelta        snmpinform       snmpstatus       snmptrap         snmpwalk
snmpcheck        snmpdf           snmpkey          snmptable        snmptrapd        
user@:~$ snmp

```

I have found that snmpd int /usr/sbin/, but what is it??

```

user@:~$ ls -al /usr/local/sbin/
total 124
drwxr-xr-x  2 root root  4096 Mar 26  2014 .
drwxr-xr-x 13 root root  4096 Jan  8  2014 ..
-rwxr-xr-x  1 root root 55950 Mar 26  2014 snmpd
-rwxr-xr-x  1 root root 61118 Mar 26  2014 snmptrapd

```

---

### Post by Bashing-om on 2015-08-01
jrg010381; Wellllll ,,

Got me scratching my head wondering what is going on .

What do the control files yield ?
```

ls -al /var/lib/dpkg/info/snmpd.list
grep -B3 -A10 snmpd /var/lib/dpkg/status

```

If there is anything there, we may get a hint of what we need to do.

[INDENT][INDENT]sometimes I do wonder
[INDENT][INDENT][INDENT][INDENT]othertimes, I just do not know[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jrg010381 on 2015-08-02
Not sure of any hints to give. 

```

user@:~$ ls -al /var/lib/dpkg/info/snmpd.list
-rw-r--r-- 1 root root 1545 Aug  1 20:42 /var/lib/dpkg/info/snmpd.list
user@:~$ grep -B3 -A10 snmpd /var/lib/dpkg/status
Homepage: http://net-snmp.sourceforge.net/
Original-Maintainer: Net-SNMP Packaging Team <pkg-net-snmp-devel@lists.alioth.debian.org>


Package: snmpd
Status: install ok half-configured
Priority: optional
Section: net
Installed-Size: 227
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: net-snmp
Version: 5.7.2~dfsg-8.1ubuntu3
Depends: libc6 (>= 2.4), libmysqlclient18 (>= 5.5.24+dfsg-1), libsnmp30 (>= 5.7.2~dfsg), libwrap0 (>= 7.6-4~), debconf (>= 0.5) | debconf-2.0, adduser, debconf, lsb-base (>= 3.2-13), libsnmp-base
Conffiles:
 /etc/snmp/snmptrapd.conf a2ee110581a5a9a1e2252400cb176bcc
 /etc/snmp/snmpd.conf 0bcc67e56996b3d9ce197a1776266856
 /etc/init.d/snmpd be9d2bb34e6fde7ccf09289905cb2cee
 /etc/default/snmpd 1ced835b933ffebc2d5176a1b5e248f7
Description: SNMP (Simple Network Management Protocol) agents
 The Simple Network Management Protocol (SNMP) provides a framework
 for the exchange of management information between agents (servers)
 and clients.
 .
 The Net-SNMP agent is a daemon which listens for incoming SNMP
 requests from clients and provides responses.
Homepage: http://net-snmp.sourceforge.net/
Original-Maintainer: Net-SNMP Packaging Team <pkg-net-snmp-devel@lists.alioth.debian.org>

```

---

### Post by Bashing-om on 2015-08-02
jrg010381; Welp'

The package manager thinks snmpd is still on the system,
As we have :
> 
Status: install ok half-configured

Let's see if the package manager will complete the configuration.
```

sudo dpkg-reconfigure snmpd 

```
We have to get the package in a consistent state, to either purge it or complete the installation. We are working to getting that package in a condition we can work with it. Let's find out what that will take.

[INDENT][INDENT]that is what I think
[/INDENT][/INDENT]

---

### Post by jrg010381 on 2015-08-04
Is there a package of snmpd that needs to be purged elsewhere?

```
user@:~$ sudo dpkg-reconfigure snmpd


/usr/sbin/dpkg-reconfigure: snmpd is broken or not fully installed
user@:~$ sudo apt-get purge snmpd


Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  snmpd*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 232 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 179813 files and directories currently installed.)
Removing snmpd (5.7.2~dfsg-8.1ubuntu3) ...
 * Stopping network management services:                                                                                                                                                                                                  Purging configuration files for snmpd (5.7.2~dfsg-8.1ubuntu3) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...

```

---

### Post by Bashing-om on 2015-08-04
jrg010381; ouch !

> 
 * Stopping network management services:


Do you still have internet connectivity ?
Did the package snmpd get removed ?

If we have internet:
what returns:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg -C

```

[INDENT][INDENT]just goes to show
[INDENT][INDENT][INDENT]look 1st before the leap
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jrg010381 on 2015-08-06
Yep, there is internet connectivity to this system. 
Thanks again for your patience and help!!

As you see, snmpd is not installed:
```

user@:~$ dpkg --get-selections | grep sn
libasn1-8-heimdal:amd64                         install
libasn1-8-heimdal:i386                          deinstall
libnet-snmp-perl                                install
libsndfile1:amd64                               install
libsndfile1:i386                                deinstall
libsnmp-base                                    install
libsnmp-info-perl                               install
libsnmp-perl                                    install
libsnmp15                                       deinstall
libsnmp30:amd64                                 install
libtasn1-3:amd64                                deinstall
libtasn1-3:i386                                 deinstall
libtasn1-6:amd64                                install
libtasn1-6:i386                                 deinstall
php5-snmp                                       install
sni-qt:amd64                                    install

```



```

user@:~$ sudo apt-get update
[sudo] password for user:
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://us.archive.ubuntu.com trusty InRelease
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Ign http://us.archive.ubuntu.com trusty-updates InRelease
Get:2 http://security.ubuntu.com trusty-security Release [63.5 kB]
Ign http://us.archive.ubuntu.com trusty-backports InRelease
Hit http://us.archive.ubuntu.com trusty Release.gpg
Get:3 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg
Hit http://us.archive.ubuntu.com trusty Release
Get:4 http://security.ubuntu.com trusty-security/main Sources [91.1 kB]
Get:5 http://us.archive.ubuntu.com trusty-updates Release [63.5 kB]
Get:6 http://security.ubuntu.com trusty-security/restricted Sources [2,061 B]
Hit http://us.archive.ubuntu.com trusty-backports Release
Get:7 http://security.ubuntu.com trusty-security/universe Sources [28.5 kB]
Hit http://us.archive.ubuntu.com trusty/main Sources
Get:8 http://security.ubuntu.com trusty-security/multiverse Sources [2,334 B]
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Get:9 http://security.ubuntu.com trusty-security/main amd64 Packages [326 kB]
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Get:10 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Get:11 http://security.ubuntu.com trusty-security/universe amd64 Packages [112 kB]
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Get:12 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,683 B]
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Get:13 http://security.ubuntu.com trusty-security/main i386 Packages [312 kB]
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Get:14 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]
Get:15 http://security.ubuntu.com trusty-security/universe i386 Packages [112 kB]
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Get:16 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,838 B]
Get:17 http://us.archive.ubuntu.com trusty-updates/main Sources [228 kB]
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Get:18 http://us.archive.ubuntu.com trusty-updates/restricted Sources [4,717 B]
Get:19 http://us.archive.ubuntu.com trusty-updates/universe Sources [130 kB]
Get:20 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,138 B]
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Get:21 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [599 kB]
Get:22 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.4 kB]
Get:23 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [301 kB]
Get:24 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:25 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [579 kB]
Get:26 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.2 kB]
Get:27 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [303 kB]
Get:28 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/main Sources
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Fetched 3,345 kB in 4s (768 kB/s)
Reading package lists... Done


user@:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  base-files bsdutils libblkid1 libmount1 libunity-control-center1 libuuid1
  libuuid1:i386 mount nvidia-common ubuntu-drivers-common unity-control-center
  unity-settings-daemon util-linux uuid-runtime
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,169 kB of archives.
After this operation, 7,168 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main base-files amd64 7.2ubuntu5.3 [60.9 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main mount amd64 2.20.1-5.1ubuntu20.6 [114 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main util-linux amd64 2.20.1-5.1ubuntu20.6 [458 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main bsdutils amd64 1:2.20.1-5.1ubuntu20.6 [33.8 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libuuid1 i386 2.20.1-5.1ubuntu20.6 [11.4 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libuuid1 amd64 2.20.1-5.1ubuntu20.6 [10.9 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libblkid1 amd64 2.20.1-5.1ubuntu20.6 [62.5 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libmount1 amd64 2.20.1-5.1ubuntu20.6 [60.2 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main ubuntu-drivers-common amd64 1:0.2.91.11 [46.0 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main uuid-runtime amd64 2.20.1-5.1ubuntu20.6 [12.3 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libunity-control-center1 amd64 14.04.3+14.04.20140922-0ubuntu1.1 [80.9 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe nvidia-common amd64 1:0.2.91.11 [1,298 B]
Get:13 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main unity-settings-daemon amd64 14.04.0+14.04.20140606-0ubuntu3 [489 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main unity-control-center amd64 14.04.3+14.04.20140922-0ubuntu1.1 [727 kB]
Fetched 2,169 kB in 1s (2,041 kB/s)
Preconfiguring packages ...
(Reading database ... 179782 files and directories currently installed.)
Preparing to unpack .../base-files_7.2ubuntu5.3_amd64.deb ...
Unpacking base-files (7.2ubuntu5.3) over (7.2ubuntu5.2) ...
Processing triggers for cracklib-runtime (2.9.1-1build1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for plymouth-theme-ubuntu-text (0.8.8-0ubuntu17.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-45-generic
Setting up base-files (7.2ubuntu5.3) ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...
Installing new version of config file /etc/os-release ...
Processing triggers for plymouth-theme-ubuntu-text (0.8.8-0ubuntu17.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-45-generic
(Reading database ... 179782 files and directories currently installed.)
Preparing to unpack .../mount_2.20.1-5.1ubuntu20.6_amd64.deb ...
Unpacking mount (2.20.1-5.1ubuntu20.6) over (2.20.1-5.1ubuntu20.4) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up mount (2.20.1-5.1ubuntu20.6) ...
(Reading database ... 179782 files and directories currently installed.)
Preparing to unpack .../util-linux_2.20.1-5.1ubuntu20.6_amd64.deb ...
Unpacking util-linux (2.20.1-5.1ubuntu20.6) over (2.20.1-5.1ubuntu20.4) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up util-linux (2.20.1-5.1ubuntu20.6) ...
(Reading database ... 179782 files and directories currently installed.)
Preparing to unpack .../bsdutils_1%3a2.20.1-5.1ubuntu20.6_amd64.deb ...
Unpacking bsdutils (1:2.20.1-5.1ubuntu20.6) over (1:2.20.1-5.1ubuntu20.4) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up bsdutils (1:2.20.1-5.1ubuntu20.6) ...
(Reading database ... 179782 files and directories currently installed.)
Preparing to unpack .../libuuid1_2.20.1-5.1ubuntu20.6_amd64.deb ...
De-configuring libuuid1:i386 (2.20.1-5.1ubuntu20.4) ...
Unpacking libuuid1:amd64 (2.20.1-5.1ubuntu20.6) over (2.20.1-5.1ubuntu20.4) ...
Preparing to unpack .../libuuid1_2.20.1-5.1ubuntu20.6_i386.deb ...
Unpacking libuuid1:i386 (2.20.1-5.1ubuntu20.6) over (2.20.1-5.1ubuntu20.4) ...
Preparing to unpack .../libblkid1_2.20.1-5.1ubuntu20.6_amd64.deb ...
Unpacking libblkid1:amd64 (2.20.1-5.1ubuntu20.6) over (2.20.1-5.1ubuntu20.4) ...
Setting up libuuid1:amd64 (2.20.1-5.1ubuntu20.6) ...
Setting up libuuid1:i386 (2.20.1-5.1ubuntu20.6) ...
Setting up libblkid1:amd64 (2.20.1-5.1ubuntu20.6) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
(Reading database ... 179782 files and directories currently installed.)
Preparing to unpack .../libmount1_2.20.1-5.1ubuntu20.6_amd64.deb ...
Unpacking libmount1:amd64 (2.20.1-5.1ubuntu20.6) over (2.20.1-5.1ubuntu20.4) ...
Setting up libmount1:amd64 (2.20.1-5.1ubuntu20.6) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
(Reading database ... 179782 files and directories currently installed.)
Preparing to unpack .../ubuntu-drivers-common_1%3a0.2.91.11_amd64.deb ...
Unpacking ubuntu-drivers-common (1:0.2.91.11) over (1:0.2.91.9) ...
Preparing to unpack .../uuid-runtime_2.20.1-5.1ubuntu20.6_amd64.deb ...
Unpacking uuid-runtime (2.20.1-5.1ubuntu20.6) over (2.20.1-5.1ubuntu20.4) ...
Preparing to unpack .../libunity-control-center1_14.04.3+14.04.20140922-0ubuntu1.1_amd64.deb ...
Unpacking libunity-control-center1 (14.04.3+14.04.20140922-0ubuntu1.1) over (14.04.3+14.04.20140922-0ubuntu1) ...
Preparing to unpack .../nvidia-common_1%3a0.2.91.11_amd64.deb ...
Unpacking nvidia-common (1:0.2.91.11) over (1:0.2.91.9) ...
Preparing to unpack .../unity-settings-daemon_14.04.0+14.04.20140606-0ubuntu3_amd64.deb ...
Unpacking unity-settings-daemon (14.04.0+14.04.20140606-0ubuntu3) over (14.04.0+14.04.20140606-0ubuntu2) ...
Preparing to unpack .../unity-control-center_14.04.3+14.04.20140922-0ubuntu1.1_amd64.deb ...
Unpacking unity-control-center (14.04.3+14.04.20140922-0ubuntu1.1) over (14.04.3+14.04.20140922-0ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Setting up ubuntu-drivers-common (1:0.2.91.11) ...
Setting up uuid-runtime (2.20.1-5.1ubuntu20.6) ...
Setting up libunity-control-center1 (14.04.3+14.04.20140922-0ubuntu1.1) ...
Setting up nvidia-common (1:0.2.91.11) ...
Setting up unity-settings-daemon (14.04.0+14.04.20140606-0ubuntu3) ...
Setting up unity-control-center (14.04.3+14.04.20140922-0ubuntu1.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...


user@:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


user@:~$ sudo dpkg -C
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 libjson0:amd64       JSON manipulation library (transitional package)
 libjson0:i386        JSON manipulation library (transitional package)

```

---

### Post by Bashing-om on 2015-08-06
jrg010381; Well ...

All looking pretty good. over all.
I have to question the need of the 32 bit libraries ( :i386 ) on the system.

The only adverse condition reported:
> 
user@:~$ sudo dpkg -C
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 libjson0:amd64       JSON manipulation library (transitional package)
 libjson0:i386        JSON manipulation library (transitional package)


How about we clean up the system, then see if we still need to address the 32 bit libraries:
```

sudo apt-get clean
apt-get autoclean
apt-get autoremove

```
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed but not yet purged package.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

Once these are done, get a new look :
```

sudp apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg -C

```

Then we can test to see what results in installing an application.

[INDENT][INDENT]prospects are good
[/INDENT][/INDENT]

---

### Post by jrg010381 on 2015-08-06
```

root@:~# 
root@:~# 
root@:~# apt-get clean


root@:~# apt-gt-get autoclean


Reading package lists... 0%


Reading package lists... 0%


Reading package lists... 1%


Reading package lists... 6%


Reading package lists... 6%


Reading package lists... 6%


Reading package lists... 6%


Reading package lists... 19%


Reading package lists... 30%


Reading package lists... 30%


Reading package lists... 30%


Reading package lists... 30%


Reading package lists... 37%


Reading package lists... 37%


Reading package lists... 37%


Reading package lists... 37%


Reading package lists... 44%


Reading package lists... 61%


Reading package lists... 61%


Reading package lists... 61%


Reading package lists... 61%


Reading package lists... 65%


Reading package lists... 65%


Reading package lists... 65%


Reading package lists... 65%


Reading package lists... 65%


Reading package lists... 65%


Reading package lists... 77%


Reading package lists... 79%


Reading package lists... 79%


Reading package lists... 82%


Reading package lists... 82%


Reading package lists... 82%


Reading package lists... 82%


Reading package lists... 84%


Reading package lists... 84%


Reading package lists... 84%


Reading package lists... 84%


Reading package lists... 86%


Reading package lists... 86%


Reading package lists... 87%


Reading package lists... 87%


Reading package lists... 88%


Reading package lists... 88%


Reading package lists... 88%


Reading package lists... 88%


Reading package lists... 90%


Reading package lists... 90%


Reading package lists... 90%


Reading package lists... 90%


Reading package lists... 90%


Reading package lists... 90%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 93%


Reading package lists... 93%


Reading package lists... 93%


Reading package lists... 93%


Reading package lists... 94%


Reading package lists... 94%


Reading package lists... 94%


Reading package lists... 94%


Reading package lists... 95%


Reading package lists... 95%


Reading package lists... 95%


Reading package lists... 95%


Reading package lists... 96%


Reading package lists... 96%


Reading package lists... 96%


Reading package lists... 96%


Reading package lists... 97%


Reading package lists... 97%


Reading package lists... 97%


Reading package lists... 97%


Reading package lists... 97%


Reading package lists... 97%


Reading package lists... 98%


Reading package lists... 98%


Reading package lists... 99%


Reading package lists... Done




Building dependency tree... 0%


Building dependency tree... 0%


Building dependency tree... 50%


Building dependency tree... 50%


Building dependency tree       




Reading state information... 0%


Reading state information... 0%


Reading state information... Done


root@:~# apt-get autoremove


Reading package lists... 0%


Reading package lists... 100%


Reading package lists... Done




Building dependency tree... 0%


Building dependency tree... 0%


Building dependency tree... 50%


Building dependency tree... 50%


Building dependency tree       




Reading state information... 0%


Reading state information... 0%


Reading state information... Done

dpkg --list | grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
(Reading database ... 
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
(Reading database ... 179781 files and directories currently installed.)
Removing account-plugin-identica (0.11+14.04.20140409.1-0ubuntu1) ...
Purging configuration files for account-plugin-identica (0.11+14.04.20140409.1-0ubuntu1) ...
Removing account-plugin-windows-live (0.11+14.04.20140409.1-0ubuntu2) ...
Purging configuration files for account-plugin-windows-live (0.11+14.04.20140409.1-0ubuntu2) ...
Removing apache2.2-common (2.2.22-1ubuntu1.7) ...
Purging configuration files for apache2.2-common (2.2.22-1ubuntu1.7) ...
dpkg: warning: while removing apache2.2-common, directory '/etc/apache2/conf.d' not empty so not removed
Removing appmenu-gtk:amd64 (0.3.92-0ubuntu1.1) ...
Purging configuration files for appmenu-gtk:amd64 (0.3.92-0ubuntu1.1) ...
Removing appmenu-gtk3:amd64 (0.3.92-0ubuntu1.1) ...
Purging configuration files for appmenu-gtk3:amd64 (0.3.92-0ubuntu1.1) ...
Removing checkbox (0.17.6-0ubuntu6) ...
Purging configuration files for checkbox (0.17.6-0ubuntu6) ...
Removing consolekit (0.4.5-3.1ubuntu2) ...
Purging configuration files for consolekit (0.4.5-3.1ubuntu2) ...
dpkg: warning: while removing consolekit, directory '/var/log/ConsoleKit' not empty so not removed
Removing defoma (0.11.12ubuntu1) ...
Purging configuration files for defoma (0.11.12ubuntu1) ...
Removing esound-common (0.2.41-11) ...
Purging configuration files for esound-common (0.2.41-11) ...
Removing foomatic-filters (4.0.16-0ubuntu0.2) ...
Purging configuration files for foomatic-filters (4.0.16-0ubuntu0.2) ...
Removing gksu (2.0.2-6ubuntu2) ...
Purging configuration files for gksu (2.0.2-6ubuntu2) ...
Removing gstreamer0.10-plugins-good:i386 (0.10.31-3+nmu1ubuntu5) ...
Purging configuration files for gstreamer0.10-plugins-good:i386 (0.10.31-3+nmu1ubuntu5) ...
Removing guile-1.8-libs (1.8.8+1-8ubuntu3) ...
Purging configuration files for guile-1.8-libs (1.8.8+1-8ubuntu3) ...
Removing gwibber (3.4.2-0ubuntu2.4) ...
Purging configuration files for gwibber (3.4.2-0ubuntu2.4) ...
Removing im-switch (1.20ubuntu5.2) ...
Purging configuration files for im-switch (1.20ubuntu5.2) ...
dpkg: warning: while removing im-switch, directory '/etc/X11/xinit/xinput.d' not empty so not removed
Removing imagemagick-common (8:6.7.7.10-6ubuntu3) ...
Purging configuration files for imagemagick-common (8:6.7.7.10-6ubuntu3) ...
Removing jockey-common (0.9.7-0ubuntu7.14) ...
Purging configuration files for jockey-common (0.9.7-0ubuntu7.14) ...
Removing jockey-gtk (0.9.7-0ubuntu7.14) ...
Purging configuration files for jockey-gtk (0.9.7-0ubuntu7.14) ...
Removing lib32asound2 (1.0.25-1ubuntu10.2) ...
Purging configuration files for lib32asound2 (1.0.25-1ubuntu10.2) ...
Removing libaa1:i386 (1.4p5-41) ...
Purging configuration files for libaa1:i386 (1.4p5-41) ...
Removing libaio1:i386 (0.3.109-4) ...
Purging configuration files for libaio1:i386 (0.3.109-4) ...
Removing libao-common (1.1.0-2ubuntu2) ...
Purging configuration files for libao-common (1.1.0-2ubuntu2) ...
Removing libao4:i386 (1.1.0-2ubuntu2) ...
Purging configuration files for libao4:i386 (1.1.0-2ubuntu2) ...
Removing libappindicator1 (12.10.1+13.10.20130920-0ubuntu4.1) ...
Purging configuration files for libappindicator1 (12.10.1+13.10.20130920-0ubuntu4.1) ...
Removing libapreq2 (2.13-1build2) ...
Purging configuration files for libapreq2 (2.13-1build2) ...
Removing libapt-inst1.4:amd64 (0.8.16~exp12ubuntu10.22) ...
Purging configuration files for libapt-inst1.4:amd64 (0.8.16~exp12ubuntu10.22) ...
Removing libarchive12:amd64 (3.0.3-6ubuntu1) ...
Purging configuration files for libarchive12:amd64 (3.0.3-6ubuntu1) ...
Removing libasn1-8-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Purging configuration files for libasn1-8-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Removing libasound2:i386 (1.0.27.2-3ubuntu7) ...
Purging configuration files for libasound2:i386 (1.0.27.2-3ubuntu7) ...
Removing libasyncns0:i386 (0.8-4ubuntu2) ...
Purging configuration files for libasyncns0:i386 (0.8-4ubuntu2) ...
Removing libatk1.0-0:i386 (2.10.0-2ubuntu2) ...
Purging configuration files for libatk1.0-0:i386 (2.10.0-2ubuntu2) ...
Removing libaudiofile1:i386 (0.3.6-2) ...
Purging configuration files for libaudiofile1:i386 (0.3.6-2) ...
Removing libavahi-client3:i386 (0.6.31-4ubuntu1) ...
Purging configuration files for libavahi-client3:i386 (0.6.31-4ubuntu1) ...
Removing libavahi-common3:i386 (0.6.31-4ubuntu1) ...
Purging configuration files for libavahi-common3:i386 (0.6.31-4ubuntu1) ...
Removing libavahi-ui-gtk3-0:amd64 (0.6.31-4ubuntu1) ...
Purging configuration files for libavahi-ui-gtk3-0:amd64 (0.6.31-4ubuntu1) ...
Removing libavc1394-0:i386 (0.5.4-2) ...
Purging configuration files for libavc1394-0:i386 (0.5.4-2) ...
Removing libbamf0:amd64 (0.2.126-0ubuntu1) ...
Purging configuration files for libbamf0:amd64 (0.2.126-0ubuntu1) ...
Removing libbamf3-0:amd64 (0.2.126-0ubuntu1) ...
Purging configuration files for libbamf3-0:amd64 (0.2.126-0ubuntu1) ...
Removing libbind9-80 (1:9.8.1.dfsg.P1-4ubuntu0.9) ...
Purging configuration files for libbind9-80 (1:9.8.1.dfsg.P1-4ubuntu0.9) ...
Removing libboost-iostreams1.46.1 (1.46.1-7ubuntu3) ...
Purging configuration files for libboost-iostreams1.46.1 (1.46.1-7ubuntu3) ...
Removing libboost-serialization1.46.1 (1.46.1-7ubuntu3) ...
Purging configuration files for libboost-serialization1.46.1 (1.46.1-7ubuntu3) ...
Removing libbrlapi0.5 (4.3-1ubuntu5) ...
Purging configuration files for libbrlapi0.5 (4.3-1ubuntu5) ...
Removing libc-ares2:amd64 (1.10.0-2) ...
Purging configuration files for libc-ares2:amd64 (1.10.0-2) ...
Removing libc6-i386 (2.19-0ubuntu6.5) ...
Purging configuration files for libc6-i386 (2.19-0ubuntu6.5) ...
Removing libcaca0:i386 (0.99.beta18-1ubuntu5) ...
Purging configuration files for libcaca0:i386 (0.99.beta18-1ubuntu5) ...
Removing libcairo-gobject2:i386 (1.13.0~20140204-0ubuntu1.1) ...
Purging configuration files for libcairo-gobject2:i386 (1.13.0~20140204-0ubuntu1.1) ...
Removing libcairo2:i386 (1.13.0~20140204-0ubuntu1.1) ...
Purging configuration files for libcairo2:i386 (1.13.0~20140204-0ubuntu1.1) ...
Removing libcamel-1.2-29 (3.2.3-0ubuntu7.2) ...
Purging configuration files for libcamel-1.2-29 (3.2.3-0ubuntu7.2) ...
Removing libcanberra-gtk0:i386 (0.30-0ubuntu3) ...
Purging configuration files for libcanberra-gtk0:i386 (0.30-0ubuntu3) ...
Removing libcanberra0:i386 (0.30-0ubuntu3) ...
Purging configuration files for libcanberra0:i386 (0.30-0ubuntu3) ...
Removing libcapi20-3:i386 (1:3.25+dfsg1-3.3ubuntu2) ...
Purging configuration files for libcapi20-3:i386 (1:3.25+dfsg1-3.3ubuntu2) ...
Removing libcdparanoia0:i386 (3.10.2+debian-11) ...
Purging configuration files for libcdparanoia0:i386 (3.10.2+debian-11) ...
Removing libcdt4 (2.26.3-10ubuntu1.2) ...
Purging configuration files for libcdt4 (2.26.3-10ubuntu1.2) ...
Removing libcgraph5 (2.26.3-10ubuntu1.2) ...
Purging configuration files for libcgraph5 (2.26.3-10ubuntu1.2) ...
Removing libcmis-0.2-0 (0.1.0-1) ...
Purging configuration files for libcmis-0.2-0 (0.1.0-1) ...
Removing libcroco3:i386 (0.6.8-2ubuntu1) ...
Purging configuration files for libcroco3:i386 (0.6.8-2ubuntu1) ...
Removing libcups2:i386 (1.7.2-0ubuntu1.2) ...
Purging configuration files for libcups2:i386 (1.7.2-0ubuntu1.2) ...
Removing libcupsdriver1:amd64 (1.5.3-0ubuntu8.5) ...
Purging configuration files for libcupsdriver1:amd64 (1.5.3-0ubuntu8.5) ...
Removing libcupsfilters1:i386 (1.0.52-0ubuntu1.2) ...
Purging configuration files for libcupsfilters1:i386 (1.0.52-0ubuntu1.2) ...
Removing libcupsimage2:i386 (1.7.2-0ubuntu1.2) ...
Purging configuration files for libcupsimage2:i386 (1.7.2-0ubuntu1.2) ...
Removing libcurl3:i386 (7.35.0-1ubuntu2.3) ...
Purging configuration files for libcurl3:i386 (7.35.0-1ubuntu2.3) ...
Removing libcurl3-nss:amd64 (7.35.0-1ubuntu2.3) ...
Purging configuration files for libcurl3-nss:amd64 (7.35.0-1ubuntu2.3) ...
Removing libdatrie1:i386 (0.2.8-1) ...
Purging configuration files for libdatrie1:i386 (0.2.8-1) ...
Removing libdb5.1:i386 (5.1.29-7ubuntu1) ...
Purging configuration files for libdb5.1:i386 (5.1.29-7ubuntu1) ...
Removing libdbus-glib-1-2:i386 (0.100.2-1) ...
Purging configuration files for libdbus-glib-1-2:i386 (0.100.2-1) ...
Removing libdconf-dbus-1-0:amd64 (0.20.0-1) ...
Purging configuration files for libdconf-dbus-1-0:amd64 (0.20.0-1) ...
Removing libdconf-qt0 (0.0.0.110722-0ubuntu4) ...
Purging configuration files for libdconf-qt0 (0.0.0.110722-0ubuntu4) ...
Removing libdconf0:amd64 (0.12.0-0ubuntu1.1) ...
Purging configuration files for libdconf0:amd64 (0.12.0-0ubuntu1.1) ...
Removing libdee-qt5-3:amd64 (3.3+14.04.20140317-0ubuntu1) ...
Purging configuration files for libdee-qt5-3:amd64 (3.3+14.04.20140317-0ubuntu1) ...
Removing libdiscid0:amd64 (0.6.1-2) ...
Purging configuration files for libdiscid0:amd64 (0.6.1-2) ...
Removing libdns81 (1:9.8.1.dfsg.P1-4ubuntu0.9) ...
Purging configuration files for libdns81 (1:9.8.1.dfsg.P1-4ubuntu0.9) ...
Removing libdotconf1.0 (1.0.13-3) ...
Purging configuration files for libdotconf1.0 (1.0.13-3) ...
Removing libdrm-nouveau1a:amd64 (2.4.52-1~precise2) ...
Purging configuration files for libdrm-nouveau1a:amd64 (2.4.52-1~precise2) ...
Removing libdv4:i386 (1.0.0-6) ...
Purging configuration files for libdv4:i386 (1.0.0-6) ...
Removing libebackend-1.2-1 (3.2.3-0ubuntu7.2) ...
Purging configuration files for libebackend-1.2-1 (3.2.3-0ubuntu7.2) ...
Removing libebook-1.2-12 (3.2.3-0ubuntu7.2) ...
Purging configuration files for libebook-1.2-12 (3.2.3-0ubuntu7.2) ...
Removing libecal-1.2-10 (3.2.3-0ubuntu7.2) ...
Purging configuration files for libecal-1.2-10 (3.2.3-0ubuntu7.2) ...
Removing libedata-book-1.2-11 (3.2.3-0ubuntu7.2) ...
Purging configuration files for libedata-book-1.2-11 (3.2.3-0ubuntu7.2) ...
Removing libedata-cal-1.2-13 (3.2.3-0ubuntu7.2) ...
Purging configuration files for libedata-cal-1.2-13 (3.2.3-0ubuntu7.2) ...
Removing libedataserver-1.2-15 (3.2.3-0ubuntu7.2) ...
Purging configuration files for libedataserver-1.2-15 (3.2.3-0ubuntu7.2) ...
Removing libedataserverui-3.0-1 (3.2.3-0ubuntu7.2) ...
Purging configuration files for libedataserverui-3.0-1 (3.2.3-0ubuntu7.2) ...
Removing libesd0:i386 (0.2.41-11) ...
Purging configuration files for libesd0:i386 (0.2.41-11) ...
Removing libevince3-3 (3.4.0-0ubuntu1.8) ...
Purging configuration files for libevince3-3 (3.4.0-0ubuntu1.8) ...
Removing libexif12:i386 (0.6.21-1ubuntu1) ...
Purging configuration files for libexif12:i386 (0.6.21-1ubuntu1) ...
Removing libexiv2-11 (0.22-2) ...
Purging configuration files for libexiv2-11 (0.22-2) ...
Removing libexpat1:i386 (2.1.0-4ubuntu1) ...
Purging configuration files for libexpat1:i386 (2.1.0-4ubuntu1) ...
Removing libexttextcat0 (3.2.0-1ubuntu1) ...
Purging configuration files for libexttextcat0 (3.2.0-1ubuntu1) ...
Removing libffi6:i386 (3.1~rc1+r3.0.13-12) ...
Purging configuration files for libffi6:i386 (3.1~rc1+r3.0.13-12) ...
Removing libflac8:i386 (1.3.0-2ubuntu0.14.04.1) ...
Purging configuration files for libflac8:i386 (1.3.0-2ubuntu0.14.04.1) ...
Removing libfluidsynth1:i386 (1.1.6-2) ...
Purging configuration files for libfluidsynth1:i386 (1.1.6-2) ...
Removing libfontconfig1:i386 (2.11.0-0ubuntu4.1) ...
Purging configuration files for libfontconfig1:i386 (2.11.0-0ubuntu4.1) ...
Removing libfreetype6:i386 (2.5.2-1ubuntu2.2) ...
Purging configuration files for libfreetype6:i386 (2.5.2-1ubuntu2.2) ...
Removing libgail18:i386 (2.24.23-0ubuntu1.1) ...
Purging configuration files for libgail18:i386 (2.24.23-0ubuntu1.1) ...
Removing libgconf-2-4:i386 (3.2.6-0ubuntu2) ...
Purging configuration files for libgconf-2-4:i386 (3.2.6-0ubuntu2) ...
Removing libgcrypt11:i386 (1.5.3-2ubuntu4.1) ...
Purging configuration files for libgcrypt11:i386 (1.5.3-2ubuntu4.1) ...
Removing libgd2-xpm:amd64 (2.0.36~rc1~dfsg-6ubuntu2) ...
Purging configuration files for libgd2-xpm:amd64 (2.0.36~rc1~dfsg-6ubuntu2) ...
Removing libgd2-xpm:i386 (2.0.36~rc1~dfsg-6ubuntu2) ...
Purging configuration files for libgd2-xpm:i386 (2.0.36~rc1~dfsg-6ubuntu2) ...
Removing libgd3:i386 (2.1.0-3) ...
Purging configuration files for libgd3:i386 (2.1.0-3) ...
Removing libgdbm3:i386 (1.8.3-12build1) ...
Purging configuration files for libgdbm3:i386 (1.8.3-12build1) ...
Removing libgdk-pixbuf2.0-0:i386 (2.30.7-0ubuntu1) ...
Purging configuration files for libgdk-pixbuf2.0-0:i386 (2.30.7-0ubuntu1) ...
Removing libgdu-gtk0:amd64 (3.0.2-2ubuntu7) ...
Purging configuration files for libgdu-gtk0:amd64 (3.0.2-2ubuntu7) ...
Removing libgdu0:amd64 (3.0.2-2ubuntu7) ...
Purging configuration files for libgdu0:amd64 (3.0.2-2ubuntu7) ...
Removing libgexiv2-1 (0.4.1-1build1) ...
Purging configuration files for libgexiv2-1 (0.4.1-1build1) ...
Removing libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
Purging configuration files for libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
Removing libgl1-mesa-glx:i386 (10.1.3-0ubuntu0.3) ...
Purging configuration files for libgl1-mesa-glx:i386 (10.1.3-0ubuntu0.3) ...
Removing libglapi-mesa:i386 (10.1.3-0ubuntu0.3) ...
Purging configuration files for libglapi-mesa:i386 (10.1.3-0ubuntu0.3) ...
Removing libglew1.6:amd64 (1.6.0-4) ...
Purging configuration files for libglew1.6:amd64 (1.6.0-4) ...
Removing libglewmx1.6:amd64 (1.6.0-4) ...
Purging configuration files for libglewmx1.6:amd64 (1.6.0-4) ...
Removing libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Purging configuration files for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Removing libglu1-mesa:i386 (9.0.0-2) ...
Purging configuration files for libglu1-mesa:i386 (9.0.0-2) ...
Removing libgnome-bluetooth8 (3.2.2-0ubuntu5.1) ...
Purging configuration files for libgnome-bluetooth8 (3.2.2-0ubuntu5.1) ...
Removing libgnome-desktop-3-2 (3.4.2-0ubuntu0.2) ...
Purging configuration files for libgnome-desktop-3-2 (3.4.2-0ubuntu0.2) ...
Removing libgnome-keyring0:i386 (3.8.0-2) ...
Purging configuration files for libgnome-keyring0:i386 (3.8.0-2) ...
Removing libgnome-menu2 (3.0.1-0ubuntu9) ...
Purging configuration files for libgnome-menu2 (3.0.1-0ubuntu9) ...
Removing libgnome2-common (2.32.1-4ubuntu1) ...
Purging configuration files for libgnome2-common (2.32.1-4ubuntu1) ...
Removing libgnomekbd7 (3.4.0.2-1ubuntu0.1) ...
Purging configuration files for libgnomekbd7 (3.4.0.2-1ubuntu0.1) ...
Removing libgnutls26:i386 (2.12.23-12ubuntu2.1) ...
Purging configuration files for libgnutls26:i386 (2.12.23-12ubuntu2.1) ...
Removing libgoa-1.0-0:amd64 (3.4.0-0ubuntu1.1) ...
Purging configuration files for libgoa-1.0-0:amd64 (3.4.0-0ubuntu1.1) ...
Removing libgomp1:i386 (4.8.2-19ubuntu1) ...
Purging configuration files for libgomp1:i386 (4.8.2-19ubuntu1) ...
Removing libgpg-error0:i386 (1.12-0.2ubuntu1) ...
Purging configuration files for libgpg-error0:i386 (1.12-0.2ubuntu1) ...
Removing libgphoto2-2:amd64 (2.4.13-1ubuntu1.2) ...
Purging configuration files for libgphoto2-2:amd64 (2.4.13-1ubuntu1.2) ...
Removing libgphoto2-2:i386 (2.4.13-1ubuntu1.2) ...
Purging configuration files for libgphoto2-2:i386 (2.4.13-1ubuntu1.2) ...
Removing libgphoto2-6:i386 (2.5.3.1-1ubuntu2.2) ...
Purging configuration files for libgphoto2-6:i386 (2.5.3.1-1ubuntu2.2) ...
Removing libgphoto2-port0:amd64 (2.4.13-1ubuntu1.2) ...
Purging configuration files for libgphoto2-port0:amd64 (2.4.13-1ubuntu1.2) ...
Removing libgphoto2-port0:i386 (2.4.13-1ubuntu1.2) ...
Purging configuration files for libgphoto2-port0:i386 (2.4.13-1ubuntu1.2) ...
Removing libgphoto2-port10:i386 (2.5.3.1-1ubuntu2.2) ...
Purging configuration files for libgphoto2-port10:i386 (2.5.3.1-1ubuntu2.2) ...
Removing libgrail5 (3.0.6-0ubuntu0.12.04.01) ...
Purging configuration files for libgrail5 (3.0.6-0ubuntu0.12.04.01) ...
Removing libgraph4 (2.26.3-10ubuntu1.2) ...
Purging configuration files for libgraph4 (2.26.3-10ubuntu1.2) ...
Removing libgraphite2-3:i386 (1.2.4-1ubuntu1) ...
Purging configuration files for libgraphite2-3:i386 (1.2.4-1ubuntu1) ...
Removing libgssapi-krb5-2:i386 (1.12+dfsg-2ubuntu4.2) ...
Purging configuration files for libgssapi-krb5-2:i386 (1.12+dfsg-2ubuntu4.2) ...
Removing libgssapi3-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Purging configuration files for libgssapi3-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Removing libgssglue1:amd64 (0.4-2ubuntu1) ...
Purging configuration files for libgssglue1:amd64 (0.4-2ubuntu1) ...
Removing libgstreamer-plugins-base0.10-0:i386 (0.10.36-1.1ubuntu2) ...
Purging configuration files for libgstreamer-plugins-base0.10-0:i386 (0.10.36-1.1ubuntu2) ...
Removing libgstreamer-plugins-base1.0-0:i386 (1.2.4-1~ubuntu1) ...
Purging configuration files for libgstreamer-plugins-base1.0-0:i386 (1.2.4-1~ubuntu1) ...
Removing libgstreamer0.10-0:i386 (0.10.36-1.2ubuntu3) ...
Purging configuration files for libgstreamer0.10-0:i386 (0.10.36-1.2ubuntu3) ...
Removing libgstreamer1.0-0:i386 (1.2.4-0ubuntu1) ...
Purging configuration files for libgstreamer1.0-0:i386 (1.2.4-0ubuntu1) ...
Removing libgtk2.0-0:i386 (2.24.23-0ubuntu1.1) ...
Purging configuration files for libgtk2.0-0:i386 (2.24.23-0ubuntu1.1) ...
Removing libgtksourceview-3.0-0:amd64 (3.4.2-0ubuntu1) ...
Purging configuration files for libgtksourceview-3.0-0:amd64 (3.4.2-0ubuntu1) ...
Removing libgtkspell-3-0 (3.0.0~hg20110814-1) ...
Purging configuration files for libgtkspell-3-0 (3.0.0~hg20110814-1) ...
Removing libgudev-1.0-0:i386 (1:204-5ubuntu20.9) ...
Purging configuration files for libgudev-1.0-0:i386 (1:204-5ubuntu20.9) ...
Removing libgvc5 (2.26.3-10ubuntu1.2) ...
Purging configuration files for libgvc5 (2.26.3-10ubuntu1.2) ...
Removing libgvpr1 (2.26.3-10ubuntu1.2) ...
Purging configuration files for libgvpr1 (2.26.3-10ubuntu1.2) ...
Removing libgweather-3-0 (3.4.1-0ubuntu1) ...
Purging configuration files for libgweather-3-0 (3.4.1-0ubuntu1) ...
Removing libgwibber-gtk2 (3.4.2-0ubuntu2.4) ...
Purging configuration files for libgwibber-gtk2 (3.4.2-0ubuntu2.4) ...
Removing libgwibber2 (3.4.2-0ubuntu2.4) ...
Purging configuration files for libgwibber2 (3.4.2-0ubuntu2.4) ...
Removing libharfbuzz0b:i386 (0.9.27-1ubuntu1) ...
Purging configuration files for libharfbuzz0b:i386 (0.9.27-1ubuntu1) ...
Removing libhcrypto4-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Purging configuration files for libhcrypto4-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Removing libheimbase1-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Purging configuration files for libheimbase1-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Removing libheimntlm0-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Purging configuration files for libheimntlm0-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Removing libhx509-5-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Purging configuration files for libhx509-5-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Removing libibus-1.0-0:amd64 (1.4.1-3ubuntu1) ...
Purging configuration files for libibus-1.0-0:amd64 (1.4.1-3ubuntu1) ...
Removing libibus-1.0-0:i386 (1.4.1-3ubuntu1) ...
Purging configuration files for libibus-1.0-0:i386 (1.4.1-3ubuntu1) ...
Removing libibus-1.0-5:i386 (1.5.5-1ubuntu3) ...
Purging configuration files for libibus-1.0-5:i386 (1.5.5-1ubuntu3) ...
Removing libical0 (0.48-1ubuntu3) ...
Purging configuration files for libical0 (0.48-1ubuntu3) ...
Removing libice6:i386 (2:1.0.8-2) ...
Purging configuration files for libice6:i386 (2:1.0.8-2) ...
Removing libicu48 (4.8.1.1-3ubuntu0.1) ...
Purging configuration files for libicu48 (4.8.1.1-3ubuntu0.1) ...
Removing libidn11:i386 (1.28-1ubuntu2) ...
Purging configuration files for libidn11:i386 (1.28-1ubuntu2) ...
Removing libiec61883-0:i386 (1.2.0-0.1ubuntu3) ...
Purging configuration files for libiec61883-0:i386 (1.2.0-0.1ubuntu3) ...
Removing libieee1284-3:i386 (0.2.11-12) ...
Purging configuration files for libieee1284-3:i386 (0.2.11-12) ...
Removing libimobiledevice2 (1.1.1-4) ...
Purging configuration files for libimobiledevice2 (1.1.1-4) ...
Removing libindicate-gtk3 (12.10.1-0ubuntu3) ...
Purging configuration files for libindicate-gtk3 (12.10.1-0ubuntu3) ...
Removing libindicate5 (12.10.1-0ubuntu3) ...
Purging configuration files for libindicate5 (12.10.1-0ubuntu3) ...
Removing libindicator-messages-status-provider1 (0.6.0-0ubuntu2) ...
Purging configuration files for libindicator-messages-status-provider1 (0.6.0-0ubuntu2) ...
Removing libindicator7 (12.10.2+14.04.20141007.1-0ubuntu1) ...
Purging configuration files for libindicator7 (12.10.2+14.04.20141007.1-0ubuntu1) ...
Removing libisc83 (1:9.8.1.dfsg.P1-4ubuntu0.9) ...
Purging configuration files for libisc83 (1:9.8.1.dfsg.P1-4ubuntu0.9) ...
Removing libisccc80 (1:9.8.1.dfsg.P1-4ubuntu0.9) ...
Purging configuration files for libisccc80 (1:9.8.1.dfsg.P1-4ubuntu0.9) ...
Removing libisccfg82 (1:9.8.1.dfsg.P1-4ubuntu0.9) ...
Purging configuration files for libisccfg82 (1:9.8.1.dfsg.P1-4ubuntu0.9) ...
Removing libjack-jackd2-0:i386 (1.9.9.5+20130622git7de15e7a-1ubuntu1) ...
Purging configuration files for libjack-jackd2-0:i386 (1.9.9.5+20130622git7de15e7a-1ubuntu1) ...
Removing libjasper1:i386 (1.900.1-14ubuntu3.2) ...
Purging configuration files for libjasper1:i386 (1.900.1-14ubuntu3.2) ...
Removing libjbig0:i386 (2.0-2ubuntu4.1) ...
Purging configuration files for libjbig0:i386 (2.0-2ubuntu4.1) ...
Removing libjpeg-turbo8:i386 (1.3.0-0ubuntu2) ...
Purging configuration files for libjpeg-turbo8:i386 (1.3.0-0ubuntu2) ...
Removing libk5crypto3:i386 (1.12+dfsg-2ubuntu4.2) ...
Purging configuration files for libk5crypto3:i386 (1.12+dfsg-2ubuntu4.2) ...
Removing libkadm5clnt-mit8:amd64 (1.10+dfsg~beta1-2ubuntu0.5) ...
Purging configuration files for libkadm5clnt-mit8:amd64 (1.10+dfsg~beta1-2ubuntu0.5) ...
Removing libkdb5-6:amd64 (1.10+dfsg~beta1-2ubuntu0.5) ...
Purging configuration files for libkdb5-6:amd64 (1.10+dfsg~beta1-2ubuntu0.5) ...
Removing libkeyutils1:i386 (1.5.6-1) ...
Purging configuration files for libkeyutils1:i386 (1.5.6-1) ...
Removing libkpathsea5 (2009-11ubuntu2) ...
Purging configuration files for libkpathsea5 (2009-11ubuntu2) ...
Removing libkrb5-26-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Purging configuration files for libkrb5-26-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Removing libkrb5-3:i386 (1.12+dfsg-2ubuntu4.2) ...
Purging configuration files for libkrb5-3:i386 (1.12+dfsg-2ubuntu4.2) ...
Removing libkrb5support0:i386 (1.12+dfsg-2ubuntu4.2) ...
Purging configuration files for libkrb5support0:i386 (1.12+dfsg-2ubuntu4.2) ...
Removing liblaunchpad-integration-3.0-1 (0.1.56.1) ...
Purging configuration files for liblaunchpad-integration-3.0-1 (0.1.56.1) ...
Removing liblcms1:amd64 (1.19.dfsg-1.2ubuntu5) ...
Purging configuration files for liblcms1:amd64 (1.19.dfsg-1.2ubuntu5) ...
Removing liblcms1:i386 (1.19.dfsg-1.2ubuntu5) ...
Purging configuration files for liblcms1:i386 (1.19.dfsg-1.2ubuntu5) ...
Removing libldap-2.4-2:i386 (2.4.31-1+nmu2ubuntu8) ...
Purging configuration files for libldap-2.4-2:i386 (2.4.31-1+nmu2ubuntu8) ...
Removing libllvm3.0:amd64 (3.0-4ubuntu1) ...
Purging configuration files for libllvm3.0:amd64 (3.0-4ubuntu1) ...
Removing liblqr-1-0:amd64 (0.4.1-2ubuntu1) ...
Purging configuration files for liblqr-1-0:amd64 (0.4.1-2ubuntu1) ...
Removing libltdl7:i386 (2.4.2-1.7ubuntu1) ...
Purging configuration files for libltdl7:i386 (2.4.2-1.7ubuntu1) ...
Removing liblua5.1-0:amd64 (5.1.5-5ubuntu0.1) ...
Purging configuration files for liblua5.1-0:amd64 (5.1.5-5ubuntu0.1) ...
Removing liblwres80 (1:9.8.1.dfsg.P1-4ubuntu0.9) ...
Purging configuration files for liblwres80 (1:9.8.1.dfsg.P1-4ubuntu0.9) ...
Removing libmad0:i386 (0.15.1b-8ubuntu1) ...
Purging configuration files for libmad0:i386 (0.15.1b-8ubuntu1) ...
Removing libmagickcore4 (8:6.6.9.7-5ubuntu3.3) ...
Purging configuration files for libmagickcore4 (8:6.6.9.7-5ubuntu3.3) ...
Removing libmetacity-private0 (1:2.34.1-1ubuntu11) ...
Purging configuration files for libmetacity-private0 (1:2.34.1-1ubuntu11) ...
Removing libmikmod2:i386 (3.1.16-1) ...
Purging configuration files for libmikmod2:i386 (3.1.16-1) ...
Removing libmng1:amd64 (1.0.10-3) ...
Purging configuration files for libmng1:amd64 (1.0.10-3) ...
Removing libmng1:i386 (1.0.10-3) ...
Purging configuration files for libmng1:i386 (1.0.10-3) ...
Removing libmpc2:amd64 (0.9-4) ...
Purging configuration files for libmpc2:amd64 (0.9-4) ...
Removing libmpg123-0:i386 (1.16.0-1ubuntu1) ...
Purging configuration files for libmpg123-0:i386 (1.16.0-1ubuntu1) ...
Removing libmusicbrainz3-6 (3.0.2-2.1) ...
Purging configuration files for libmusicbrainz3-6 (3.0.2-2.1) ...
Removing libnspr4:i386 (2:4.10.7-0ubuntu0.14.04.1) ...
Purging configuration files for libnspr4:i386 (2:4.10.7-0ubuntu0.14.04.1) ...
Removing libnss3:i386 (2:3.17.1-0ubuntu0.14.04.2) ...
Purging configuration files for libnss3:i386 (2:3.17.1-0ubuntu0.14.04.2) ...
Removing libnux-2.0-0 (2.14.1-0ubuntu1) ...
Purging configuration files for libnux-2.0-0 (2.14.1-0ubuntu1) ...
Removing libodbc1:i386 (2.2.14p2-5ubuntu5) ...
Purging configuration files for libodbc1:i386 (2.2.14p2-5ubuntu5) ...
Removing libogg0:i386 (1.3.1-1ubuntu1) ...
Purging configuration files for libogg0:i386 (1.3.1-1ubuntu1) ...
Removing libopenal-data (1:1.14-4ubuntu1) ...
Purging configuration files for libopenal-data (1:1.14-4ubuntu1) ...
Removing libopenal1:i386 (1:1.14-4ubuntu1) ...
Purging configuration files for libopenal1:i386 (1:1.14-4ubuntu1) ...
Removing liborc-0.4-0:i386 (1:0.4.18-1ubuntu1) ...
Purging configuration files for liborc-0.4-0:i386 (1:0.4.18-1ubuntu1) ...
Removing libotr2 (3.2.0-4ubuntu0.2) ...
Purging configuration files for libotr2 (3.2.0-4ubuntu0.2) ...
Removing liboverlay-scrollbar-0.2-0 (0.2.16-0ubuntu1.1) ...
Purging configuration files for liboverlay-scrollbar-0.2-0 (0.2.16-0ubuntu1.1) ...
Removing liboverlay-scrollbar3-0.2-0 (0.2.16-0ubuntu1.1) ...
Purging configuration files for liboverlay-scrollbar3-0.2-0 (0.2.16-0ubuntu1.1) ...
Removing libp11-kit0:i386 (0.20.2-2ubuntu2) ...
Purging configuration files for libp11-kit0:i386 (0.20.2-2ubuntu2) ...
Removing libpackagekit-glib2-14 (0.7.2-4ubuntu3) ...
Purging configuration files for libpackagekit-glib2-14 (0.7.2-4ubuntu3) ...
Removing libpango-1.0-0:i386 (1.36.3-1ubuntu1.1) ...
Purging configuration files for libpango-1.0-0:i386 (1.36.3-1ubuntu1.1) ...
Removing libpangocairo-1.0-0:i386 (1.36.3-1ubuntu1.1) ...
Purging configuration files for libpangocairo-1.0-0:i386 (1.36.3-1ubuntu1.1) ...
Removing libpangoft2-1.0-0:i386 (1.36.3-1ubuntu1.1) ...
Purging configuration files for libpangoft2-1.0-0:i386 (1.36.3-1ubuntu1.1) ...
Removing libpangox-1.0-0:i386 (0.0.2-4ubuntu1) ...
Purging configuration files for libpangox-1.0-0:i386 (0.0.2-4ubuntu1) ...
Removing libpangoxft-1.0-0:i386 (1.36.3-1ubuntu1.1) ...
Purging configuration files for libpangoxft-1.0-0:i386 (1.36.3-1ubuntu1.1) ...
Removing libpixman-1-0:i386 (0.30.2-2ubuntu1) ...
Purging configuration files for libpixman-1-0:i386 (0.30.2-2ubuntu1) ...
Removing libpoppler19:amd64 (0.18.4-1ubuntu3.1) ...
Purging configuration files for libpoppler19:amd64 (0.18.4-1ubuntu3.1) ...
Removing libprotobuf7 (2.4.1-1ubuntu2) ...
Purging configuration files for libprotobuf7 (2.4.1-1ubuntu2) ...
Removing libprotoc7 (2.4.1-1ubuntu2) ...
Purging configuration files for libprotoc7 (2.4.1-1ubuntu2) ...
Removing libprotoc8:amd64 (2.5.0-9ubuntu1) ...
Purging configuration files for libprotoc8:amd64 (2.5.0-9ubuntu1) ...
Removing libproxy1:i386 (0.4.11-0ubuntu4) ...
Purging configuration files for libproxy1:i386 (0.4.11-0ubuntu4) ...
Removing libpth20:amd64 (2.0.7-19ubuntu1) ...
Purging configuration files for libpth20:amd64 (2.0.7-19ubuntu1) ...
Removing libpulse-mainloop-glib0:i386 (1:4.0-0ubuntu11) ...
Purging configuration files for libpulse-mainloop-glib0:i386 (1:4.0-0ubuntu11) ...
Removing libpulse0:i386 (1:4.0-0ubuntu11) ...
Purging configuration files for libpulse0:i386 (1:4.0-0ubuntu11) ...
Removing libqt4-declarative:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Purging configuration files for libqt4-declarative:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-designer:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Purging configuration files for libqt4-designer:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-network:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Purging configuration files for libqt4-network:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-opengl:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Purging configuration files for libqt4-opengl:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-qt3support:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Purging configuration files for libqt4-qt3support:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-script:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Purging configuration files for libqt4-script:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-scripttools:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Purging configuration files for libqt4-scripttools:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-sql:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Purging configuration files for libqt4-sql:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-svg:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Purging configuration files for libqt4-svg:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-test:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Purging configuration files for libqt4-test:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-xml:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Purging configuration files for libqt4-xml:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-xmlpatterns:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Purging configuration files for libqt4-xmlpatterns:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqtbamf1 (0.2.4-0ubuntu2) ...
Purging configuration files for libqtbamf1 (0.2.4-0ubuntu2) ...
Removing libqtcore4:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Purging configuration files for libqtcore4:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqtdbus4:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Purging configuration files for libqtdbus4:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqtdee2 (0.2.4-0ubuntu1) ...
Purging configuration files for libqtdee2 (0.2.4-0ubuntu1) ...
Removing libqtgconf1 (0.1-0ubuntu5) ...
Purging configuration files for libqtgconf1 (0.1-0ubuntu5) ...
Removing libqtgui4:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Purging configuration files for libqtgui4:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqtwebkit4:i386 (2.3.2-0ubuntu7) ...
Purging configuration files for libqtwebkit4:i386 (2.3.2-0ubuntu7) ...
Removing libquvi7:amd64 (0.4.1-1ubuntu3) ...
Purging configuration files for libquvi7:amd64 (0.4.1-1ubuntu3) ...
Removing libraw1394-11:i386 (2.1.0-1ubuntu1) ...
Purging configuration files for libraw1394-11:i386 (2.1.0-1ubuntu1) ...
Removing libraw5 (0.14.4-0ubuntu2.2) ...
Purging configuration files for libraw5 (0.14.4-0ubuntu2.2) ...
Removing libreadline6:i386 (6.3-4ubuntu2) ...
Purging configuration files for libreadline6:i386 (6.3-4ubuntu2) ...
Removing librhythmbox-core5 (2.96-0ubuntu4.3) ...
Purging configuration files for librhythmbox-core5 (2.96-0ubuntu4.3) ...
Removing libroken18-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Purging configuration files for libroken18-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Removing librsvg2-2:i386 (2.40.2-1) ...
Purging configuration files for librsvg2-2:i386 (2.40.2-1) ...
Removing librtmp0:i386 (2.4+20121230.gitdf6c518-1) ...
Purging configuration files for librtmp0:i386 (2.4+20121230.gitdf6c518-1) ...
Removing libruby1.8 (1.8.7.352-2ubuntu1.6) ...
Purging configuration files for libruby1.8 (1.8.7.352-2ubuntu1.6) ...
Removing libsamplerate0:i386 (0.1.8-7) ...
Purging configuration files for libsamplerate0:i386 (0.1.8-7) ...
Removing libsane:i386 (1.0.23-3ubuntu3.1) ...
Purging configuration files for libsane:i386 (1.0.23-3ubuntu3.1) ...
Removing directory /etc/sane.d/ ...
Removing libsasl2-2:i386 (2.1.25.dfsg1-17build1) ...
Purging configuration files for libsasl2-2:i386 (2.1.25.dfsg1-17build1) ...
Removing libsdl-image1.2:i386 (1.2.12-5build2) ...
Purging configuration files for libsdl-image1.2:i386 (1.2.12-5build2) ...
Removing libsdl-mixer1.2:i386 (1.2.12-10) ...
Purging configuration files for libsdl-mixer1.2:i386 (1.2.12-10) ...
Removing libsdl-net1.2:i386 (1.2.8-4) ...
Purging configuration files for libsdl-net1.2:i386 (1.2.8-4) ...
Removing libsdl-ttf2.0-0:i386 (2.0.11-3) ...
Purging configuration files for libsdl-ttf2.0-0:i386 (2.0.11-3) ...
Removing libsdl1.2debian:i386 (1.2.15-8ubuntu1.1) ...
Purging configuration files for libsdl1.2debian:i386 (1.2.15-8ubuntu1.1) ...
Removing libsecret-1-0:i386 (0.16-0ubuntu1) ...
Purging configuration files for libsecret-1-0:i386 (0.16-0ubuntu1) ...
Removing libshout3:i386 (2.3.1-3) ...
Purging configuration files for libshout3:i386 (2.3.1-3) ...
Removing libslp1 (1.2.1-9) ...
Purging configuration files for libslp1 (1.2.1-9) ...
Removing libsm6:i386 (2:1.2.1-2) ...
Purging configuration files for libsm6:i386 (2:1.2.1-2) ...
Removing libsmi2ldbl:amd64 (0.4.8+dfsg2-8ubuntu2) ...
Purging configuration files for libsmi2ldbl:amd64 (0.4.8+dfsg2-8ubuntu2) ...
Removing libsndfile1:i386 (1.0.25-7ubuntu2) ...
Purging configuration files for libsndfile1:i386 (1.0.25-7ubuntu2) ...
Removing libsnmp15 (5.4.3~dfsg-2.4ubuntu1.2) ...
Purging configuration files for libsnmp15 (5.4.3~dfsg-2.4ubuntu1.2) ...
dpkg: warning: while removing libsnmp15, directory '/etc/snmp' not empty so not removed
Removing libsoup-gnome2.4-1:i386 (2.44.2-1ubuntu2) ...
Purging configuration files for libsoup-gnome2.4-1:i386 (2.44.2-1ubuntu2) ...
Removing libsoup2.4-1:i386 (2.44.2-1ubuntu2) ...
Purging configuration files for libsoup2.4-1:i386 (2.44.2-1ubuntu2) ...
Removing libspeex1:i386 (1.2~rc1.1-1ubuntu1) ...
Purging configuration files for libspeex1:i386 (1.2~rc1.1-1ubuntu1) ...
Removing libspeexdsp1:i386 (1.2~rc1.1-1ubuntu1) ...
Purging configuration files for libspeexdsp1:i386 (1.2~rc1.1-1ubuntu1) ...
Removing libsqlite3-0:i386 (3.8.2-1ubuntu2) ...
Purging configuration files for libsqlite3-0:i386 (3.8.2-1ubuntu2) ...
Removing libssl0.9.8:i386 (0.9.8o-7ubuntu3.2.14.04.1) ...
Purging configuration files for libssl0.9.8:i386 (0.9.8o-7ubuntu3.2.14.04.1) ...
Removing libssl1.0.0:i386 (1.0.1f-1ubuntu2.8) ...
Purging configuration files for libssl1.0.0:i386 (1.0.1f-1ubuntu2.8) ...
Removing libstdc++5:i386 (1:3.3.6-25ubuntu4) ...
Purging configuration files for libstdc++5:i386 (1:3.3.6-25ubuntu4) ...
Removing libstdc++6:i386 (4.8.2-19ubuntu1) ...
Purging configuration files for libstdc++6:i386 (4.8.2-19ubuntu1) ...
Removing libsyncdaemon-1.0-1 (3.0.2-0ubuntu2.2) ...
Purging configuration files for libsyncdaemon-1.0-1 (3.0.2-0ubuntu2.2) ...
Removing libsysfs2:amd64 (2.1.0+repack-3ubuntu1) ...
Purging configuration files for libsysfs2:amd64 (2.1.0+repack-3ubuntu1) ...
Removing libtag1-vanilla:i386 (1.9.1-2) ...
Purging configuration files for libtag1-vanilla:i386 (1.9.1-2) ...
Removing libtasn1-3:amd64 (2.10-1ubuntu1.2) ...
Purging configuration files for libtasn1-3:amd64 (2.10-1ubuntu1.2) ...
Removing libtasn1-3:i386 (2.10-1ubuntu1.2) ...
Purging configuration files for libtasn1-3:i386 (2.10-1ubuntu1.2) ...
Removing libtasn1-6:i386 (3.4-3ubuntu0.1) ...
Purging configuration files for libtasn1-6:i386 (3.4-3ubuntu0.1) ...
Removing libtcl8.5:amd64 (8.5.15-2ubuntu1) ...
Purging configuration files for libtcl8.5:amd64 (8.5.15-2ubuntu1) ...
Removing libtdb1:i386 (1.2.12-1) ...
Purging configuration files for libtdb1:i386 (1.2.12-1) ...
Removing libtelepathy-farstream2:amd64 (0.4.0-3ubuntu2) ...
Purging configuration files for libtelepathy-farstream2:amd64 (0.4.0-3ubuntu2) ...
Removing libtelepathy-logger2:amd64 (0.4.0-0ubuntu1) ...
Purging configuration files for libtelepathy-logger2:amd64 (0.4.0-0ubuntu1) ...
Removing libthai0:i386 (0.1.20-3) ...
Purging configuration files for libthai0:i386 (0.1.20-3) ...
Removing libtheora0:i386 (1.1.1+dfsg.1-3.2) ...
Purging configuration files for libtheora0:i386 (1.1.1+dfsg.1-3.2) ...
Removing libtiff4:amd64 (3.9.5-2ubuntu1.6) ...
Purging configuration files for libtiff4:amd64 (3.9.5-2ubuntu1.6) ...
Removing libtiff4:i386 (3.9.5-2ubuntu1.6) ...
Purging configuration files for libtiff4:i386 (3.9.5-2ubuntu1.6) ...
Removing libtiff5:i386 (4.0.3-7ubuntu0.1) ...
Purging configuration files for libtiff5:i386 (4.0.3-7ubuntu0.1) ...
Removing libtirpc1:amd64 (0.2.2-5ubuntu2) ...
Purging configuration files for libtirpc1:amd64 (0.2.2-5ubuntu2) ...
Removing libtommath0 (0.42.0-1) ...
Purging configuration files for libtommath0 (0.42.0-1) ...
Removing libtotem-plparser17 (3.4.1-1) ...
Purging configuration files for libtotem-plparser17 (3.4.1-1) ...
Removing libtspi1 (0.3.11.2-1) ...
Purging configuration files for libtspi1 (0.3.11.2-1) ...
Removing libu1db-qt5-3:amd64 (0.1.5+14.04.20140313-0ubuntu2) ...
Purging configuration files for libu1db-qt5-3:amd64 (0.1.5+14.04.20140313-0ubuntu2) ...
Removing libubuntuoneui-3.0-1 (3.0.1-0ubuntu1) ...
Purging configuration files for libubuntuoneui-3.0-1 (3.0.1-0ubuntu1) ...
Removing libudev0:amd64 (175-0ubuntu9.8) ...
Purging configuration files for libudev0:amd64 (175-0ubuntu9.8) ...
Removing libudev0:i386 (175-0ubuntu9.8) ...
Purging configuration files for libudev0:i386 (175-0ubuntu9.8) ...
Removing libudev1:i386 (204-5ubuntu20.12) ...
Purging configuration files for libudev1:i386 (204-5ubuntu20.12) ...
Removing libunique-3.0-0 (3.0.2-2ubuntu1) ...
Purging configuration files for libunique-3.0-0 (3.0.2-2ubuntu1) ...
Removing libunistring0:i386 (0.9.3-5ubuntu3) ...
Purging configuration files for libunistring0:i386 (0.9.3-5ubuntu3) ...
Removing libunity-core-5.0-5 (5.20.0-0ubuntu3) ...
Purging configuration files for libunity-core-5.0-5 (5.20.0-0ubuntu3) ...
Removing libupstart1:amd64 (1.12.1-0ubuntu4.2) ...
Purging configuration files for libupstart1:amd64 (1.12.1-0ubuntu4.2) ...
Removing libusb-0.1-4:i386 (2:0.1.12-23.3ubuntu1) ...
Purging configuration files for libusb-0.1-4:i386 (2:0.1.12-23.3ubuntu1) ...
Removing libusb-1.0-0:i386 (2:1.0.17-1ubuntu2) ...
Purging configuration files for libusb-1.0-0:i386 (2:1.0.17-1ubuntu2) ...
Removing libusbmuxd1 (1.0.7-2ubuntu0.1) ...
Purging configuration files for libusbmuxd1 (1.0.7-2ubuntu0.1) ...
Removing libv4l-0:i386 (1.0.1-1) ...
Purging configuration files for libv4l-0:i386 (1.0.1-1) ...
Removing libv4lconvert0:i386 (1.0.1-1) ...
Purging configuration files for libv4lconvert0:i386 (1.0.1-1) ...
Removing libvisual-0.4-0:i386 (0.4.0-5) ...
Purging configuration files for libvisual-0.4-0:i386 (0.4.0-5) ...
Removing libvorbis0a:i386 (1.3.2-1.3ubuntu1) ...
Purging configuration files for libvorbis0a:i386 (1.3.2-1.3ubuntu1) ...
Removing libvorbisenc2:i386 (1.3.2-1.3ubuntu1) ...
Purging configuration files for libvorbisenc2:i386 (1.3.2-1.3ubuntu1) ...
Removing libvorbisfile3:i386 (1.3.2-1.3ubuntu1) ...
Purging configuration files for libvorbisfile3:i386 (1.3.2-1.3ubuntu1) ...
Removing libvpx1:i386 (1.3.0-2) ...
Purging configuration files for libvpx1:i386 (1.3.0-2) ...
Removing libwavpack1:i386 (4.70.0-1) ...
Purging configuration files for libwavpack1:i386 (4.70.0-1) ...
Removing libwebp5:i386 (0.4.0-4) ...
Purging configuration files for libwebp5:i386 (0.4.0-4) ...
Removing libwind0-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Purging configuration files for libwind0-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1) ...
Removing libwireshark-data (1.10.6-1) ...
Purging configuration files for libwireshark-data (1.10.6-1) ...
Removing libwireshark1 (1.6.7-1) ...
Purging configuration files for libwireshark1 (1.6.7-1) ...
Removing libwireshark3:amd64 (1.10.6-1) ...
Purging configuration files for libwireshark3:amd64 (1.10.6-1) ...
Removing libwiretap1 (1.6.7-1) ...
Purging configuration files for libwiretap1 (1.6.7-1) ...
Removing libwiretap3:amd64 (1.10.6-1) ...
Purging configuration files for libwiretap3:amd64 (1.10.6-1) ...
Removing libwrap0:i386 (7.6.q-25) ...
Purging configuration files for libwrap0:i386 (7.6.q-25) ...
Removing libwsutil1 (1.6.7-1) ...
Purging configuration files for libwsutil1 (1.6.7-1) ...
Removing libwsutil3:amd64 (1.10.6-1) ...
Purging configuration files for libwsutil3:amd64 (1.10.6-1) ...
Removing libx11-6:i386 (2:1.6.2-1ubuntu2) ...
Purging configuration files for libx11-6:i386 (2:1.6.2-1ubuntu2) ...
Removing libx11-xcb1:i386 (2:1.6.2-1ubuntu2) ...
Purging configuration files for libx11-xcb1:i386 (2:1.6.2-1ubuntu2) ...
Removing libxatracker1:amd64 (8.0.4-0ubuntu0.7) ...
Purging configuration files for libxatracker1:amd64 (8.0.4-0ubuntu0.7) ...
Removing libxau6:i386 (1:1.0.8-1) ...
Purging configuration files for libxau6:i386 (1:1.0.8-1) ...
Removing libxaw7:i386 (2:1.0.12-1) ...
Purging configuration files for libxaw7:i386 (2:1.0.12-1) ...
Removing libxcb-dri2-0:i386 (1.10-2ubuntu1) ...
Purging configuration files for libxcb-dri2-0:i386 (1.10-2ubuntu1) ...
Removing libxcb-dri3-0:i386 (1.10-2ubuntu1) ...
Purging configuration files for libxcb-dri3-0:i386 (1.10-2ubuntu1) ...
Removing libxcb-glx0:i386 (1.10-2ubuntu1) ...
Purging configuration files for libxcb-glx0:i386 (1.10-2ubuntu1) ...
Removing libxcb-present0:i386 (1.10-2ubuntu1) ...
Purging configuration files for libxcb-present0:i386 (1.10-2ubuntu1) ...
Removing libxcb-render0:i386 (1.10-2ubuntu1) ...
Purging configuration files for libxcb-render0:i386 (1.10-2ubuntu1) ...
Removing libxcb-shm0:i386 (1.10-2ubuntu1) ...
Purging configuration files for libxcb-shm0:i386 (1.10-2ubuntu1) ...
Removing libxcb-sync1:i386 (1.10-2ubuntu1) ...
Purging configuration files for libxcb-sync1:i386 (1.10-2ubuntu1) ...
Removing libxcb1:i386 (1.10-2ubuntu1) ...
Purging configuration files for libxcb1:i386 (1.10-2ubuntu1) ...
Removing libxcomposite1:i386 (1:0.4.4-1) ...
Purging configuration files for libxcomposite1:i386 (1:0.4.4-1) ...
Removing libxcursor1:i386 (1:1.1.14-1) ...
Purging configuration files for libxcursor1:i386 (1:1.1.14-1) ...
Removing libxdamage1:i386 (1:1.1.4-1ubuntu1) ...
Purging configuration files for libxdamage1:i386 (1:1.1.4-1ubuntu1) ...
Removing libxdmcp6:i386 (1:1.1.1-1) ...
Purging configuration files for libxdmcp6:i386 (1:1.1.1-1) ...
Removing libxext6:i386 (2:1.3.2-1) ...
Purging configuration files for libxext6:i386 (2:1.3.2-1) ...
Removing libxfixes3:i386 (1:5.0.1-1ubuntu1) ...
Purging configuration files for libxfixes3:i386 (1:5.0.1-1ubuntu1) ...
Removing libxft2:i386 (2.3.1-2) ...
Purging configuration files for libxft2:i386 (2.3.1-2) ...
Removing libxi6:i386 (2:1.7.1.901-1ubuntu1) ...
Purging configuration files for libxi6:i386 (2:1.7.1.901-1ubuntu1) ...
Removing libxinerama1:i386 (2:1.1.3-1) ...
Purging configuration files for libxinerama1:i386 (2:1.1.3-1) ...
Removing libxml2:i386 (2.9.1+dfsg1-3ubuntu4.4) ...
Purging configuration files for libxml2:i386 (2.9.1+dfsg1-3ubuntu4.4) ...
Removing libxmu6:i386 (2:1.1.1-1) ...
Purging configuration files for libxmu6:i386 (2:1.1.1-1) ...
Removing libxp6:i386 (1:1.0.2-1ubuntu1) ...
Purging configuration files for libxp6:i386 (1:1.0.2-1ubuntu1) ...
Removing libxpm4:i386 (1:3.5.10-1) ...
Purging configuration files for libxpm4:i386 (1:3.5.10-1) ...
Removing libxrandr2:i386 (2:1.4.2-1) ...
Purging configuration files for libxrandr2:i386 (2:1.4.2-1) ...
Removing libxrender1:i386 (1:0.9.8-1) ...
Purging configuration files for libxrender1:i386 (1:0.9.8-1) ...
Removing libxshmfence1:i386 (1.1-2) ...
Purging configuration files for libxshmfence1:i386 (1.1-2) ...
Removing libxslt1.1:i386 (1.1.28-2build1) ...
Purging configuration files for libxslt1.1:i386 (1.1.28-2build1) ...
Removing libxss1:i386 (1:1.2.2-1) ...
Purging configuration files for libxss1:i386 (1:1.2.2-1) ...
Removing libxt6:i386 (1:1.1.4-1) ...
Purging configuration files for libxt6:i386 (1:1.1.4-1) ...
Removing libxtst6:i386 (2:1.2.2-1) ...
Purging configuration files for libxtst6:i386 (2:1.2.2-1) ...
Removing libxv1:i386 (2:1.0.10-1) ...
Purging configuration files for libxv1:i386 (2:1.0.10-1) ...
Removing libxxf86vm1:i386 (1:1.1.3-1) ...
Purging configuration files for libxxf86vm1:i386 (1:1.1.3-1) ...
Removing libyajl1 (1.0.12-2) ...
Purging configuration files for libyajl1 (1.0.12-2) ...
Removing linux-image-3.16.0-31-generic (3.16.0-31.43~14.04.1) ...
Purging configuration files for linux-image-3.16.0-31-generic (3.16.0-31.43~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-31-generic /boot/vmlinuz-3.16.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-31-generic /boot/vmlinuz-3.16.0-31-generic
Removing linux-image-3.16.0-33-generic (3.16.0-33.44~14.04.1) ...
Purging configuration files for linux-image-3.16.0-33-generic (3.16.0-33.44~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-33-generic /boot/vmlinuz-3.16.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-33-generic /boot/vmlinuz-3.16.0-33-generic
Removing linux-image-3.16.0-34-generic (3.16.0-34.47~14.04.1) ...
Purging configuration files for linux-image-3.16.0-34-generic (3.16.0-34.47~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
Removing linux-image-3.16.0-36-generic (3.16.0-36.48~14.04.1) ...
Purging configuration files for linux-image-3.16.0-36-generic (3.16.0-36.48~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-36-generic /boot/vmlinuz-3.16.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-36-generic /boot/vmlinuz-3.16.0-36-generic
Removing linux-image-3.16.0-37-generic (3.16.0-37.51~14.04.1) ...
Purging configuration files for linux-image-3.16.0-37-generic (3.16.0-37.51~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-37-generic /boot/vmlinuz-3.16.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-37-generic /boot/vmlinuz-3.16.0-37-generic
Removing linux-image-3.16.0-38-generic (3.16.0-38.52~14.04.1) ...
Purging configuration files for linux-image-3.16.0-38-generic (3.16.0-38.52~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-38-generic /boot/vmlinuz-3.16.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-38-generic /boot/vmlinuz-3.16.0-38-generic
Removing linux-image-3.16.0-39-generic (3.16.0-39.53~14.04.1) ...
Purging configuration files for linux-image-3.16.0-39-generic (3.16.0-39.53~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-39-generic /boot/vmlinuz-3.16.0-39-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-39-generic /boot/vmlinuz-3.16.0-39-generic
Removing linux-image-3.16.0-41-generic (3.16.0-41.57~14.04.1) ...
Purging configuration files for linux-image-3.16.0-41-generic (3.16.0-41.57~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-41-generic /boot/vmlinuz-3.16.0-41-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-41-generic /boot/vmlinuz-3.16.0-41-generic
Removing linux-image-3.16.0-43-generic (3.16.0-43.58~14.04.1) ...
Purging configuration files for linux-image-3.16.0-43-generic (3.16.0-43.58~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-43-generic /boot/vmlinuz-3.16.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-43-generic /boot/vmlinuz-3.16.0-43-generic
Removing linux-image-3.2.0-37-generic (3.2.0-37.58) ...
Purging configuration files for linux-image-3.2.0-37-generic (3.2.0-37.58) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
Removing linux-image-extra-3.16.0-31-generic (3.16.0-31.43~14.04.1) ...
Purging configuration files for linux-image-extra-3.16.0-31-generic (3.16.0-31.43~14.04.1) ...
Removing linux-image-extra-3.16.0-33-generic (3.16.0-33.44~14.04.1) ...
Purging configuration files for linux-image-extra-3.16.0-33-generic (3.16.0-33.44~14.04.1) ...
Removing linux-image-extra-3.16.0-34-generic (3.16.0-34.47~14.04.1) ...
Purging configuration files for linux-image-extra-3.16.0-34-generic (3.16.0-34.47~14.04.1) ...
Removing linux-image-extra-3.16.0-36-generic (3.16.0-36.48~14.04.1) ...
Purging configuration files for linux-image-extra-3.16.0-36-generic (3.16.0-36.48~14.04.1) ...
Removing linux-image-extra-3.16.0-37-generic (3.16.0-37.51~14.04.1) ...
Purging configuration files for linux-image-extra-3.16.0-37-generic (3.16.0-37.51~14.04.1) ...
Removing linux-image-extra-3.16.0-38-generic (3.16.0-38.52~14.04.1) ...
Purging configuration files for linux-image-extra-3.16.0-38-generic (3.16.0-38.52~14.04.1) ...
Removing linux-image-extra-3.16.0-39-generic (3.16.0-39.53~14.04.1) ...
Purging configuration files for linux-image-extra-3.16.0-39-generic (3.16.0-39.53~14.04.1) ...
Removing linux-image-extra-3.16.0-41-generic (3.16.0-41.57~14.04.1) ...
Purging configuration files for linux-image-extra-3.16.0-41-generic (3.16.0-41.57~14.04.1) ...
Removing linux-image-extra-3.16.0-43-generic (3.16.0-43.58~14.04.1) ...
Purging configuration files for linux-image-extra-3.16.0-43-generic (3.16.0-43.58~14.04.1) ...
Removing netdisco-backend (1.0-1) ...
Purging configuration files for netdisco-backend (1.0-1) ...
dpkg: warning: while removing netdisco-backend, directory '/var/log/netdisco' not empty so not removed
dpkg: warning: while removing netdisco-backend, directory '/usr/lib/netdisco' not empty so not removed
Removing netdisco-frontend (1.0-1) ...
Purging configuration files for netdisco-frontend (1.0-1) ...
dpkg: warning: while removing netdisco-frontend, directory '/usr/share/netdisco/html/doc' not empty so not removed
dpkg: warning: while removing netdisco-frontend, directory '/var/lib/netdisco/mason' not empty so not removed
dpkg: warning: while removing netdisco-frontend, directory '/etc/netdisco' not empty so not removed
Removing ntop (3:4.1.0+dfsg1-1) ...
Purging configuration files for ntop (3:4.1.0+dfsg1-1) ...
Removing odbcinst1debian2:i386 (2.2.14p2-5ubuntu5) ...
Purging configuration files for odbcinst1debian2:i386 (2.2.14p2-5ubuntu5) ...
Removing oss-compat (1) ...
Purging configuration files for oss-compat (1) ...
Removing postfix (2.9.6-1~12.04.1) ...
Purging configuration files for postfix (2.9.6-1~12.04.1) ...
Removing python-aptdaemon.pkcompat (0.43+bzr805-0ubuntu9) ...
Purging configuration files for python-aptdaemon.pkcompat (0.43+bzr805-0ubuntu9) ...
Removing python-ubuntuone-client (3.0.2-0ubuntu2.2) ...
Purging configuration files for python-ubuntuone-client (3.0.2-0ubuntu2.2) ...
Removing python-ubuntuone-storageprotocol (3.0.2-0ubuntu1) ...
Purging configuration files for python-ubuntuone-storageprotocol (3.0.2-0ubuntu1) ...
Removing rancid (2.3.6-2) ...
Purging configuration files for rancid (2.3.6-2) ...
Removing ruby1.8 (1.8.7.352-2ubuntu1.6) ...
Purging configuration files for ruby1.8 (1.8.7.352-2ubuntu1.6) ...
Removing tcl8.5 (8.5.15-2ubuntu1) ...
Purging configuration files for tcl8.5 (8.5.15-2ubuntu1) ...
Removing ubuntuone-client (3.0.2-0ubuntu2.2) ...
Purging configuration files for ubuntuone-client (3.0.2-0ubuntu2.2) ...
Removing unity-common (5.20.0-0ubuntu3) ...
Purging configuration files for unity-common (5.20.0-0ubuntu3) ...
dpkg: warning: while removing unity-common, directory '/etc/compizconfig/upgrades' not empty so not removed
Removing wireshark (1.10.6-1) ...
Purging configuration files for wireshark (1.10.6-1) ...
Removing wireshark-common (1.10.6-1) ...
Purging configuration files for wireshark-common (1.10.6-1) ...
Removing xaw3dg:i386 (1.5+E-18.2) ...
Purging configuration files for xaw3dg:i386 (1.5+E-18.2) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
root@:~# apt-get update




0% [Working]
            
Ign http://security.ubuntu.com trusty-security InRelease


            
10% [Waiting for headers]
                         
Ign http://us.archive.ubuntu.com trusty InRelease


                         
17% [Working]
             
Ign http://us.archive.ubuntu.com trusty-updates InRelease


             
21% [Waiting for headers]
                         
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]


                         
0% [Waiting for headers] [1 Release.gpg 0 B/933 B 0%]
                                                     
100% [Waiting for headers]
                          
Ign http://us.archive.ubuntu.com trusty-backports InRelease


100% [Waiting for headers]
                          
Get:2 http://security.ubuntu.com trusty-security Release [63.5 kB]


                          
1% [Waiting for headers] [2 Release 0 B/63.5 kB 0%]
                                                   
Hit http://us.archive.ubuntu.com trusty Release.gpg


                                                   
37% [2 Release 22.9 kB/63.5 kB 36%]
                                   
Get:3 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]


                                   
89% [3 Release.gpg 0 B/933 B 0%] [2 Release 57.1 kB/63.5 kB 90%]
                                                                
90% [2 Release 57.1 kB/63.5 kB 90%]
                                   
100% [Waiting for headers]
                          
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg


100% [Waiting for headers]
                          
100% [2 Release gpgv 63.5 kB] [Waiting for headers]
                                                   
100% [Waiting for headers]
                          
Hit http://us.archive.ubuntu.com trusty Release


                          
100% [Waiting for headers] [Waiting for headers]
                                                
100% [Release gpgv 58.5 kB] [Waiting for headers] [Waiting for headers]
                                                                       
100% [Waiting for headers] [Waiting for headers]
                                                
Get:4 http://security.ubuntu.com trusty-security/main Sources [91.1 kB]


                                                
58% [Waiting for headers] [4 Sources 25.6 kB/91.1 kB 28%]
                                                         
Get:5 http://us.archive.ubuntu.com trusty-updates Release [63.5 kB]


                                                         
51% [5 Release 13.4 kB/63.5 kB 21%] [4 Sources 33.9 kB/91.1 kB 37%]
                                                                   
87% [5 Release 33.9 kB/63.5 kB 53%]
                                   
87% [4 Sources bzip2 0 B] [5 Release 33.9 kB/63.5 kB 53%] [Waiting for headers]
                                                                               
96% [5 Release 54.4 kB/63.5 kB 86%] [Waiting for headers]
                                                         
Get:6 http://security.ubuntu.com trusty-security/restricted Sources [2,061 B]


96% [5 Release 54.4 kB/63.5 kB 86%] [Waiting for headers]
                                                         
96% [6 Sources bzip2 0 B] [5 Release 54.4 kB/63.5 kB 86%] [Waiting for headers]
                                                                               
96% [5 Release 54.4 kB/63.5 kB 86%] [Waiting for headers]
                                                         
100% [Waiting for headers] [Waiting for headers]
                                                
100% [5 Release gpgv 63.5 kB] [Waiting for headers] [Waiting for headers]
                                                                         
100% [Waiting for headers] [Waiting for headers]
                                                
Get:7 http://security.ubuntu.com trusty-security/universe Sources [28.5 kB]


                                                
94% [Waiting for headers] [7 Sources 13.3 kB/28.5 kB 47%]
                                                         
100% [Waiting for headers] [Waiting for headers]
                                                
100% [7 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers]
                                                                      
Hit http://us.archive.ubuntu.com trusty-backports Release


                                                                      
100% [7 Sources bzip2 0 B] [Waiting for headers]
                                                
100% [7 Sources bzip2 0 B] [Release gpgv 63.5 kB] [Waiting for headers] [Waitin
                                                                               
100% [Release gpgv 63.5 kB] [Waiting for headers] [Waiting for headers]
                                                                       
100% [Waiting for headers] [Waiting for headers]
                                                
Get:8 http://security.ubuntu.com trusty-security/multiverse Sources [2,334 B]


                                                
100% [Waiting for headers]
                          
100% [8 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers]
                                                                      
100% [Waiting for headers] [Waiting for headers]
                                                
Hit http://us.archive.ubuntu.com trusty/main Sources


100% [Waiting for headers] [Waiting for headers]
                                                
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers]
                                                                   
Get:9 http://security.ubuntu.com trusty-security/main amd64 Packages [326 kB]


                                                                   
45% [Sources 5,000 kB] [Waiting for headers] [9 Packages 5,126 B/326 kB 2%]
                                                                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources


                                                                           
54% [Sources 5,000 kB] [Waiting for headers] [9 Packages 62.6 kB/326 kB 19%]
                                                                            
Hit http://us.archive.ubuntu.com trusty/universe Sources


                                                                            
66% [Sources 5,000 kB] [9 Packages 127 kB/326 kB 39%]
                                                     
Hit http://us.archive.ubuntu.com trusty/multiverse Sources


84% [Sources 5,000 kB] [9 Packages 234 kB/326 kB 72%]
                                                     
100% [Sources 5,000 kB] [Waiting for headers]
                                             
100% [Sources 5,000 kB] [9 Packages bzip2 0 B] [Waiting for headers]
                                                                    
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages


                                                                    
100% [Sources 5,000 kB] [9 Packages bzip2 0 B] [Waiting for headers] [Waiting f
                                                                               
100% [9 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers]
                                                                       
100% [Sources 22.9 kB] [9 Packages bzip2 0 B] [Waiting for headers] [Waiting fo
                                                                               
100% [9 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers]
                                                                       
100% [Sources 27.9 MB] [9 Packages bzip2 0 B] [Waiting for headers] [Waiting fo
                                                                               
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages


                                                                               
Get:10 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]


100% [Sources 27.9 MB] [9 Packages bzip2 0 B] [10 Packages 8,875 B/8,875 B 100%
100% [Sources 27.9 MB] [9 Packages bzip2 0 B] [Waiting for headers] [Waiting fo
                                                                               
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages


                                                                               
100% [Sources 27.9 MB] [9 Packages bzip2 0 B] [Waiting for headers]
                                                                   
Get:11 http://security.ubuntu.com trusty-security/universe amd64 Packages [112 kB]


                                                                   
98% [Sources 27.9 MB] [9 Packages bzip2 0 B] [Waiting for headers] [11 Packages
                                                                               
100% [Sources 27.9 MB] [9 Packages bzip2 0 B] [Waiting for headers]
                                                                   
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages


                                                                   
100% [Sources 27.9 MB] [9 Packages bzip2 0 B] [Waiting for headers] [Waiting fo
                                                                               
Get:12 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,683 B]


100% [Sources 27.9 MB] [9 Packages bzip2 0 B] [Waiting for headers] [12 Package
100% [Sources 27.9 MB] [9 Packages bzip2 0 B] [Waiting for headers] [Waiting fo
                                                                               
Hit http://us.archive.ubuntu.com trusty/main i386 Packages


100% [Sources 27.9 MB] [9 Packages bzip2 0 B] [Waiting for headers] [Waiting fo
                                                                               
Get:13 http://security.ubuntu.com trusty-security/main i386 Packages [312 kB]


95% [Sources 27.9 MB] [9 Packages bzip2 0 B] [Waiting for headers] [13 Packages
                                                                               
98% [Sources 27.9 MB] [Waiting for headers] [13 Packages 171 kB/312 kB 55%]
                                                                           
98% [Sources 27.9 MB] [10 Packages bzip2 0 B] [Waiting for headers] [13 Package
                                                                               
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages


98% [Sources 27.9 MB] [10 Packages bzip2 0 B] [Waiting for headers] [13 Package
                                                                               
98% [Sources 27.9 MB] [Waiting for headers] [13 Packages 171 kB/312 kB 55%]
                                                                           
98% [Sources 27.9 MB] [11 Packages bzip2 0 B] [Waiting for headers] [13 Package
                                                                               
100% [Sources 27.9 MB] [11 Packages bzip2 0 B] [Waiting for headers]
                                                                    
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers]
                                                                  
100% [Sources 27.9 MB] [12 Packages bzip2 0 B] [Waiting for headers] [Waiting f
                                                                               
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers]
                                                                  
100% [Sources 27.9 MB] [13 Packages bzip2 0 B] [Waiting for headers] [Waiting f
                                                                               
Get:14 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]


100% [Sources 27.9 MB] [13 Packages bzip2 0 B] [Waiting for headers] [14 Packag
100% [Sources 27.9 MB] [13 Packages bzip2 0 B] [Waiting for headers] [Waiting f
                                                                               
Get:15 http://security.ubuntu.com trusty-security/universe i386 Packages [112 kB]


98% [Sources 27.9 MB] [13 Packages bzip2 0 B] [Waiting for headers] [15 Package
                                                                               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages


                                                                               
100% [Sources 27.9 MB] [13 Packages bzip2 0 B] [15 Packages 109 kB/112 kB 97%]
                                                                              
100% [Sources 27.9 MB] [13 Packages bzip2 0 B] [Waiting for headers]
                                                                    
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages


100% [Sources 27.9 MB] [13 Packages bzip2 0 B] [Waiting for headers]
                                                                    
Get:16 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,838 B]


                                                                    
100% [Sources 27.9 MB] [13 Packages bzip2 0 B] [Waiting for headers] [Waiting f
                                                                               
Hit http://security.ubuntu.com trusty-security/main Translation-en


                                                                               
100% [Sources 27.9 MB] [13 Packages bzip2 0 B] [Waiting for headers]
                                                                    
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers]
                                                                  
100% [Sources 27.9 MB] [14 Packages bzip2 0 B] [Waiting for headers] [Waiting f
                                                                               
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers]
                                                                  
100% [Sources 27.9 MB] [15 Packages bzip2 0 B] [Waiting for headers] [Waiting f
                                                                               
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en


                                                                               
100% [Sources 27.9 MB] [15 Packages bzip2 0 B] [Waiting for headers]
                                                                    
Hit http://us.archive.ubuntu.com trusty/main Translation-en


                                                                    
100% [Sources 27.9 MB] [15 Packages bzip2 0 B] [Waiting for headers] [Waiting f
                                                                               
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers]
                                                                  
100% [Sources 27.9 MB] [16 Packages bzip2 0 B] [Waiting for headers] [Waiting f
                                                                               
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers]
                                                                  
Hit http://security.ubuntu.com trusty-security/restricted Translation-en


100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers]
                                                                  
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en


100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers]
                                                                  
Hit http://security.ubuntu.com trusty-security/universe Translation-en


                                                                  
100% [Sources 27.9 MB] [Waiting for headers]
                                            
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en


100% [Sources 27.9 MB] [Waiting for headers]
                                            
Hit http://us.archive.ubuntu.com trusty/universe Translation-en


                                            
100% [Sources 27.9 MB]
                      
100% [Waiting for headers]
                          
100% [Sources 711 kB] [Waiting for headers]
                                           
100% [Waiting for headers]
                          
100% [Packages 8,235 kB] [Waiting for headers]
                                              
Get:17 http://us.archive.ubuntu.com trusty-updates/main Sources [228 kB]


                                              
99% [Packages 8,235 kB] [17 Sources 2,405 B/228 kB 1%]
                                                      
100% [Packages 8,235 kB]
                        
100% [Packages 8,235 kB] [17 Sources bzip2 0 B]
                                               
100% [17 Sources bzip2 0 B] [Waiting for headers]
                                                 
100% [Packages 184 kB] [17 Sources bzip2 0 B] [Waiting for headers]
                                                                   
100% [17 Sources bzip2 0 B] [Waiting for headers]
                                                 
100% [Packages 31.7 MB] [17 Sources bzip2 0 B] [Waiting for headers]
                                                                    
Get:18 http://us.archive.ubuntu.com trusty-updates/restricted Sources [4,717 B]


                                                                    
100% [Packages 31.7 MB] [17 Sources bzip2 0 B] [18 Sources 2,408 B/4,717 B 51%]
                                                                               
100% [Packages 31.7 MB] [17 Sources bzip2 0 B] [Waiting for headers]
                                                                    
100% [Packages 31.7 MB] [Waiting for headers]
                                             
100% [Packages 31.7 MB] [18 Sources bzip2 0 B] [Waiting for headers]
                                                                    
100% [Packages 31.7 MB] [Waiting for headers]
                                             
Get:19 http://us.archive.ubuntu.com trusty-updates/universe Sources [130 kB]


                                             
100% [Packages 31.7 MB] [19 Sources 3,773 B/130 kB 3%]
                                                      
100% [Packages 31.7 MB]
                       
100% [Packages 31.7 MB] [19 Sources bzip2 0 B] [Waiting for headers]
                                                                    
100% [Packages 31.7 MB] [Waiting for headers]
                                             
Get:20 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,138 B]


100% [Packages 31.7 MB] [Waiting for headers]
                                             
100% [Packages 31.7 MB] [20 Sources bzip2 0 B] [Waiting for headers]
                                                                    
100% [Packages 31.7 MB] [Waiting for headers]
                                             
Get:21 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [599 kB]


                                             
99% [Packages 31.7 MB] [21 Packages 3,773 B/599 kB 1%]
                                                      
100% [Packages 31.7 MB]
                       
100% [Packages 31.7 MB] [21 Packages bzip2 0 B]
                                               
Get:22 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.3 kB]


                                               
100% [Packages 31.7 MB] [21 Packages bzip2 0 B] [22 Packages 3,775 B/15.3 kB 25
                                                                               
100% [Packages 31.7 MB] [21 Packages bzip2 0 B] [Waiting for headers]
                                                                     
Get:23 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [301 kB]


                                                                     
99% [Packages 31.7 MB] [21 Packages bzip2 0 B] [23 Packages 6,509 B/301 kB 2%]
                                                                              
100% [Packages 31.7 MB] [21 Packages bzip2 0 B] [Waiting for headers]
                                                                     
Get:24 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]


                                                                     
100% [Packages 31.7 MB] [21 Packages bzip2 0 B] [24 Packages 6,511 B/12.0 kB 54
                                                                               
100% [Packages 31.7 MB] [21 Packages bzip2 0 B] [Waiting for headers]
                                                                     
100% [Packages 31.7 MB] [Waiting for headers]
                                             
100% [Packages 31.7 MB] [22 Packages bzip2 0 B] [Waiting for headers]
                                                                     
100% [Packages 31.7 MB] [Waiting for headers]
                                             
100% [Packages 31.7 MB] [23 Packages bzip2 0 B] [Waiting for headers]
                                                                     
Get:25 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [579 kB]


                                                                     
99% [Packages 31.7 MB] [23 Packages bzip2 0 B] [25 Packages 7,877 B/579 kB 1%]
                                                                              
100% [Packages 31.7 MB] [23 Packages bzip2 0 B] [Waiting for headers]
                                                                     
100% [23 Packages bzip2 0 B] [Waiting for headers]
                                                  
100% [Packages 664 kB] [23 Packages bzip2 0 B] [Waiting for headers]
                                                                    
100% [Packages 664 kB] [Waiting for headers]
                                            
100% [Packages 664 kB] [24 Packages bzip2 0 B] [Waiting for headers]
                                                                    
100% [Packages 664 kB] [Waiting for headers]
                                            
100% [Packages 664 kB] [25 Packages bzip2 0 B] [Waiting for headers]
                                                                    
100% [25 Packages bzip2 0 B] [Waiting for headers]
                                                  
100% [Packages 8,205 kB] [25 Packages bzip2 0 B] [Waiting for headers]
                                                                      
Get:26 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.2 kB]


                                                                      
100% [Packages 8,205 kB] [25 Packages bzip2 0 B] [26 Packages 2,407 B/15.2 kB 1
                                                                               
100% [Packages 8,205 kB] [25 Packages bzip2 0 B] [Waiting for headers]
                                                                      
Get:27 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [303 kB]


                                                                      
100% [Packages 8,205 kB] [25 Packages bzip2 0 B] [27 Packages 5,141 B/303 kB 2%
                                                                               
100% [25 Packages bzip2 0 B] [27 Packages 280 kB/303 kB 92%]
                                                            
100% [Packages 185 kB] [25 Packages bzip2 0 B] [27 Packages 280 kB/303 kB 92%]
                                                                              
100% [Packages 185 kB] [25 Packages bzip2 0 B] [Waiting for headers]
                                                                    
100% [25 Packages bzip2 0 B] [Waiting for headers]
                                                  
100% [Packages 31.7 MB] [25 Packages bzip2 0 B] [Waiting for headers]
                                                                     
100% [Packages 31.7 MB] [Waiting for headers]
                                             
100% [Packages 31.7 MB] [26 Packages bzip2 0 B] [Waiting for headers]
                                                                     
100% [Packages 31.7 MB] [Waiting for headers]
                                             
100% [Packages 31.7 MB] [27 Packages bzip2 0 B] [Waiting for headers]
                                                                     
Get:28 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]


                                                                     
100% [Packages 31.7 MB] [27 Packages bzip2 0 B] [28 Packages 5,143 B/12.1 kB 43
                                                                               
100% [Packages 31.7 MB] [27 Packages bzip2 0 B] [Waiting for headers]
                                                                     
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en


100% [Packages 31.7 MB] [27 Packages bzip2 0 B] [Waiting for headers]
                                                                     
100% [Packages 31.7 MB] [Waiting for headers]
                                             
100% [Packages 31.7 MB] [28 Packages bzip2 0 B] [Waiting for headers]
                                                                     
100% [Packages 31.7 MB] [Waiting for headers]
                                             
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en


100% [Packages 31.7 MB] [Waiting for headers]
                                             
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en


100% [Packages 31.7 MB] [Waiting for headers]
                                             
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en


100% [Packages 31.7 MB] [Waiting for headers]
                                             
Hit http://us.archive.ubuntu.com trusty-backports/main Sources


100% [Packages 31.7 MB] [Waiting for headers]
                                             
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources


100% [Packages 31.7 MB] [Waiting for headers]
                                             
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources


100% [Packages 31.7 MB] [Waiting for headers]
                                             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources


100% [Packages 31.7 MB] [Waiting for headers]
                                             
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages


100% [Packages 31.7 MB] [Waiting for headers]
                                             
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages


                                             
100% [Packages 31.7 MB]
                       
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages


100% [Packages 31.7 MB]
                       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages


100% [Packages 31.7 MB]
                       
100% [Waiting for headers]
                          
100% [Packages 674 kB] [Waiting for headers]
                                            
100% [Waiting for headers]
                          
100% [Translation-en 2,064 kB] [Waiting for headers]
                                                    
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages


                                                    
100% [Translation-en 2,064 kB]
                              
100% [Waiting for headers]
                          
100% [Translation-en 5,770 B] [Waiting for headers]
                                                   
100% [Waiting for headers]
                          
100% [Translation-en 4,149 kB] [Waiting for headers]
                                                    
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages


                                                    
100% [Translation-en 4,149 kB]
                              
100% [Waiting for headers]
                          
100% [Translation-en 15.4 kB] [Waiting for headers]
                                                   
100% [Waiting for headers]
                          
100% [Translation-en 409 kB] [Waiting for headers]
                                                  
100% [Waiting for headers]
                          
100% [Translation-en 332 kB] [Waiting for headers]
                                                  
100% [Waiting for headers]
                          
100% [Translation-en 21.2 kB] [Waiting for headers]
                                                   
100% [Waiting for headers]
                          
100% [Translation-en 18.6 MB] [Waiting for headers]
                                                   
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages


100% [Translation-en 18.6 MB] [Waiting for headers]
                                                   
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages


100% [Translation-en 18.6 MB] [Waiting for headers]
                                                   
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en


100% [Translation-en 18.6 MB] [Waiting for headers]
                                                   
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en


100% [Translation-en 18.6 MB] [Waiting for headers]
                                                   
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en


100% [Translation-en 18.6 MB] [Waiting for headers]
                                                   
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en


100% [Translation-en 18.6 MB] [Waiting for headers]
                                                   
100% [Waiting for headers]
                          
100% [Translation-en 2,875 kB] [Waiting for headers]
                                                    
100% [Waiting for headers]
                          
100% [Translation-en 21.7 kB] [Waiting for headers]
                                                   
100% [Waiting for headers]
                          
100% [Translation-en 30.3 kB] [Waiting for headers]
                                                   
100% [Waiting for headers]
                          
100% [Translation-en 815 kB] [Waiting for headers]
                                                  
100% [Waiting for headers]
                          
100% [Sources 18.3 kB] [Waiting for headers]
                                            
100% [Waiting for headers]
                          
100% [Sources 0 B] [Waiting for headers]
                                        
100% [Waiting for headers]
                          
100% [Sources 111 kB] [Waiting for headers]
                                           
100% [Waiting for headers]
                          
100% [Sources 4,444 B] [Waiting for headers]
                                            
100% [Waiting for headers]
                          
100% [Packages 24.0 kB] [Waiting for headers]
                                             
100% [Waiting for headers]
                          
100% [Packages 0 B] [Waiting for headers]
                                         
100% [Waiting for headers]
                          
100% [Packages 160 kB] [Waiting for headers]
                                            
100% [Waiting for headers]
                          
100% [Packages 3,396 B] [Waiting for headers]
                                             
100% [Waiting for headers]
                          
100% [Packages 23.9 kB] [Waiting for headers]
                                             
100% [Waiting for headers]
                          
100% [Packages 0 B] [Waiting for headers]
                                         
100% [Waiting for headers]
                          
100% [Packages 159 kB] [Waiting for headers]
                                            
100% [Waiting for headers]
                          
100% [Packages 3,341 B] [Waiting for headers]
                                             
100% [Waiting for headers]
                          
100% [Translation-en 12.4 kB] [Waiting for headers]
                                                   
100% [Waiting for headers]
                          
100% [Translation-en 2,242 B] [Waiting for headers]
                                                   
100% [Waiting for headers]
                          
100% [Translation-en 0 B] [Waiting for headers]
                                               
100% [Waiting for headers]
                          
100% [Translation-en 115 kB] [Waiting for headers]
                                                  
100% [Waiting for headers]
                          
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US


100% [Waiting for headers]
                          
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US


                          
100% [Working]
              
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US


100% [Working]
              
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US


100% [Working]
              
Fetched 3,344 kB in 4s (703 kB/s)


Reading package lists... 0%


Reading package lists... 0%


Reading package lists... 1%


Reading package lists... 6%


Reading package lists... 6%


Reading package lists... 6%


Reading package lists... 6%


Reading package lists... 17%


Reading package lists... 30%


Reading package lists... 30%


Reading package lists... 31%


Reading package lists... 31%


Reading package lists... 37%


Reading package lists... 37%


Reading package lists... 37%


Reading package lists... 37%


Reading package lists... 40%


Reading package lists... 61%


Reading package lists... 61%


Reading package lists... 62%


Reading package lists... 62%


Reading package lists... 65%


Reading package lists... 65%


Reading package lists... 65%


Reading package lists... 65%


Reading package lists... 65%


Reading package lists... 65%


Reading package lists... 71%


Reading package lists... 79%


Reading package lists... 79%


Reading package lists... 82%


Reading package lists... 82%


Reading package lists... 82%


Reading package lists... 82%


Reading package lists... 84%


Reading package lists... 84%


Reading package lists... 84%


Reading package lists... 84%


Reading package lists... 87%


Reading package lists... 87%


Reading package lists... 87%


Reading package lists... 87%


Reading package lists... 88%


Reading package lists... 88%


Reading package lists... 88%


Reading package lists... 88%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 91%


Reading package lists... 92%


Reading package lists... 92%


Reading package lists... 93%


Reading package lists... 93%


Reading package lists... 93%


Reading package lists... 93%


Reading package lists... 94%


Reading package lists... 94%


Reading package lists... 94%


Reading package lists... 94%


Reading package lists... 95%


Reading package lists... 95%


Reading package lists... 96%


Reading package lists... 96%


Reading package lists... 96%


Reading package lists... 96%


Reading package lists... 96%


Reading package lists... 96%


Reading package lists... 98%


Reading package lists... 98%


Reading package lists... 98%


Reading package lists... 98%


Reading package lists... 98%


Reading package lists... 98%


Reading package lists... 98%


Reading package lists... 98%


Reading package lists... 99%


Reading package lists... Done


root@:~# apt-get upgrade


Reading package lists... 0%


Reading package lists... 100%


Reading package lists... Done




Building dependency tree... 0%


Building dependency tree... 0%


Building dependency tree... 50%


Building dependency tree... 50%


Building dependency tree       




Reading state information... 0%


Reading state information... 0%


Reading state information... Done


Calculating upgrade... Done
The following packages will be upgraded:
  icedtea-6-jre-cacao icedtea-6-jre-jamvm openjdk-6-jre-headless
  openjdk-6-jre-lib
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 37.6 MB of archives.
After this operation, 28.7 kB of additional disk space will be used.
Do you want to continue? [Y/n] y




0% [Working]
            
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe icedtea-6-jre-cacao amd64 6b36-1.13.8-0ubuntu1~14.04 [333 kB]


            
0% [1 icedtea-6-jre-cacao 0 B/333 kB 0%]
                                        
1% [Working]
            
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe openjdk-6-jre-lib all 6b36-1.13.8-0ubuntu1~14.04 [5,998 kB]


            
1% [2 openjdk-6-jre-lib 0 B/5,998 kB 0%]
                                        
3% [2 openjdk-6-jre-lib 961 kB/5,998 kB 16%]
                                            
8% [2 openjdk-6-jre-lib 2,525 kB/5,998 kB 42%]
                                              
15% [2 openjdk-6-jre-lib 5,492 kB/5,998 kB 92%]
                                               
17% [Working]
             
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe icedtea-6-jre-jamvm amd64 6b36-1.13.8-0ubuntu1~14.04 [399 kB]


             
17% [3 icedtea-6-jre-jamvm 0 B/399 kB 0%]
                                         
18% [Working]
             
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe openjdk-6-jre-headless amd64 6b36-1.13.8-0ubuntu1~14.04 [30.9 MB]


             
18% [4 openjdk-6-jre-headless 0 B/30.9 MB 0%]
                                             
30% [4 openjdk-6-jre-headless 4,681 kB/30.9 MB 15%]
44% [4 openjdk-6-jre-headless 9,892 kB/30.9 MB 32%]
                                                   
58% [4 openjdk-6-jre-headless 15.2 MB/30.9 MB 49%]
72% [4 openjdk-6-jre-headless 20.5 MB/30.9 MB 66%]
86% [4 openjdk-6-jre-headless 25.7 MB/30.9 MB 83%]
                                                  
100% [4 openjdk-6-jre-headless 30.9 MB/30.9 MB 100%]
                                                    
100% [Working]
              
Fetched 37.6 MB in 5s (7,172 kB/s)
(Reading database ... 
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
(Reading database ... 179645 files and directories currently installed.)
Preparing to unpack .../icedtea-6-jre-cacao_6b36-1.13.8-0ubuntu1~14.04_amd64.deb ...
Unpacking icedtea-6-jre-cacao:amd64 (6b36-1.13.8-0ubuntu1~14.04) over (6b35-1.13.7-1ubuntu0.14.04.1) ...
Preparing to unpack .../openjdk-6-jre-lib_6b36-1.13.8-0ubuntu1~14.04_all.deb ...
Unpacking openjdk-6-jre-lib (6b36-1.13.8-0ubuntu1~14.04) over (6b35-1.13.7-1ubuntu0.14.04.1) ...
Preparing to unpack .../icedtea-6-jre-jamvm_6b36-1.13.8-0ubuntu1~14.04_amd64.deb ...
Unpacking icedtea-6-jre-jamvm:amd64 (6b36-1.13.8-0ubuntu1~14.04) over (6b35-1.13.7-1ubuntu0.14.04.1) ...
Preparing to unpack .../openjdk-6-jre-headless_6b36-1.13.8-0ubuntu1~14.04_amd64.deb ...
Unpacking openjdk-6-jre-headless:amd64 (6b36-1.13.8-0ubuntu1~14.04) over (6b35-1.13.7-1ubuntu0.14.04.1) ...
Setting up openjdk-6-jre-headless:amd64 (6b36-1.13.8-0ubuntu1~14.04) ...
Installing new version of config file /etc/java-6-openjdk/security/java.security ...
Setting up openjdk-6-jre-lib (6b36-1.13.8-0ubuntu1~14.04) ...
Setting up icedtea-6-jre-cacao:amd64 (6b36-1.13.8-0ubuntu1~14.04) ...
Setting up icedtea-6-jre-jamvm:amd64 (6b36-1.13.8-0ubuntu1~14.04) ...


root@:~# apt-get distrupgrade
E: Invalid operation distupgrade


root@:~# apt-get distupgrade-upgrade


Reading package lists... 0%


Reading package lists... 100%


Reading package lists... Done




Building dependency tree... 0%


Building dependency tree... 0%


Building dependency tree... 50%


Building dependency tree... 50%


Building dependency tree       




Reading state information... 0%


Reading state information... 0%


Reading state information... Done


Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


root@:~# apt-get -f install


Reading package lists... 0%


Reading package lists... 100%


Reading package lists... Done




Building dependency tree... 0%


Building dependency tree... 0%


Building dependency tree... 50%


Building dependency tree... 50%


Building dependency tree       




Reading state information... 0%


Reading state information... 0%


Reading state information... Done


0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@:~# dpkg -C
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 libjson0:amd64       JSON manipulation library (transitional package)
 libjson0:i386        JSON manipulation library (transitional package)



```

---

### Post by Bashing-om on 2015-08-06
jrg010381; Well !

A lot done that certainly needed doing !
what now results :
```

sudo apt-get install --reinstall libjson0:amd64
sudo apt-get install --reinstall libjson0:i386

```
And while on my mind, how we doing for /boot ?
```

dpkg -l | grep linux-
df -h
df -i

```

[INDENT][INDENT]on the home stretch ?
[/INDENT][/INDENT]

---

### Post by jrg010381 on 2015-08-06
```

root@:~# dpkg -l | grep linux-
ii  linux-cloud-tools-3.13.0-61                           3.13.0-61.100                                       amd64        Linux kernel version specific cloud tools for version 3.13.0-61
ii  linux-cloud-tools-3.13.0-61-generic                   3.13.0-61.100                                       amd64        Linux kernel version specific cloud tools for version 3.13.0-61
ii  linux-cloud-tools-common                              3.13.0-61.100                                       all          Linux kernel version specific cloud tools for version 3.13.0
ii  linux-cloud-tools-virtual                             3.13.0.61.68                                        amd64        This package will always depend on the latest minimal generic kernel cloud tools.
ii  linux-firmware                                        1.127.14                                            all          Firmware for Linux kernel drivers
ii  linux-image-3.16.0-44-generic                         3.16.0-44.59~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-45-generic                         3.16.0-45.60~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-52-generic                          3.2.0-52.78                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-44-generic                   3.16.0-44.59~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-45-generic                   3.16.0-45.60~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-utopic                        3.16.0.45.36                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-61.100                                       amd64        Linux Kernel Headers for development
ii  linux-lts-utopic-tools-3.16.0-31                      3.16.0-31.43~14.04.1                                amd64        Linux kernel version specific tools for version 3.16.0-31
ii  linux-lts-utopic-tools-common                         3.16.0-38.52~14.04.1                                all          Linux kernel version specific tools for version 3.16.0
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  linux-tools-3.16.0-31-generic                         3.16.0-31.43~14.04.1                                amd64        Linux kernel version specific tools for version 3.16.0-31
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

root@:~# df -h
Filesystem                      Size  Used Avail Use% Mounted on
/dev/mapper/-root   38G   14G   22G  39% /
none                            4.0K     0  4.0K   0% /sys/fs/cgroup
udev                            987M  4.0K  987M   1% /dev
tmpfs                           200M  1.6M  198M   1% /run
none                            5.0M     0  5.0M   0% /run/lock
none                            998M  148K  998M   1% /run/shm
none                            100M   40K  100M   1% /run/user
/dev/sda1                       228M   91M  126M  42% /boot

root@:~# df -i
Filesystem                      Inodes  IUsed   IFree IUse% Mounted on
/dev/mapper/-root 2477328 236071 2241257   10% /
none                            255367      2  255365    1% /sys/fs/cgroup
udev                            252594    445  252149    1% /dev
tmpfs                           255367    465  254902    1% /run
none                            255367      7  255360    1% /run/lock
none                            255367      5  255362    1% /run/shm
none                            255367     20  255347    1% /run/user
/dev/sda1                       124496    309  124187    1% /boot

```

---

### Post by Bashing-om on 2015-08-06
jrg010381; WOW;


Did the libjson0 libraries install ? All is now good in that department ?

On to other issue :
> 
ii  linux-image-3.2.0-52-generic

Such and OLD kernel still on the system. What release are you running ?
```

lsb_release -a

```
As the indication:
> 
ii  linux-image-3.16.0-44-generic

says you are running 'utopic (14.10). That release is End_Of_Life and no longer has support . To add to the issue, IF this is 14.10, we must get you up on a supported release -> 15.04 . 

And as we have that old kernel as well as the new kernels, is HardWare Enablement stack a factor on this system ?
```

hwe-support-status --verbose
ls -al /usr/bin/hwe-support-status
hwe-support-status --show-all-unsupported

```

[INDENT][INDENT]are we there, yet 
[/INDENT][/INDENT]

---

### Post by jrg010381 on 2015-08-11
sorry for the delayed response...

```
user@:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
```
```

user@:~$ sudo do-release-upgrade -d
Checking for a new Ubuntu release
No new release found

```

---

### Post by Bashing-om on 2015-08-11
jrg010381; Hey;

For sure you are on 14.04, and most likely HWE is enabled. That will explain the 'utopic' kernels ( now End_of_Life).

The command " sudo do-release-upgrade -d ' will fail. As the '-d' flag directs to install the (D)evelopment release. That would now be 15.10, and 15.10 is not in your upgrade path from 14.04. I do not think that is what you had in mind.

What we need to do is install the currently supported kernel and Xserver stack (vivid).
Is the package manager now stable where we can ?

[INDENT][INDENT]regards
[/INDENT][/INDENT]

---

### Post by jrg010381 on 2015-08-13
I think the package manager is stable. Let's proceed.

---

### Post by Bashing-om on 2015-08-13
jrg010381; K;

Let's do terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg -C

```
To make sure all is up to date, and there are no problems;
IF all runs clean then;
Such that NOW we can install the new kernel, and it's Xserver components:
```

sudo apt-get install linux-generic-lts-vivid libgl1-mesa-glx-lts-vivid xserver-xorg-lts-vivid linux-image-generic-lts-vivid

```

Reboot and tell me what kernel you are now booting :
```

uname -r

```

[INDENT][INDENT]what condition is
[INDENT][INDENT][INDENT]our condition in now
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jrg010381 on 2015-08-14
```

user@:~$ uname -r
3.19.0-25-generic

```

I followed up with 
```

root@:~# apt-get update ; apt-get upgrade
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://us.archive.ubuntu.com trusty InRelease
Hit http://security.ubuntu.com trusty-security Release.gpg
Ign http://us.archive.ubuntu.com trusty-updates InRelease
Hit http://security.ubuntu.com trusty-security Release
Ign http://us.archive.ubuntu.com trusty-backports InRelease
Hit http://us.archive.ubuntu.com trusty Release.gpg
Hit http://security.ubuntu.com trusty-security/main Sources
Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Hit http://security.ubuntu.com trusty-security/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg
Hit http://security.ubuntu.com trusty-security/universe Sources
Hit http://us.archive.ubuntu.com trusty Release
Hit http://security.ubuntu.com trusty-security/multiverse Sources
Get:2 http://us.archive.ubuntu.com trusty-updates Release [63.5 kB]
Hit http://security.ubuntu.com trusty-security/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports Release
Hit http://security.ubuntu.com trusty-security/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Get:3 http://us.archive.ubuntu.com trusty-updates/main Sources [229 kB]
Get:4 http://us.archive.ubuntu.com trusty-updates/restricted Sources [4,717 B]
Get:5 http://us.archive.ubuntu.com trusty-updates/universe Sources [133 kB]
Get:6 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,143 B]
Get:7 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [600 kB]
Get:8 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.3 kB]
Get:9 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [308 kB]
Get:10 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.9 kB]
Get:11 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [580 kB]
Get:12 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.2 kB]
Get:13 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [309 kB]
Get:14 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/main Sources
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Fetched 2,286 kB in 8s (279 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libglamor0 libllvm3.4 libspice-server1 linux-image-3.16.0-44-generic
  linux-image-extra-3.16.0-44-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@:~# apt-get clean
root@:~# apt-get autoclean
Reading package lists... Done
Building dependency tree
Reading state information... Done
root@:~# apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  libglamor0 libllvm3.4 libspice-server1 linux-image-3.16.0-44-generic
  linux-image-extra-3.16.0-44-generic
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 230 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 209782 files and directories currently installed.)
Removing libglamor0:amd64 (0.6.0-0ubuntu4) ...
Removing libllvm3.4:amd64 (1:3.4-1ubuntu3) ...
Removing libspice-server1:amd64 (0.12.4-0nocelt2ubuntu1) ...
Removing linux-image-extra-3.16.0-44-generic (3.16.0-44.59~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-44-generic /boot/vmlinuz-3.16.0-44-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-44-generic /boot/vmlinuz-3.16.0-44-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-44-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-44-generic /boot/vmlinuz-3.16.0-44-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-44-generic /boot/vmlinuz-3.16.0-44-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-44-generic /boot/vmlinuz-3.16.0-44-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.16.0-45-generic
Found initrd image: /boot/initrd.img-3.16.0-45-generic
Found linux image: /boot/vmlinuz-3.16.0-44-generic
Found initrd image: /boot/initrd.img-3.16.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-3.16.0-44-generic (3.16.0-44.59~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-44-generic /boot/vmlinuz-3.16.0-44-generic
update-initramfs: Deleting /boot/initrd.img-3.16.0-44-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-44-generic /boot/vmlinuz-3.16.0-44-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.16.0-45-generic
Found initrd image: /boot/initrd.img-3.16.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...

```

Then I went to install snmpd, but it failed out with the same error

---

### Post by Bashing-om on 2015-08-14
jrg010381: :)

Looks great to me ... all good now ?

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by jrg010381 on 2015-08-16
Well, when I go to install I et the same error message .

```
    root:~# apt-get install snmpdReading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  snmpd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/73.3 kB of archives.
After this operation, 232 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package snmpd.
(Reading database ... 204721 files and directories currently installed.)
Preparing to unpack .../snmpd_5.7.2~dfsg-8.1ubuntu3_amd64.deb ...
Unpacking snmpd (5.7.2~dfsg-8.1ubuntu3) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up snmpd (5.7.2~dfsg-8.1ubuntu3) ...
update-rc.d: warning:  stop runlevel arguments (1) do not match snmpd Default-Stop values (0 1 6)
 * Starting network management services:                                                                                                                             /usr/sbin/snmpd: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
invoke-rc.d: initscript snmpd, action "start" failed.
dpkg: error processing package snmpd (--configure):
 subprocess installed post-installation script returned error exit status 127
Processing triggers for ureadahead (0.100.0-16) ...
Errors were encountered while processing:
 snmpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2015-08-17
jrg010381; Yuk;

The system is advising there is a config file issue:
> 
update-rc.d: warning:  stop runlevel arguments (1) do not match snmpd Default-Stop values (0 1 6)

bk
invoke-rc.d: initscript snmpd, action "start" failed.
dpkg: error processing package snmpd (--configure):
 subprocess installed post-installation script returned error exit status 127



Maybe best to find that control file and see what it says:
looking for it:
```

ls -al /etc/init.d

```
See what versions of snmpd are installed, as opposed to what "should" be:
```

apt-cache show snmpd
apt-cache policy snmpd
dpkg -l snmpd

```

Maybe consider taking a look at the post-installation script .
get to the bottom of this and consider if  'update-rc.d ' will correct the situation.

Small steps, one thing at a time .
[INDENT][INDENT][INDENT]if I knew better
[INDENT][INDENT][INDENT]might do different
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

