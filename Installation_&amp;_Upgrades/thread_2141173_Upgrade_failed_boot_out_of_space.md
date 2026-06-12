---
title: "Upgrade failed /boot out of space"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by 65 mustang on 2013-05-01
Upgrading from 12.10 to 13.04 stoped because /boot ran out of space.  Had too many old kernels that were in there.  I cleaned that up and the system thinks its running 13.04, kernel is the new one, packages are up to date.

But something still thinks the system needs an upgrade because whenever i ssh into it i am presented with:
```
Welcome to Ubuntu 13.04 (GNU/Linux 3.8.0-19-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

New release '13.04' available.
Run 'do-release-upgrade' to upgrade to it.
```
```
do-release-upgrade 
Checking for a new Ubuntu release
No new release found
```
```
root@dalserver:~# uname -a
Linux dalserver 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
root@dalserver:~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring
```

Any ideas?

---

### Post by papibe on 2013-05-01
Hi 65 mustang.

I would start checking the sources. Could you post the result of this command?
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.

---

### Post by 65 mustang on 2013-05-01
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list

     1	# added by the release upgrader
     2	# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427.1)]/ lucid main restricted
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	
     6	deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted
     7	deb-src http://us.archive.ubuntu.com/ubuntu/ raring restricted main multiverse universe #Added by software-properties
     8	
     9	## Major bug fix updates produced after the final release of the
    10	## distribution.
    11	deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
    12	deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates restricted main multiverse universe #Added by software-properties
    13	
    14	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    15	## team. Also, please note that software in universe WILL NOT receive any
    16	## review or updates from the Ubuntu security team.
    17	deb http://us.archive.ubuntu.com/ubuntu/ raring universe
    18	deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe
    19	
    20	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    21	## team, and may not be under a free licence. Please satisfy yourself as to 
    22	## your rights to use the software. Also, please note that software in 
    23	## multiverse WILL NOT receive any review or updates from the Ubuntu
    24	## security team.
    25	deb http://us.archive.ubuntu.com/ubuntu/ raring multiverse
    26	deb http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse
    27	
    28	## Uncomment the following two lines to add software from the 'backports'
    29	## repository.
    30	## N.B. software from this repository may not have been tested as
    31	## extensively as that contained in the main release, although it includes
    32	## newer versions of some applications which may provide useful features.
    33	## Also, please note that software in backports WILL NOT receive any review
    34	## or updates from the Ubuntu security team.
    35	
    36	## Uncomment the following two lines to add software from Canonical's
    37	## 'partner' repository.
    38	## This software is not part of Ubuntu, but is offered by Canonical and the
    39	## respective vendors as a service to Ubuntu users.
    40	
    41	deb http://us.archive.ubuntu.com/ubuntu/ raring-security main restricted
    42	deb-src http://us.archive.ubuntu.com/ubuntu/ raring-security restricted main multiverse universe #Added by software-properties
    43	deb http://us.archive.ubuntu.com/ubuntu/ raring-security universe
    44	deb http://us.archive.ubuntu.com/ubuntu/ raring-security multiverse
    45	deb http://extras.ubuntu.com/ubuntu raring main #Third party developers repository
```

---

### Post by papibe on 2013-05-01
Thanks. They look OK.

What happens when you update and upgrade?

Regards.

---

### Post by 65 mustang on 2013-05-01
```
tsmith@dalserver:~$ sudo apt-get update
[sudo] password for tsmith: 
Hit http://us.archive.ubuntu.com raring Release.gpg
Hit http://us.archive.ubuntu.com raring-updates Release.gpg
Hit http://extras.ubuntu.com raring Release.gpg
Hit http://us.archive.ubuntu.com raring-security Release.gpg
Hit http://us.archive.ubuntu.com raring Release
Hit http://extras.ubuntu.com raring Release
Hit http://us.archive.ubuntu.com raring-updates Release
Hit http://us.archive.ubuntu.com raring-security Release
Hit http://us.archive.ubuntu.com raring/restricted Sources
Hit http://extras.ubuntu.com raring/main amd64 Packages
Hit http://us.archive.ubuntu.com raring/main Sources
Hit http://us.archive.ubuntu.com raring/multiverse Sources
Hit http://extras.ubuntu.com raring/main i386 Packages
Hit http://us.archive.ubuntu.com raring/universe Sources
Hit http://us.archive.ubuntu.com raring/main amd64 Packages
Hit http://us.archive.ubuntu.com raring/restricted amd64 Packages
Hit http://us.archive.ubuntu.com raring/universe amd64 Packages
Hit http://us.archive.ubuntu.com raring/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com raring/main i386 Packages
Hit http://us.archive.ubuntu.com raring/restricted i386 Packages
Hit http://us.archive.ubuntu.com raring/universe i386 Packages
Hit http://us.archive.ubuntu.com raring/multiverse i386 Packages
Hit http://us.archive.ubuntu.com raring/main Translation-en
Hit http://us.archive.ubuntu.com raring/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring/restricted Translation-en
Ign http://extras.ubuntu.com raring/main Translation-en_US
Hit http://us.archive.ubuntu.com raring/universe Translation-en
Ign http://extras.ubuntu.com raring/main Translation-en
Hit http://us.archive.ubuntu.com raring-updates/restricted Sources
Hit http://us.archive.ubuntu.com raring-updates/main Sources
Hit http://us.archive.ubuntu.com raring-updates/multiverse Sources
Hit http://us.archive.ubuntu.com raring-updates/universe Sources
Hit http://us.archive.ubuntu.com raring-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates/main i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/main Translation-en
Hit http://us.archive.ubuntu.com raring-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com raring-updates/universe Translation-en
Hit http://us.archive.ubuntu.com raring-security/restricted Sources
Hit http://us.archive.ubuntu.com raring-security/main Sources
Hit http://us.archive.ubuntu.com raring-security/multiverse Sources
Hit http://us.archive.ubuntu.com raring-security/universe Sources
Hit http://us.archive.ubuntu.com raring-security/main amd64 Packages
Hit http://us.archive.ubuntu.com raring-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com raring-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com raring-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com raring-security/main i386 Packages
Hit http://us.archive.ubuntu.com raring-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com raring-security/universe i386 Packages
Hit http://us.archive.ubuntu.com raring-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com raring-security/main Translation-en
Hit http://us.archive.ubuntu.com raring-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring-security/restricted Translation-en
Hit http://us.archive.ubuntu.com raring-security/universe Translation-en
Ign http://us.archive.ubuntu.com raring/main Translation-en_US
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring-security/main Translation-en_US
Ign http://us.archive.ubuntu.com raring-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring-security/universe Translation-en_US
Reading package lists... Done
tsmith@dalserver:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tsmith@dalserver:~$
```

---

