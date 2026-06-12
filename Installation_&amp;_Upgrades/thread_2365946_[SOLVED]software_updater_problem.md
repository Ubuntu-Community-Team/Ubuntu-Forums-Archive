---
title: "[SOLVED]software updater problem"
date: 2017-07-12
forum: Installation &amp; Upgrades
---

### Post by Gingalone on 2017-07-12
Just suddenly my laptop Ubuntu 16.04-AMD64 refuses to upgrade (and at the same time the Dropbox client stopped working...):```
sudo apt update
....
Hit:14 http://archive.canonical.com/ubuntu xenial InRelease                              
Hit:16 http://ppa.launchpad.net/videolan/stable-daily/ubuntu xenial InRelease
Ign:17 http://archive.getdeb.net/ubuntu xenial-getdeb InRelease                          
Err:18 http://archive.getdeb.net/ubuntu xenial-getdeb Release
  Connection failed
Reading package lists... Done
E: The repository 'http://archive.getdeb.net/ubuntu xenial-getdeb Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

``` The output of this command took hours
It looks there are some conflict among repositories:
```
cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted
     2	# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted
     3	
     4	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     5	# newer versions of the distribution.
     6	deb http://it.archive.ubuntu.com/ubuntu/ xenial main restricted
     7	# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial main restricted
     8	
     9	## Major bug fix updates produced after the final release of the
    10	## distribution.
    11	deb http://it.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    12	# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    13	
    14	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    15	## team, and may not be under a free licence. Please satisfy yourself as to
    16	## your rights to use the software. Also, please note that software in
    17	## universe WILL NOT receive any review or updates from the Ubuntu security
    18	## team.
    19	deb http://it.archive.ubuntu.com/ubuntu/ xenial universe
    20	# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial universe
    21	deb http://it.archive.ubuntu.com/ubuntu/ xenial-updates universe
    22	# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates universe
    23	
    24	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25	## team, and may not be under a free licence. Please satisfy yourself as to 
    26	## your rights to use the software. Also, please note that software in 
    27	## multiverse WILL NOT receive any review or updates from the Ubuntu
    28	## security team.
    29	deb http://it.archive.ubuntu.com/ubuntu/ xenial multiverse
    30	# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial multiverse
    31	deb http://it.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    32	# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    33	
    34	## N.B. software from this repository may not have been tested as
    35	## extensively as that contained in the main release, although it includes
    36	## newer versions of some applications which may provide useful features.
    37	## Also, please note that software in backports WILL NOT receive any review
    38	## or updates from the Ubuntu security team.
    39	deb http://it.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    40	# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    41	
    42	## Uncomment the following two lines to add software from Canonical's
    43	## 'partner' repository.
    44	## This software is not part of Ubuntu, but is offered by Canonical and the
    45	## respective vendors as a service to Ubuntu users.
    46	# deb http://archive.canonical.com/ubuntu xenial partner
    47	# deb-src http://archive.canonical.com/ubuntu xenial partner
    48	
    49	deb http://security.ubuntu.com/ubuntu xenial-security main restricted
    50	# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
    51	deb http://security.ubuntu.com/ubuntu xenial-security universe
    52	# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
    53	deb http://security.ubuntu.com/ubuntu xenial-security multiverse
    54	# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
    55	
    56	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
    57	# newer versions of the distribution.
    58	# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial main restricted
    59	
    60	## Major bug fix updates produced after the final release of the
    61	## distribution.
    62	# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    63	
    64	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    65	## team, and may not be under a free licence. Please satisfy yourself as to
    66	## your rights to use the software. Also, please note that software in
    67	## universe WILL NOT receive any review or updates from the Ubuntu security
    68	## team.
    69	# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial universe
    70	# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates universe
    71	
    72	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    73	## team, and may not be under a free licence. Please satisfy yourself as to 
    74	## your rights to use the software. Also, please note that software in 
    75	## multiverse WILL NOT receive any review or updates from the Ubuntu
    76	## security team.
    77	# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial multiverse
    78	# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    79	
    80	## N.B. software from this repository may not have been tested as
    81	## extensively as that contained in the main release, although it includes
    82	## newer versions of some applications which may provide useful features.
    83	## Also, please note that software in backports WILL NOT receive any review
    84	## or updates from the Ubuntu security team.
    85	# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    86	
    87	## Uncomment the following two lines to add software from Canonical's
    88	## 'partner' repository.
    89	## This software is not part of Ubuntu, but is offered by Canonical and the
    90	## respective vendors as a service to Ubuntu users.
    91	deb http://archive.canonical.com/ubuntu xenial partner
    92	# deb-src http://archive.canonical.com/ubuntu xenial partner
    93	
    94	# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
    95	# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
    96	# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse

``````
ls -1 /etc/apt/sources.list.d
diesch-ubuntu-testing-xenial.list
diesch-ubuntu-testing-xenial.list.save
dropbox.list
dropbox.list.save
getdeb.list
getdeb.list.save
google-earth.list
google-earth.list.save
osmc-installer.list
osmc-installer.list.save
rebuntu16-ubuntu-avidemux_unofficial-xenial.list
rebuntu16-ubuntu-avidemux_unofficial-xenial.list.save
stefansundin-ubuntu-truecrypt-xenial.list
stefansundin-ubuntu-truecrypt-xenial.list.save
teejee2008-ubuntu-ppa-xenial.list
teejee2008-ubuntu-ppa-xenial.list.save
videolan-ubuntu-stable-daily-xenial.list
videolan-ubuntu-stable-daily-xenial.list.save
```
Thank you for any help

---

### Post by Gingalone on 2017-07-14
The problem was the getdeb repository which was not reachable (down) so, according to [http://www.webupd8.org/2010/05/getdeb-playdeb-repositories-down-what.html](http://www.webupd8.org/2010/05/getdeb-playdeb-repositories-down-what.html) I switched to a mirror and the problem was solved (but not for the [http://download.opensuse.org/repositories/home:/osmc/xUbuntu_16.04/](http://download.opensuse.org/repositories/home:/osmc/xUbuntu_16.04/) /  repository).

---

