---
title: "Sub-process /usr/bin/dpkg returned an error code (1) trying to install mariaDB"
date: 2015-11-13
forum: Installation &amp; Upgrades
---

### Post by inesitaferreiracoelho on 2015-11-13
Hi I'm new to ubuntu and I need do install maria db for a school project but no one seems to be capable of helping me with this. I'am using ubuntu 14.04 and installing maria db 10.1-

So this is me trying to resolve the issue that appear when the installation doesn't work properly.

```
inesferreira:~$ sudo apt-get install mariadb-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libdbd-mysql-perl : Depends: libmysqlclient18 (>= 5.5.13-1) but it is not going to be installed
 libmariadbclient18 : Depends: libmysqlclient18 (= 10.1.8+maria-1~trusty) but it is not going to be installed
 mariadb-server : Depends: mariadb-server-10.1 (= 10.1.8+maria-1~trusty) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

```
inesferreira:~$ sudo apt-get install mariadb-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libdbd-mysql-perl : Depends: libmysqlclient18 (>= 5.5.13-1) but it is not going to be installed
 libmariadbclient18 : Depends: libmysqlclient18 (= 10.1.8+maria-1~trusty) but it is not going to be installed
 mariadb-server : Depends: mariadb-server-10.1 (= 10.1.8+maria-1~trusty) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
((((I try to do what the instructions said))))))

```

inesferreira:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  galera-3 libaio1 libdbd-mysql-perl libdbi-perl libjemalloc1
  libmariadbclient18 libmysqlclient18 mariadb-client-10.1
  mariadb-client-core-10.1 mariadb-common mariadb-server-core-10.1
  mysql-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmysqlclient18
The following NEW packages will be installed:
  libmysqlclient18
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
5 not fully installed or removed.
Need to get 0 B/2892 B of archives.
After this operation, 27,6 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: error processing archive /var/cache/apt/archives/libmysqlclient18_10.1.8+maria-1~trusty_amd64.deb (--unpack):
 libmysqlclient18:amd64 10.1.8+maria-1~trusty (Multi-Arch: no) is not co-installable with libmysqlclient18 which has multiple installed instances
Errors were encountered while processing:
 /var/cache/apt/archives/libmysqlclient18_10.1.8+maria-1~trusty_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
inesferreira:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libdbd-mysql-perl : Depends: libmysqlclient18 (>= 5.5.13-1) but it is not installed
 libmariadbclient18 : Depends: libmysqlclient18 (= 10.1.8+maria-1~trusty) but it is not installed
E: Unmet dependencies. Try using -f.
```

```
inesferreira:~$ sudo apt-get -f autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  galera-3 libaio1 libdbd-mysql-perl libdbi-perl libjemalloc1
  libmariadbclient18 mariadb-client-10.1 mariadb-client-core-10.1
  mariadb-common mariadb-server-core-10.1 mysql-common
0 upgraded, 0 newly installed, 11 to remove and 10 not upgraded.
5 not fully installed or removed.
After this operation, 60,7 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 460886 files and directories currently installed.)
Removing mariadb-client-10.1 (10.1.8+maria-1~trusty) ...
Removing libdbd-mysql-perl (4.025-1) ...
Removing mariadb-server-core-10.1 (10.1.8+maria-1~trusty) ...
Removing mariadb-client-core-10.1 (10.1.8+maria-1~trusty) ...
Removing libmariadbclient18 (10.1.8+maria-1~trusty) ...
Removing galera-3 (25.3.9-trusty) ...
Removing libaio1:amd64 (0.3.109-4) ...
Removing libdbi-perl (1.630-1) ...
Removing libjemalloc1 (3.5.1-2) ...
Removing mariadb-common (10.1.8+maria-1~trusty) ...
Removing mysql-common (10.1.8+maria-1~trusty) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
```


 And....I'm totally lost....

---

### Post by Bashing-om on 2015-11-13
inesitaferreiracoelho; Hi !

Edit: And a hearty Welcome to the forum !

My 1st thought from:
> 
 Depends: libmysqlclient18 (>= 5.5.13-1) but it is not going to be installed
libmariadbclient18 : Depends: libmysqlclient18 (= 10.1.8+maria-1~trusty)

is a conflict in sources ??

what returns:
```

apt-cache policy libmysqlclient18 
apt-cahe policy mariadb-server
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
Please post these outputs - Between Code Tags - to maintain formatting and promote readability :
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]so a tale is told
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2015-11-13
Bashing-om is right - you are trying to install MariaDB from a non-Ubuntu source...and by doing so you have introduced a *version conflict* to your system that prevents the package manager from functioning.

Is there some reason you cannot use the perfectly nice, tested, installable version of MariaDB already in the Ubuntu repositories?

---

### Post by inesitaferreiracoelho on 2015-11-16
Thank you for you reply but I follow the instructions on the mariadb website. 
I'm sorry but I don't understand how you are suggesting i may proceed with the installation but please tell me.

---

### Post by inesitaferreiracoelho on 2015-11-16
```
inesferreira:~$ apt-cache policy libmysqlclient18 
libmysqlclient18:
  Installed: (none)
  Candidate: 10.1.8+maria-1~trusty
  Version table:
     10.1.8+maria-1~trusty 0
        500 http://mirrors.fe.up.pt/pub/mariadb/repo/10.1/ubuntu/ trusty/main amd64 Packages
     5.5.46-0ubuntu0.14.04.2 0
        500 http://pt.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     5.5.35+dfsg-1ubuntu1 0
        500 http://pt.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```

```
inesferreira:~$ apt-cache policy mariadb-server
mariadb-server:
  Installed: (none)
  Candidate: 10.1.8+maria-1~trusty
  Version table:
     10.1.8+maria-1~trusty 0
        500 http://mirrors.fe.up.pt/pub/mariadb/repo/10.1/ubuntu/ trusty/main amd64 Packages
     5.5.46-1ubuntu0.14.04.2 0
        500 http://pt.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
     5.5.36-1 0
        500 http://pt.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages

```

```
inesferreira:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://pt.archive.ubuntu.com/ubuntu/ trusty main restricted
     6    deb-src http://pt.archive.ubuntu.com/ubuntu/ trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://pt.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    11    deb-src http://pt.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://pt.archive.ubuntu.com/ubuntu/ trusty universe
    17    deb-src http://pt.archive.ubuntu.com/ubuntu/ trusty universe
    18    deb http://pt.archive.ubuntu.com/ubuntu/ trusty-updates universe
    19    deb-src http://pt.archive.ubuntu.com/ubuntu/ trusty-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://pt.archive.ubuntu.com/ubuntu/ trusty multiverse
    27    deb-src http://pt.archive.ubuntu.com/ubuntu/ trusty multiverse
    28    deb http://pt.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    29    deb-src http://pt.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://pt.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    37    deb-src http://pt.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
    41    deb http://security.ubuntu.com/ubuntu trusty-security universe
    42    deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    43    deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu trusty partner
    51    # deb-src http://archive.canonical.com/ubuntu trusty partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    # deb http://extras.ubuntu.com/ubuntu trusty main
    56    # deb-src http://extras.ubuntu.com/ubuntu trusty main
    57    deb [arch=amd64,i386] http://mirrors.fe.up.pt/pub/mariadb/repo/10.1/ubuntu trusty main
    58    # deb-src [arch=amd64,i386] http://mirrors.fe.up.pt/pub/mariadb/repo/10.1/ubuntu trusty main


```

```
inesferreira:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_jpdbamdb-free-gtk_ubuntu.list <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/jpdbamdb-free-gtk/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_jpdbamdb-free-gtk_ubuntu.list.save <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/jpdbamdb-free-gtk/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_jpdbamdb-full-gtk_ubuntu.list <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/jpdbamdb-full-gtk/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_jpdbamdb-full-gtk_ubuntu.list.save <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/jpdbamdb-full-gtk/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/spotify.list <==

==> /etc/apt/sources.list.d/spotify.list.save <==

==> /etc/apt/sources.list.d/webupd8team-popcorntime-trusty.list <==

==> /etc/apt/sources.list.d/webupd8team-popcorntime-trusty.list.save <==



```


Thank you for your help, if this can shed some light good, because I honestly only grasp like half of it.

---

### Post by inesitaferreiracoelho on 2015-11-16
> **Bashing-om said:**
> inesitaferreiracoelho; Hi !

Edit: And a hearty Welcome to the forum !

My 1st thought from:

is a conflict in sources ??

what returns:
```

apt-cache policy libmysqlclient18 
apt-cahe policy mariadb-server
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
Please post these outputs - Between Code Tags - to maintain formatting and promote readability :
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[INDENT][INDENT]so a tale is told
[/INDENT]
[/INDENT]


apt-cache policy libmysqlclient18

```
inesferreira:~$ apt-cache policy libmysqlclient18 
libmysqlclient18:
  Installed: (none)
  Candidate: 10.1.8+maria-1~trusty
  Version table:
     10.1.8+maria-1~trusty 0
        500 http://mirrors.fe.up.pt/pub/mariadb/repo/10.1/ubuntu/ trusty/main amd64 Packages
     5.5.46-0ubuntu0.14.04.2 0
        500 http://pt.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     5.5.35+dfsg-1ubuntu1 0
        500 http://pt.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```

apt-cache policy mariadb-server

```
inesferreira:~$ apt-cache policy mariadb-server
mariadb-server:
  Installed: (none)
  Candidate: 10.1.8+maria-1~trusty
  Version table:
     10.1.8+maria-1~trusty 0
        500 http://mirrors.fe.up.pt/pub/mariadb/repo/10.1/ubuntu/ trusty/main amd64 Packages
     5.5.46-1ubuntu0.14.04.2 0
        500 http://pt.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
     5.5.36-1 0
        500 http://pt.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages

```

cat -n /etc/apt/sources.list

```
inesferreira:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://pt.archive.ubuntu.com/ubuntu/ trusty main restricted
     6    deb-src http://pt.archive.ubuntu.com/ubuntu/ trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://pt.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    11    deb-src http://pt.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://pt.archive.ubuntu.com/ubuntu/ trusty universe
    17    deb-src http://pt.archive.ubuntu.com/ubuntu/ trusty universe
    18    deb http://pt.archive.ubuntu.com/ubuntu/ trusty-updates universe
    19    deb-src http://pt.archive.ubuntu.com/ubuntu/ trusty-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://pt.archive.ubuntu.com/ubuntu/ trusty multiverse
    27    deb-src http://pt.archive.ubuntu.com/ubuntu/ trusty multiverse
    28    deb http://pt.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    29    deb-src http://pt.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://pt.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    37    deb-src http://pt.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
    41    deb http://security.ubuntu.com/ubuntu trusty-security universe
    42    deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    43    deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu trusty partner
    51    # deb-src http://archive.canonical.com/ubuntu trusty partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    # deb http://extras.ubuntu.com/ubuntu trusty main
    56    # deb-src http://extras.ubuntu.com/ubuntu trusty main
    57    deb [arch=amd64,i386] http://mirrors.fe.up.pt/pub/mariadb/repo/10.1/ubuntu trusty main
    58    # deb-src [arch=amd64,i386] http://mirrors.fe.up.pt/pub/mariadb/repo/10.1/ubuntu trusty main


```

tail -v -n +1 /etc/apt/sources.list.d/*

```
inesferreira:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_jpdbamdb-free-gtk_ubuntu.list <==
deb  https://private-ppa.launchpad.net/commercial-ppa-uploaders/jpdbamdb-free-gtk/ubuntu  trusty main #Added by software-center; credentials stored in  /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_jpdbamdb-free-gtk_ubuntu.list.save <==
deb  https://private-ppa.launchpad.net/commercial-ppa-uploaders/jpdbamdb-free-gtk/ubuntu  trusty main #Added by software-center; credentials stored in  /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_jpdbamdb-full-gtk_ubuntu.list <==
deb  https://private-ppa.launchpad.net/commercial-ppa-uploaders/jpdbamdb-full-gtk/ubuntu  trusty main #Added by software-center; credentials stored in  /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_jpdbamdb-full-gtk_ubuntu.list.save <==
deb  https://private-ppa.launchpad.net/commercial-ppa-uploaders/jpdbamdb-full-gtk/ubuntu  trusty main #Added by software-center; credentials stored in  /etc/apt/auth.conf

==> /etc/apt/sources.list.d/spotify.list <==

==> /etc/apt/sources.list.d/spotify.list.save <==

==> /etc/apt/sources.list.d/webupd8team-popcorntime-trusty.list <==

==> /etc/apt/sources.list.d/webupd8team-popcorntime-trusty.list.save <==



```


Thank you for your help, if this can shed some light good, because I honestly only grasp like half of it.

---

### Post by Bashing-om on 2015-11-16
inesitaferreiracoelho; Oh Boy ! ...

In addition to coping with 3 versions of mariadb-server we have the "proposed" repo active . We can have no idea of what system files may now be elevated with "proposed" active.

All we can do is "try" to fix and see what results.
Presently I am seeking a means to 'ppa-purge' mariadb-server back to what is standard in the repo ( 5.5.35+dfsg-1ubuntu1 0 ).

Is there a reason that the 5.5 version of mariadb-server does not serve your needs ?

[INDENT][INDENT]we may have our work cut out for us
[/INDENT][/INDENT]

---

### Post by inesitaferreiracoelho on 2015-11-17
When I accessed the site saw the 10.1 was the latest stable version and choose only because of that. Honestly what I have to do is so simple that I don&#8217;t see why 5.5 wouldn&#8217;t work.

Thanks again any help is very appreciated because I don&#8217;t have any idea on how to fix it.

---

### Post by ian-weisser on 2015-11-17
1) Eliminate that non-14.04-compatible MariaDB repository that is causing the breakage.
Open System Settings --> Software & Updates
Look for the 'Other Software' tab. Uncheck everything you added for MariaDB.
Look for the 'Updates' tab. Uncheck 'Pre-release Updates (-proposed)'
Close Software & Updates

2) Uninstall and expunge all those non-Ubuntu packages leftover from that non-14.04-compatible MariaDB repository
Open a Terminal and run the following commands
```
sudo apt-get purge mariadb*     ## Uninstall all mariadb packages
sudo apt-get autoremove         ## Uninstall all mariadb package dependencies
sudo apt-get clean              ## Delete the MariaDB packages from your cache (along with all others)
```

3) Install MariaDB from the tested, compatible, safe Ubuntu repositories.
```
sudo apt-get update                     ## Refresh the package database without those non-14.04-compatible sources
sudo apt-get install mariadb-server     ## Install MariaDB from the only choice available, the Ubuntu repos
```

---

### Post by inesitaferreiracoelho on 2015-11-17
> **ian-weisser said:**
> 1) Eliminate that non-14.04-compatible MariaDB repository that is causing the breakage.
Open System Settings --> Software & Updates
Look for the 'Other Software' tab. Uncheck everything you added for MariaDB.
Look for the 'Updates' tab. Uncheck 'Pre-release Updates (-proposed)'
Close Software & Updates

2) Uninstall and expunge all those non-Ubuntu packages leftover from that non-14.04-compatible MariaDB repository
Open a Terminal and run the following commands
```
sudo apt-get purge mariadb*     ## Uninstall all mariadb packages
sudo apt-get autoremove         ## Uninstall all mariadb package dependencies
sudo apt-get clean              ## Delete the MariaDB packages from your cache (along with all others)
```

3) Install MariaDB from the tested, compatible, safe Ubuntu repositories.
```
sudo apt-get update                     ## Refresh the package database without those non-14.04-compatible sources
sudo apt-get install mariadb-server     ## Install MariaDB from the only choice available, the Ubuntu repos
```


It solved the problem!

Thank you so much for all your replies! 
Only one more question , am I supposed to mark this thread as solved ? If so, were?

---

### Post by Bashing-om on 2015-11-17
inesitaferreiracoelho; Great !

Very pleased it was as simple as that to resolve ! .. I was prepared for a fight .
Many thanks to Ian !

It is your responsibility - and your call - to mark the thread solved:
1st post -> thread tools in the drop down :
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

