---
title: "Problems after installing SW on Ubuntu 12.04 64-bit"
date: 2015-08-22
forum: Installation &amp; Upgrades
---

### Post by anton37 on 2015-08-22
After installing mp4joiner, mainly:
```
Add the following line to /etc/apt/sources.list:
deb http://www.deb-multimedia.org sid main
Update the package index:
# sudo apt-get update
Install GPG key of the repository:
# sudo apt-get install deb-multimedia-keyring
Install libwxsvg3 deb package:
# sudo apt-get install libwxsvg3
```
lots of programs were uninstalled.


Upon solving the problem, I stilll have troubles with reinstalling:
1. audacious
```
sudo apt-get install audacious
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 audacious : Depends: libaudcore1 (= 3.2.1-2) but 3.3.99.1-0~webupd8~precise is to be installed
E: Unable to correct problems, you have held broken packages.
```


```
sudo dpkg -i '/home/anton/audacious-plugins_3.4-0~webupd8~precise_amd64.deb' 
Selecting previously unselected package audacious-plugins:amd64.
(Reading database ... 1330657 files and directories currently installed.)
Preparing to unpack .../audacious-plugins_3.4-0~webupd8~precise_amd64.deb ...
Unpacking audacious-plugins:amd64 (3.4-0~webupd8~precise) ...
dpkg: dependency problems prevent configuration of audacious-plugins:amd64:
 audacious-plugins:amd64 depends on libaudcore1 (>= 3.4-0~webupd8~precise); however:
  Version of libaudcore1:amd64 on system is 3.3.99.1-0~webupd8~precise.


dpkg: error processing package audacious-plugins:amd64 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 audacious-plugins:amd64
```


2. nfs-kernel-server
```
sudo apt-get install nfs-kernel-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 nfs-kernel-server : Depends: libtirpc1 but it is not going to be installed
                     Depends: nfs-common (= 1:1.2.5-3ubuntu3.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```


```
sudo apt-get install nfs-common       
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 nfs-common : Depends: libtirpc1 but it is not going to be installed
              Depends: rpcbind (>= 0.2.0-6ubuntu1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```


```
sudo apt-get install rpcbind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 rpcbind : Depends: libtirpc1 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```


3. wine
```
sudo apt-get install wine1.7  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine1.7 : Depends: wine1.7-i386 (= 1:1.7.18-0ubuntu1) but it is not installable
E: Unable to correct problems, you have held broken packages.
```


3. Russian locale
```
locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=ru_RU.UTF-8
LANGUAGE=ru_RU.UTF-8
LC_CTYPE="ru_RU.UTF-8"
LC_NUMERIC="ru_RU.UTF-8"
LC_TIME="ru_RU.UTF-8"
LC_COLLATE="ru_RU.UTF-8"
LC_MONETARY="ru_RU.UTF-8"
LC_MESSAGES="ru_RU.UTF-8"
LC_PAPER="ru_RU.UTF-8"
LC_NAME="ru_RU.UTF-8"
LC_ADDRESS="ru_RU.UTF-8"
LC_TELEPHONE="ru_RU.UTF-8"
LC_MEASUREMENT="ru_RU.UTF-8"
LC_IDENTIFICATION="ru_RU.UTF-8"
LC_ALL=ru_RU.UTF-8
```


```
sudo apt-get install language-pack-ru
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
 language-pack-ru : Depends: language-pack-ru-base (>= 1:12.04+20140106) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```


```
sudo apt-get install language-pack-ru-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
```


```
sudo apt-get install locales
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libc6 : Breaks: locales (< 2.19) but 2.13+git20120306-3 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
 language-pack-ru-base : Depends: locales (>= 2.3.6) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```


```
sudo apt-cache policy libc6 locales
libc6:
  Installed: 2.19-19
  Candidate: 2.19-19
  Version table:
 *** 2.19-19 0
        100 /var/lib/dpkg/status
     2.15-0ubuntu10.12 0
        500 http://ru.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
     2.15-0ubuntu10.11 0
        500 http://ru.archive.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
     2.15-0ubuntu10 0
        500 http://ru.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
locales:
  Installed: (none)
  Candidate: 2.13+git20120306-3
  Version table:
     2.13+git20120306-3 0
        500 http://ru.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
```


```
sudo apt-get purge locales
sudo aptitude install locales
The following NEW packages will be installed:
  locales 
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 3359 kB of archives. After unpacking 9372 kB will be used.
The following packages have unmet dependencies:
 libc6 : Breaks: locales (< 2.19) but 2.13+git20120306-3 is to be installed.
 libc6:i386 : Breaks: locales (< 2.19) but 2.13+git20120306-3 is to be installed.
The following actions will resolve these dependencies:
     Keep the following packages at their current version:
1)     locales [Not Installed]                            
Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
```


```
cat /etc/locale.gen
cat: /etc/locale.gen: No such file or directory
```


```
sudo localectl set "LANG=ru_RU.UTF-8"
sudo: localectl: command not found
```


```
locale -av
locale: C.UTF-8         directory: /usr/lib/locale/C.UTF-8
-------------------------------------------------------------------------------
    title | C locale
    email | aurel32@debian.org
 language | C
 revision | 1.5
     date | 2012-11-18
  codeset | UTF-8
```


```
locale -a
C
C.UTF-8
POSIX
```


```
cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LC_ALL="ru_RU.UTF-8"
```


```
ls /usr/lib/locale
C.UTF-8
```


```
export LC_ALL=ru_RU.UTF-8
bash: warning: setlocale: LC_ALL: cannot change locale (ru_RU.UTF-8)
```


```
sudo locale-gen
sudo: locale-gen: command not found
```


```
localedef -i ru_RU -f UTF-8 ru_RU.UTF-8
character map file `UTF-8' not found: No such file or directory
cannot read character map directory `/usr/share/i18n/charmaps': No such file or directory
```


```
update-locale LC_CTYPE=ru_RU.UTF-8


Creating temporary directory...
Creating copy of GOsa...
Converting .tpl files...
Extracting languages...
Merging po files with existing ones
* merging locale/core/*/LC_MESSAGES/messages.po: touch: cannot touch `locale/core/*/LC_MESSAGES/messages.po': No such file or directory
rm: cannot remove `locale/core/*/LC_MESSAGES/messages.po.tmp': No such file or directory
failed
Copying new po files, making backups...
find: `locale/core/': No such file or directory


There were errors during the transition. Please fix!
```


```
sudo dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "ru_RU.UTF-8",
    LC_ALL = "ru_RU.UTF-8",
    LC_PAPER = "ru_RU.UTF-8",
    LC_ADDRESS = "ru_RU.UTF-8",
    LC_MONETARY = "ru_RU.UTF-8",
    LC_NUMERIC = "ru_RU.UTF-8",
    LC_TELEPHONE = "ru_RU.UTF-8",
    LC_MESSAGES = "ru_RU.UTF-8",
    LC_IDENTIFICATION = "ru_RU.UTF-8",
    LC_COLLATE = "ru_RU.UTF-8",
    LC_MEASUREMENT = "ru_RU.UTF-8",
    LC_CTYPE = "ru_RU.UTF-8",
    LC_TIME = "ru_RU.UTF-8",
    LC_NAME = "ru_RU.UTF-8",
    LANG = "ru_RU.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg-query: package 'locales' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: locales is not installed
```

My source.list:
```
cat -n /etc/apt/sources.list tail -v -n +1 /etc/apt/sources.list.d/*
     1    # deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://ru.archive.ubuntu.com/ubuntu/ precise main restricted multiverse universe
     6    deb-src http://ru.archive.ubuntu.com/ubuntu/ precise main restricted multiverse universe
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://ru.archive.ubuntu.com/ubuntu/ precise-updates main restricted multiverse universe
    11    deb-src http://ru.archive.ubuntu.com/ubuntu/ precise-updates main restricted multiverse universe
    12    
    13    deb http://ru.archive.ubuntu.com/ubuntu/ precise-security main restricted multiverse universe
    14    deb-src http://ru.archive.ubuntu.com/ubuntu/ precise-security main restricted multiverse universe
    15    
    16    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17    ## team. Also, please note that software in universe WILL NOT receive any
    18    ## review or updates from the Ubuntu security team.
    19    
    20    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    21    ## team, and may not be under a free licence. Please satisfy yourself as to 
    22    ## your rights to use the software. Also, please note that software in 
    23    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    24    ## security team.
    25    deb http://ru.archive.ubuntu.com/ubuntu/ precise multiverse
    26    deb-src http://ru.archive.ubuntu.com/ubuntu/ precise multiverse
    27    deb http://ru.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    28    deb-src http://ru.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    29    
    30    ## N.B. software from this repository may not have been tested as
    31    ## extensively as that contained in the main release, although it includes
    32    ## newer versions of some applications which may provide useful features.
    33    ## Also, please note that software in backports WILL NOT receive any review
    34    ## or updates from the Ubuntu security team.
    35    deb http://ru.archive.ubuntu.com/ubuntu/ precise-backports main restricted multiverse universe
    36    deb-src http://ru.archive.ubuntu.com/ubuntu/ precise-backports main restricted multiverse universe
    37    
    38    ## Uncomment the following two lines to add software from Canonical's
    39    ## 'partner' repository.
    40    ## This software is not part of Ubuntu, but is offered by Canonical and the
    41    ## respective vendors as a service to Ubuntu users.
    42    deb http://archive.canonical.com/ubuntu precise partner
    43    deb-src http://archive.canonical.com/ubuntu precise partner
    44    
    45    ## This software is not part of Ubuntu, but is offered by third-party
    46    ## developers who want to ship their latest software.
    47    deb http://extras.ubuntu.com/ubuntu precise main
    48    deb-src http://extras.ubuntu.com/ubuntu precise main
    49    
    50    # Repository for 3.x
    51    # deb http://apt.tvheadend.org/stable precise main
    52    # deb-src http://apt.tvheadend.org/stable precise main
    53    # deb http://apt.tvheadend.org/beta precise main
    54    # deb-src http://apt.tvheadend.org/beta precise main
    55    # deb http://apt.tvheadend.org/unstable precise main
    56    # deb-src http://apt.tvheadend.org/unstable precise main
    57    # Repository for 4.x
    58    # deb https://dl.bintray.com/tvheadend/ubuntu stable main
    59    # deb https://dl.bintray.com/tvheadend/ubuntu testing main
    60    # deb https://dl.bintray.com/tvheadend/ubuntu master main
    61    # deb https://dl.bintray.com/tvheadend/ubuntu unstable main
    62    
    63    #Remastersys Precise
    64    # deb http://www.remastersys.com/ubuntu precise main
    65    deb http://free.nchc.org.tw/drbl-core drbl stable
    66    
    67    deb http://ppa.launchpad.net/network-manager/trunk/ubuntu precise main
    68    deb-src http://ppa.launchpad.net/network-manager/trunk/ubuntu precise main
    69    
    70    #### Audacity - http://audacity.sourceforge.net/
    71    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BB901940
    72    deb http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main
    73    deb-src http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main
    74    
    75    #### Banshee - https://edge.launchpad.net/~banshee-team
    76    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
    77    deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main
    78    deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main
    79    
    80    #### Cairo Composite Manager - http://cairo-compmgr.tuxfamily.org/
    81    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 75198A89
    82    deb http://ppa.launchpad.net/shnatsel/cairo-compmgr/ubuntu precise main
    83    
    84    #### CoreAVC-for-Ubuntu  - http://code.google.com/p/coreavc-for-linux/w/list
    85    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEEB23232
    86    deb http://ppa.launchpad.net/ripps818/coreavc/ubuntu precise main
    87    deb-src http://ppa.launchpad.net/ripps818/coreavc/ubuntu precise main
    88    
    89    #### Daniil's Bash Video Download - http://daniil.it
    90    ## Run this command: wget -q -O - http://dano.cu.cc/1Aci9Qp | sudo apt-key add - && sudo apt-get update
    91    deb http://repo.daniil.it lenny main
    92    
    93    #### DeaDBeeF - http://deadbeef.sourceforge.net/
    94    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3C8E2A7F
    95    deb http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu precise main
    96    deb-src http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu precise main
    97    
    98    #### Dorkfolio Kernel Repository - http://www.dorkfolio.net/
    99    ## Run this command: gpg --keyserver keyserver.ubuntu.com --recv-keys F8274BD4 && sudo gpg --armor --export F8274BD4 | sudo apt-key add -
   100    deb http://packages.dorkfolio.net/ubuntu precise main
   101    deb-src http://packages.dorkfolio.net/ubuntu precise main
   102    
   103    #### FBReader - http://www.fbreader.org/desktop/
   104    ## Run this command: wget http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc -O- | sudo apt-key add -
   105    deb http://www.fbreader.org/desktop/debian stable main
   106    deb-src http://www.fbreader.org/desktop/debian stable main
   107    
   108    #### Flacon - http://kde-apps.org/content/show.php?content=113388
   109    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
   110    deb http://ppa.launchpad.net/flacon/ppa/ubuntu precise main
   111    deb-src http://ppa.launchpad.net/flacon/ppa/ubuntu precise main
   112    
   113    #### GCstar - http://www.gcstar.org/
   114    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5BE6AD9A
   115    deb http://ppa.launchpad.net/gcstar/gcstar-dev/ubuntu precise main
   116    deb-src http://ppa.launchpad.net/gcstar/gcstar-dev/ubuntu precise main
   117    
   118    #### GetDeb - http://www.getdeb.net
   119    ## Run this command: wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
   120    deb http://archive.getdeb.net/ubuntu precise-getdeb apps
   121    
   122    #### Gimp - https://launchpad.net/~otto-kesselgulasch/+archive/gimp
   123    ## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
   124    deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
   125    deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
   126    
   127    #### Glx-Dock / Cairo-Dock - http://www.glx-dock.org
   128    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
   129    deb http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu precise main
   130    deb-src http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu precise main
   131    
   132    #### GNOME3 extra apps - https://launchpad.net/~gnome3-team/+archive/gnome3
   133    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
   134    deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main
   135    
   136    #### Google Linux Software Repositories (Testing) - http://www.google.com/linuxrepositories/
   137    ## Run this command: wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add  -
   138    deb http://dl.google.com/linux/deb/ testing non-free
   139    
   140    #### Gwibber (Daily) - https://launchpad.net/gwibber
   141    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
   142    deb http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu precise main
   143    deb-src http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu precise main
   144    
   145    #### HandBrake Snapshots - http://handbrake.fr/
   146    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 816950D8
   147    deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu precise main
   148    deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu precise main
   149    
   150    #### LibreOffice - http://www.documentfoundation.org/download/
   151    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
   152    deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
   153    deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
   154    
   155    #### MPlayer Daily Builds - https://launchpad.net/~motumedia/+archive/mplayer-daily
   156    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 06438B87
   157    deb http://ppa.launchpad.net/motumedia/mplayer-daily/ubuntu precise main
   158    deb-src http://ppa.launchpad.net/motumedia/mplayer-daily/ubuntu precise main
   159    
   160    #### MKVToolnix - http://www.bunkus.org/videotools/mkvtoolnix/
   161    ## Run this command: wget -q http://www.bunkus.org/gpg-pub-moritzbunkus.txt -O- | sudo apt-key add -
   162    deb http://www.bunkus.org/ubuntu/precise/ ./
   163    deb-src http://www.bunkus.org/ubuntu/precise/ ./
   164    
   165    #### MongoDB - http://www.mongodb.org/
   166    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
   167    deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen
   168    
   169    #### muCommander - http://www.mucommander.com/
   170    ## Run this command: sudo wget -O - http://apt.mucommander.com/apt.key | sudo apt-key add - 
   171    deb http://apt.mucommander.com stable main non-free contrib
   172    
   173    #### OpenShot - http://www.openshotvideo.com
   174    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B9BA26FA
   175    deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu precise main
   176    deb-src http://ppa.launchpad.net/openshot.developers/ppa/ubuntu precise main
   177    
   178    #### Opera - http://www.opera.com/
   179    ## Run this command: sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
   180    deb http://deb.opera.com/opera/ stable non-free
   181    
   182    #### PlayDeb - http://www.playdeb.net/
   183    ## Run this command: wget -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
   184    deb http://archive.getdeb.net/ubuntu precise-getdeb games
   185    
   186    #### PlayOnLinux - http://www.playonlinux.com/en
   187    ## Run this command: wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
   188    deb http://deb.playonlinux.com/ precise main
   189    
   190    #### Plex Media Center - http://www.plexapp.com
   191    ## Run this command: wget -q http://plexapp.com/plex_pub_key.pub -O- | sudo apt-key add -
   192    deb http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo lucid main
   193    
   194    #### SMPlayer2 PPA - https://launchpad.net/~smplayer2/+archive/daily
   195    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3A17F739
   196    deb http://ppa.launchpad.net/smplayer2/daily/ubuntu precise main
   197    deb-src http://ppa.launchpad.net/smplayer2/daily/ubuntu precise main
   198    
   199    #### Tor: anonymity online - http://www.torproject.org/
   200    ## Run this command: gpg --keyserver subkeys.pgp.net --recv 886DDD89 && gpg --export --armor 886DDD89  | sudo apt-key add -
   201    deb http://deb.torproject.org/torproject.org precise main
   202    deb-src http://deb.torproject.org/torproject.org precise main
   203    
   204    #### Ubuntu Tweak - http://ubuntu-tweak.com/
   205    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
   206    deb http://ppa.launchpad.net/tualatrix/ubuntu precise main
   207    deb-src http://ppa.launchpad.net/tualatrix/ubuntu precise main
   208    
   209    #### Unsettings - http://www.florian-diesch.de/software/unsettings/
   210    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0FEB6DD9
   211    deb http://ppa.launchpad.net/diesch/testing/ubuntu precise main
   212    deb-src http://ppa.launchpad.net/diesch/testing/ubuntu precise main
   213    
   214    #### VirtualBox - http://www.virtualbox.org
   215    ## Run this command: wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
   216    deb http://download.virtualbox.org/virtualbox/debian precise contrib
   217    
   218    #### Wine - https://launchpad.net/~ubuntu-wine/+archive/ppa/
   219    ## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
   220    deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
   221    deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
   222    
   223    #### X Updates - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
   224    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
   225    deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
   226    deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
   227    
   228    #### Yuuguu - http://yuuguu.com
   229    deb http://update.yuuguu.com/repositories/apt hardy multiverse
cat: tail: No such file or directory
cat: +1: No such file or directory
   230    deb http://ppa.launchpad.net/ ppa/ppa/ubuntu precise main
   231    deb-src http://ppa.launchpad.net/ ppa/ppa/ubuntu precise main
   232    deb http://ppa.launchpad.net/ ppa/ppa/ubuntu precise main
   233    deb-src http://ppa.launchpad.net/ ppa/ppa/ubuntu precise main
   234    deb http://ppa.launchpad.net/ ppa/ppa/ubuntu precise main
   235    deb-src http://ppa.launchpad.net/ ppa/ppa/ubuntu precise main
   236    # deb http://ppa.launchpad.net/aap/kodi/ubuntu precise main
   237    # deb-src http://ppa.launchpad.net/aap/kodi/ubuntu precise main
   238    # deb http://ppa.launchpad.net/aap/kodi/ubuntu precise main
   239    # deb-src http://ppa.launchpad.net/aap/kodi/ubuntu precise main
   240    # deb http://ppa.launchpad.net/aap/kodi/ubuntu precise main
   241    # deb-src http://ppa.launchpad.net/aap/kodi/ubuntu precise main
   242    # deb http://ppa.launchpad.net/aap/xbmc/ubuntu precise main
   243    # deb-src http://ppa.launchpad.net/aap/xbmc/ubuntu precise main
   244    # deb http://ppa.launchpad.net/aap/xbmc/ubuntu precise main
   245    # deb-src http://ppa.launchpad.net/aap/xbmc/ubuntu precise main
   246    # deb http://ppa.launchpad.net/aap/xbmc/ubuntu precise main
   247    # deb-src http://ppa.launchpad.net/aap/xbmc/ubuntu precise main
   248    deb http://repo.acestream.org/ubuntu/ precise main
   249    deb http://repo.acestream.org/ubuntu/ precise main
   250    deb http://repo.acestream.org/ubuntu/ precise main
   251    # deb http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu oneiric main
   252    # deb-src http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu oneiric main
   253    # deb http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu oneiric main
   254    # deb-src http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu oneiric main
   255    # deb http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu oneiric main
   256    # deb-src http://ppa.launchpad.net/alexandr-surkov/xbmc/ubuntu oneiric main
   257    deb http://ppa.launchpad.net/alexandr-surkov/xbmc-pvr/ubuntu oneiric main
   258    deb-src http://ppa.launchpad.net/alexandr-surkov/xbmc-pvr/ubuntu oneiric main
   259    deb http://ppa.launchpad.net/alexandr-surkov/xbmc-pvr/ubuntu oneiric main
   260    deb-src http://ppa.launchpad.net/alexandr-surkov/xbmc-pvr/ubuntu oneiric main
   261    deb http://ppa.launchpad.net/alexandr-surkov/xbmc-pvr/ubuntu oneiric main
   262    deb-src http://ppa.launchpad.net/alexandr-surkov/xbmc-pvr/ubuntu oneiric main
   263    deb http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu precise main #Banshee daily builds
   264    deb http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu precise main #Banshee daily builds
   265    deb http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu precise main #Banshee daily builds
   266    deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu oneiric main #Banshee Team PPA
   267    deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu oneiric main #Banshee Team PPA
   268    deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu oneiric main #Banshee Team PPA
   269    deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main #Banshee Team PPA
   270    deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main #Banshee Team PPA
   271    deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main #Banshee Team PPA
   272    deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu precise main #Cairo-Dock (Stable) M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   273    deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu precise main #Cairo-Dock (Stable) M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   274    deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu precise main #Cairo-Dock (Stable) M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   275    deb http://ppa.launchpad.net/chris-lea/node.js/ubuntu precise main
   276    deb-src http://ppa.launchpad.net/chris-lea/node.js/ubuntu precise main
   277    deb http://ppa.launchpad.net/chris-lea/node.js/ubuntu precise main
   278    deb-src http://ppa.launchpad.net/chris-lea/node.js/ubuntu precise main
   279    deb http://ppa.launchpad.net/chris-lea/node.js/ubuntu precise main
   280    deb-src http://ppa.launchpad.net/chris-lea/node.js/ubuntu precise main
   281    deb http://ppa.launchpad.net/chromium-daily/stable/ubuntu precise main #Ubuntu Chromium - Stable Channel PPA M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   282    deb http://ppa.launchpad.net/chromium-daily/stable/ubuntu precise main #Ubuntu Chromium - Stable Channel PPA M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   283    deb http://ppa.launchpad.net/chromium-daily/stable/ubuntu precise main #Ubuntu Chromium - Stable Channel PPA M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   284    deb http://ppa.launchpad.net/chromium-daily/stable/ubuntu precise main #Ubuntu Chromium - Stable Channel PPA
   285    deb http://ppa.launchpad.net/chromium-daily/stable/ubuntu precise main #Ubuntu Chromium - Stable Channel PPA
   286    deb http://ppa.launchpad.net/chromium-daily/stable/ubuntu precise main #Ubuntu Chromium - Stable Channel PPA
   287    deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   288    deb-src http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   289    deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   290    deb-src http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   291    deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   292    deb-src http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   293    deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main #Grub Customizer PPA
   294    deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main #Grub Customizer PPA
   295    deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main #Grub Customizer PPA
   296    # deb http://ppa.launchpad.net/ferramroberto/java/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   297    # deb-src http://ppa.launchpad.net/ferramroberto/java/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   298    # deb http://ppa.launchpad.net/ferramroberto/java/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   299    # deb-src http://ppa.launchpad.net/ferramroberto/java/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   300    # deb http://ppa.launchpad.net/ferramroberto/java/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   301    # deb-src http://ppa.launchpad.net/ferramroberto/java/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   302    # deb http://ppa.launchpad.net/flacon/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   303    # deb-src http://ppa.launchpad.net/flacon/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   304    # deb http://ppa.launchpad.net/flacon/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   305    # deb-src http://ppa.launchpad.net/flacon/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   306    # deb http://ppa.launchpad.net/flacon/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   307    # deb-src http://ppa.launchpad.net/flacon/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   308    deb http://ppa.launchpad.net/foobnix-player/foobnix/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   309    deb-src http://ppa.launchpad.net/foobnix-player/foobnix/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   310    deb http://ppa.launchpad.net/foobnix-player/foobnix/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   311    deb-src http://ppa.launchpad.net/foobnix-player/foobnix/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   312    deb http://ppa.launchpad.net/foobnix-player/foobnix/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   313    deb-src http://ppa.launchpad.net/foobnix-player/foobnix/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   314    deb http://ppa.launchpad.net/gcstar/ppa/ubuntu oneiric main
   315    deb-src http://ppa.launchpad.net/gcstar/ppa/ubuntu oneiric main
   316    deb http://ppa.launchpad.net/gcstar/ppa/ubuntu oneiric main
   317    deb-src http://ppa.launchpad.net/gcstar/ppa/ubuntu oneiric main
   318    deb http://ppa.launchpad.net/gcstar/ppa/ubuntu oneiric main
   319    deb-src http://ppa.launchpad.net/gcstar/ppa/ubuntu oneiric main
   320    deb http://ppa.launchpad.net/gnote/ppa/ubuntu precise main #gnote stable
   321    deb http://ppa.launchpad.net/gnote/ppa/ubuntu precise main #gnote stable
   322    deb http://ppa.launchpad.net/gnote/ppa/ubuntu precise main #gnote stable
   323    deb http://dl.google.com/linux/chrome/deb/ stable main #Google Chrome Stable M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   324    deb http://dl.google.com/linux/chrome/deb/ stable main #Google Chrome Stable M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   325    deb http://dl.google.com/linux/chrome/deb/ stable main #Google Chrome Stable M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   326    deb http://ppa.launchpad.net/john.vrbanac/cuckoo/ubuntu precise main
   327    deb-src http://ppa.launchpad.net/john.vrbanac/cuckoo/ubuntu precise main
   328    deb http://ppa.launchpad.net/john.vrbanac/cuckoo/ubuntu precise main
   329    deb-src http://ppa.launchpad.net/john.vrbanac/cuckoo/ubuntu precise main
   330    deb http://ppa.launchpad.net/john.vrbanac/cuckoo/ubuntu precise main
   331    deb-src http://ppa.launchpad.net/john.vrbanac/cuckoo/ubuntu precise main
   332    deb http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
   333    deb-src http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
   334    deb http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
   335    deb-src http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
   336    deb http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
   337    deb-src http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
   338    deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
   339    deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
   340    deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
   341    deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
   342    deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
   343    deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
   344    ## Please report any bug on https://bugs.launchpad.net/medibuntu/
   345    ## Please report any bug on https://bugs.launchpad.net/medibuntu/
   346    ## Please report any bug on https://bugs.launchpad.net/medibuntu/
   347    deb http://ppa.launchpad.net/motumedia/mplayer-daily/ubuntu precise main #MPlayer Daily Builds M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   348    deb http://ppa.launchpad.net/motumedia/mplayer-daily/ubuntu precise main #MPlayer Daily Builds M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   349    deb http://ppa.launchpad.net/motumedia/mplayer-daily/ubuntu precise main #MPlayer Daily Builds M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   350    # deb http://ppa.launchpad.net/mythbuntu/0.25/ubuntu precise main
   351    # deb-src http://ppa.launchpad.net/mythbuntu/0.25/ubuntu precise main
   352    # deb http://ppa.launchpad.net/mythbuntu/0.25/ubuntu precise main
   353    # deb-src http://ppa.launchpad.net/mythbuntu/0.25/ubuntu precise main
   354    # deb http://ppa.launchpad.net/mythbuntu/0.25/ubuntu precise main
   355    # deb-src http://ppa.launchpad.net/mythbuntu/0.25/ubuntu precise main
   356    # deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu precise main
   357    # deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu precise main
   358    # deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu precise main
   359    # deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu precise main
   360    # deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu precise main
   361    # deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu precise main
   362    deb-src http://ppa.launchpad.net/mythbuntu/xmltv/ubuntu precise main
   363    deb http://ppa.launchpad.net/relan/exfat/ubuntu precise main
   364    deb-src http://ppa.launchpad.net/relan/exfat/ubuntu precise main
   365    deb http://ppa.launchpad.net/relan/exfat/ubuntu precise main
   366    deb-src http://ppa.launchpad.net/relan/exfat/ubuntu precise main
   367    deb http://ppa.launchpad.net/relan/exfat/ubuntu precise main
   368    deb-src http://ppa.launchpad.net/relan/exfat/ubuntu precise main
   369    # deb http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   370    # deb-src http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   371    # deb http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   372    # deb-src http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   373    # deb http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   374    # deb-src http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   375    deb http://ppa.launchpad.net/sevenmachines/flash/ubuntu precise main #Adobe Flash (x86-64) M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   376    deb http://ppa.launchpad.net/sevenmachines/flash/ubuntu precise main #Adobe Flash (x86-64) M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   377    deb http://ppa.launchpad.net/sevenmachines/flash/ubuntu precise main #Adobe Flash (x86-64) M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   378    deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   379    deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
   380    deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   381    deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
   382    deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   383    deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
   384    deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
   385    deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
   386    deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
   387    deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
   388    deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
   389    deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
   390    deb http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
   391    deb-src http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
   392    deb http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
   393    deb-src http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
   394    deb http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
   395    deb-src http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
   396    deb http://ppa.launchpad.net/synce/ppa/ubuntu precise main
   397    deb-src http://ppa.launchpad.net/synce/ppa/ubuntu precise main
   398    deb http://ppa.launchpad.net/synce/ppa/ubuntu precise main
   399    deb-src http://ppa.launchpad.net/synce/ppa/ubuntu precise main
   400    deb http://ppa.launchpad.net/synce/ppa/ubuntu precise main
   401    deb-src http://ppa.launchpad.net/synce/ppa/ubuntu precise main
   402    deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   403    deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   404    deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   405    deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   406    deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   407    deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   408    # deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu precise main #XBMC PPA
   409    # deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu precise main #XBMC PPA
   410    # deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu precise main #XBMC PPA
   411    deb http://ppa.launchpad.net/team-xbmc/unstable/ubuntu oneiric main
   412    deb-src http://ppa.launchpad.net/team-xbmc/unstable/ubuntu oneiric main
   413    deb http://ppa.launchpad.net/team-xbmc/unstable/ubuntu oneiric main
   414    deb-src http://ppa.launchpad.net/team-xbmc/unstable/ubuntu oneiric main
   415    deb http://ppa.launchpad.net/team-xbmc/unstable/ubuntu oneiric main
   416    deb-src http://ppa.launchpad.net/team-xbmc/unstable/ubuntu oneiric main
   417    # deb http://ppa.launchpad.net/team-xbmc/unstable/ubuntu precise main
   418    # deb-src http://ppa.launchpad.net/team-xbmc/unstable/ubuntu precise main
   419    # deb http://ppa.launchpad.net/team-xbmc/unstable/ubuntu precise main
   420    # deb-src http://ppa.launchpad.net/team-xbmc/unstable/ubuntu precise main
   421    # deb http://ppa.launchpad.net/team-xbmc/unstable/ubuntu precise main
   422    # deb-src http://ppa.launchpad.net/team-xbmc/unstable/ubuntu precise main
   423    # deb http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu precise main
   424    # deb-src http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu precise main
   425    # deb http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu precise main
   426    # deb-src http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu precise main
   427    # deb http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu precise main
   428    # deb-src http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu precise main
   429    deb http://ppa.launchpad.net/tiheum/equinox/ubuntu precise main #Faenza icon theme
   430    deb http://ppa.launchpad.net/tiheum/equinox/ubuntu precise main #Faenza icon theme
   431    deb http://ppa.launchpad.net/tiheum/equinox/ubuntu precise main #Faenza icon theme
   432    deb http://ppa.launchpad.net/transmissionbt/ppa/ubuntu precise main #Transmission Stable builds
   433    deb http://ppa.launchpad.net/transmissionbt/ppa/ubuntu precise main #Transmission Stable builds
   434    deb http://ppa.launchpad.net/transmissionbt/ppa/ubuntu precise main #Transmission Stable builds
   435    deb http://ppa.launchpad.net/tualatrix/next/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   436    deb-src http://ppa.launchpad.net/tualatrix/next/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   437    deb http://ppa.launchpad.net/tualatrix/next/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   438    deb-src http://ppa.launchpad.net/tualatrix/next/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   439    deb http://ppa.launchpad.net/tualatrix/next/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   440    deb-src http://ppa.launchpad.net/tualatrix/next/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   441    deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu precise main #Ubuntu Tweak Stable PPA
   442    deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu precise main #Ubuntu Tweak Stable PPA
   443    deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu precise main #Ubuntu Tweak Stable PPA
   444    deb http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu precise main #Firefox Aurora Builds Official PPA
   445    deb http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu precise main #Firefox Aurora Builds Official PPA
   446    deb http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu precise main #Firefox Aurora Builds Official PPA
   447    deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   448    deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   449    deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   450    deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   451    deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   452    deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main # M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   453    deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main #Ubuntu Wine Team PPA
   454    deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main #Ubuntu Wine Team PPA
   455    deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main #Ubuntu Wine Team PPA
   456    deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
   457    deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
   458    deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
   459    deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
   460    deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
   461    deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
   462    deb http://ppa.launchpad.net/upubuntu-com/system/ubuntu precise main
   463    deb-src http://ppa.launchpad.net/upubuntu-com/system/ubuntu precise main
   464    deb http://ppa.launchpad.net/upubuntu-com/system/ubuntu precise main
   465    deb-src http://ppa.launchpad.net/upubuntu-com/system/ubuntu precise main
   466    deb http://ppa.launchpad.net/upubuntu-com/system/ubuntu precise main
   467    deb-src http://ppa.launchpad.net/upubuntu-com/system/ubuntu precise main
   468    deb http://download.virtualbox.org/virtualbox/debian precise contrib #VirtualBox Offical Source M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   469    deb http://download.virtualbox.org/virtualbox/debian precise contrib #VirtualBox Offical Source
   470    deb http://download.virtualbox.org/virtualbox/debian precise contrib #VirtualBox Offical Source M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   471    deb http://download.virtualbox.org/virtualbox/debian precise contrib #VirtualBox Offical Source
   472    deb http://download.virtualbox.org/virtualbox/debian precise contrib #VirtualBox Offical Source M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   473    deb http://download.virtualbox.org/virtualbox/debian precise contrib #VirtualBox Offical Source
   474    deb http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu precise main #Weather Indicator PPA M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   475    deb http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu precise main #Weather Indicator PPA M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   476    deb http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu precise main #Weather Indicator PPA M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   477    deb http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu precise main #Weather Indicator PPA
   478    deb http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu precise main #Weather Indicator PPA
   479    deb http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu precise main #Weather Indicator PPA
   480    deb http://ppa.launchpad.net/webupd8team/unstable/ubuntu precise main
   481    deb-src http://ppa.launchpad.net/webupd8team/unstable/ubuntu precise main
   482    deb http://ppa.launchpad.net/webupd8team/unstable/ubuntu precise main
   483    deb-src http://ppa.launchpad.net/webupd8team/unstable/ubuntu precise main
   484    deb http://ppa.launchpad.net/webupd8team/unstable/ubuntu precise main
   485    deb-src http://ppa.launchpad.net/webupd8team/unstable/ubuntu precise main
   486    # deb http://ppa.launchpad.net/wsnipex/xbmc-xvba/ubuntu oneiric main
   487    # deb-src http://ppa.launchpad.net/wsnipex/xbmc-xvba/ubuntu oneiric main
   488    # deb http://ppa.launchpad.net/wsnipex/xbmc-xvba/ubuntu oneiric main
   489    # deb-src http://ppa.launchpad.net/wsnipex/xbmc-xvba/ubuntu oneiric main
   490    # deb http://ppa.launchpad.net/wsnipex/xbmc-xvba/ubuntu oneiric main
   491    # deb-src http://ppa.launchpad.net/wsnipex/xbmc-xvba/ubuntu oneiric main
   492    deb http://repo.yandex.ru/yandex-disk/deb/ stable main
   493    deb http://repo.yandex.ru/yandex-disk/deb/ stable main
   494    deb http://repo.yandex.ru/yandex-disk/deb/ stable main
   495    deb http://ppa.launchpad.net/zeitgeist/ppa/ubuntu precise main
   496    deb-src http://ppa.launchpad.net/zeitgeist/ppa/ubuntu precise main
   497    deb http://ppa.launchpad.net/zeitgeist/ppa/ubuntu precise main
   498    deb-src http://ppa.launchpad.net/zeitgeist/ppa/ubuntu precise main
   499    deb http://ppa.launchpad.net/zeitgeist/ppa/ubuntu precise main
   500    deb-src http://ppa.launchpad.net/zeitgeist/ppa/ubuntu precise main
```

Tried many things, but of no help

---

### Post by TheFu on 2015-08-22
TL;DR.

Have you been updating consistently?  Like every week? Run 
```
sudo apt-get update
sudo apt-get dist-upgrade
```
This will keep dependencies up to date.  If you have been doing this before this problem, I haven't a clue.

I don't know anything about sid or how compatible it is with the Ubuntu you are running. Is it compatible?
[https://unix.stackexchange.com/questions/41407/is-ubuntu-lts-binary-compatible-with-debian](https://unix.stackexchange.com/questions/41407/is-ubuntu-lts-binary-compatible-with-debian) says they are not compatible - use at your own risk and be very careful if too many packages become involved.  I'm afraid you'll need to restore from the backup prior to accepting the first solution.

IMHO, manually installing any .deb file will break a system. If not today, later.  When that is done, it tells APT you know what you are doing and whatever the dependencies are for that manual package install are fine. You know better than APT what is needed. Great if true.  Digging a deeper hole if not true.

Normally, it is best to find an Ubuntu PPA for stuff like this: [http://www.upubuntu.com/2015/01/how-to-joinmerge-multiple-mp4-files.html](http://www.upubuntu.com/2015/01/how-to-joinmerge-multiple-mp4-files.html) is one.

BTW - we've all done stuff like this. 

I've never heard of or used that tool.  Is there another option you would consider like using mkvmerge to combine the files into 1 mkv file?  I know that tool works and there is a PPA for it. No re-encoding needed.

---

### Post by anton37 on 2015-08-23
> Have you been updating consistently? Like every week? Run
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Sure I did this many times, but the problem is still here - no wine, no nfs-kernel-server, no audacious, no Russian locale


> I'm afraid you'll need to restore from the backup prior to accepting the first solution.
Do you mean switching to any old Ubuntu image in grub?
Never raised OS from backups


> IMHO, manually installing any .deb file will break a system
I didn't know that. Thanks


> Normally, it is best to find an Ubuntu PPA for stuff like this: [http://www.upubuntu.com/2015/01/how-...mp4-files.html](http://www.upubuntu.com/2015/01/how-...mp4-files.html) is one.
Of course, I did this, but sudo apt-add-repository ppa:samrog131/ppa cannot be accessed any more.
Following Linux forums I jumped to [http://pkgs.org/debian-sid/multimedia-main-amd64/libwxsvg3_1.5.4-dmo3_amd64.deb.html](http://pkgs.org/debian-sid/multimedia-main-amd64/libwxsvg3_1.5.4-dmo3_amd64.deb.html).
Not knowing that sid must not be used on Ubuntu


> Is there another option you would consider like using mkvmerge to combine the files into 1 mkv file? I know that tool works and there is a PPA for it. No re-encoding needed.
Actually I used kdenlive for merging *.mp4 from my Samsung.
But now with 160 mp4 files kdenlive simply "kills" my PC

---

### Post by TheFu on 2015-08-23
So - does the system "update" cleanly now?

kdenlive is a GUI, correct?  mkvmerge is not. If all the input files have the same vcodec, acodec, resolution, and settings for both codecs, then it will merge them almost as fast as a copy. After the merge into 1 file, you can use ffmpeg to convert from mkv to mp4 containers, if that is really necessary.

If you are any directly installed .deb files, those can be holding other package dependencies. Until removed, the system cannot correct itself.

I doubt going back to an older kernel will help at all. I'm talking about restoring from a backup. Prior to when you started this effort.

Lastly, when it comes to package managers being able to resolve complex dependencies issues, aptitude seems smarter. If you don't like a solution, say "NO" and it will try to provide a different one.  Sometimes there isn't a solution at all, but sometimes there is.

---

### Post by anton37 on 2015-08-23
Thanks, no doubt I'll follow your pieces of advice concerning video merging as soon as I solve OS troubles.

I did everything from here to clean the system:
[http://help.ubuntu.ru/wiki/%D1%80%D0%B5%D1%88%D0%B5%D0%BD%D0%B8%D0%B5_%D0%BF%D1%80%D0%BE%D0%B1%D0%BB%D0%B5%D0%BC_%D1%81_%D0%B7%D0%B0%D0%B2%D0%B8%D1%81%D0%B8%D0%BC%D0%BE%D1%81%D1%82%D1%8F%D0%BC%D0%B8](http://help.ubuntu.ru/wiki/%D1%80%D0%B5%D1%88%D0%B5%D0%BD%D0%B8%D0%B5_%D0%BF%D1%80%D0%BE%D0%B1%D0%BB%D0%B5%D0%BC_%D1%81_%D0%B7%D0%B0%D0%B2%D0%B8%D1%81%D0%B8%D0%BC%D0%BE%D1%81%D1%82%D1%8F%D0%BC%D0%B8)

Anyway the problem is still here.

You said I'd restore OS from backup.
But actually I've never done any backups manually

---

### Post by TheFu on 2015-08-23
> **anton37 said:**
> Thanks, no doubt I'll follow your pieces of advice concerning video merging as soon as I solve OS troubles.

I did everything from here to clean the system:
[http://help.ubuntu.ru/wiki/%D1%80%D0%B5%D1%88%D0%B5%D0%BD%D0%B8%D0%B5_%D0%BF%D1%80%D0%BE%D0%B1%D0%BB%D0%B5%D0%BC_%D1%81_%D0%B7%D0%B0%D0%B2%D0%B8%D1%81%D0%B8%D0%BC%D0%BE%D1%81%D1%82%D1%8F%D0%BC%D0%B8](http://help.ubuntu.ru/wiki/%D1%80%D0%B5%D1%88%D0%B5%D0%BD%D0%B8%D0%B5_%D0%BF%D1%80%D0%BE%D0%B1%D0%BB%D0%B5%D0%BC_%D1%81_%D0%B7%D0%B0%D0%B2%D0%B8%D1%81%D0%B8%D0%BC%D0%BE%D1%81%D1%82%D1%8F%D0%BC%D0%B8)

Anyway the problem is still here.

You said I'd restore OS from backup.
But actually I've never done any backups manually

Sorry, I can't read Russian and my Spanish and German aren't too good either. ;(

The mkvmerge is just another option. I use it a bunch, usually to split files, but sometimes merging.  It is the only tool I know that splits all parts of the files, multiple audio and subtitle and SRT tracks correctly too. Every editor that I've tried only handles 1 audio track and 1 CC track. 

No backups. Ouch.  Sadly, we all have to learn this lesson the hard way. I did too a long time ago.  That lesson got me "backup religion" and now have automatic, daily, versioned, backups for almost all my systems.  Helps me sleep better at night too.

Sorry, but I'm out of ideas. Probably need to step back and copy/paste the update/dist-upgrade outputs (if there are any issues). Then we can work on 1 issue at a time.

---

### Post by anton37 on 2015-08-23
Thank you for your help.

Here you are:

```
bash: warning: setlocale: LC_ALL: cannot change locale (ru_RU.UTF-8)bash: warning: setlocale: LC_ALL: cannot change locale (ru_RU.UTF-8)
bash: warning: setlocale: LC_ALL: cannot change locale (ru_RU.UTF-8)


anton@anton-bung:~$ sudo apt-get clean


anton@anton-bung:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
W: Duplicate sources.list entry http://ru.archive.ubuntu.com/ubuntu/ precise/multiverse amd64 Packages (/var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://ru.archive.ubuntu.com/ubuntu/ precise-updates/multiverse amd64 Packages (/var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/banshee-team/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_banshee-team_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_libreoffice_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/motumedia/mplayer-daily/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_motumedia_mplayer-daily_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://download.virtualbox.org/virtualbox/debian/ precise/contrib amd64 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry http://download.virtualbox.org/virtualbox/debian/ precise/contrib amd64 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/chromium-daily/stable/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_chromium-daily_stable_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_danielrichter2007_grub-customizer_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://download.skype.com/linux/repos/debian/ stable/non-free i386 Packages (/var/lib/apt/lists/download.skype.com_linux_repos_debian_dists_stable_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_weather-indicator-team_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems


anton@anton-bung:~$ sudo apt-get update
Err http://packages.dorkfolio.net precise Release.gpg
  Could not resolve 'packages.dorkfolio.net'
Hit http://ru.archive.ubuntu.com precise Release.gpg                                                                                                
Hit http://ru.archive.ubuntu.com precise-updates Release.gpg                                                                                        
Hit http://ru.archive.ubuntu.com precise-security Release.gpg                                                                                       
Hit http://ru.archive.ubuntu.com precise-backports Release.gpg                                                                                      
Hit http://repo.yandex.ru stable Release.gpg                                                                                                        
Hit http://ru.archive.ubuntu.com precise Release                                                                                                    
Hit http://ru.archive.ubuntu.com precise-updates Release                                                                                            
Hit http://ru.archive.ubuntu.com precise-security Release                                                                                           
Hit http://repo.yandex.ru stable Release                                                                                                            
Hit http://ru.archive.ubuntu.com precise-backports Release                                                                                          
Hit http://ru.archive.ubuntu.com precise/main Sources                                                                                               
Hit http://ru.archive.ubuntu.com precise/restricted Sources                                                                                         
Hit http://ru.archive.ubuntu.com precise/multiverse Sources                                                                                         
Hit http://ru.archive.ubuntu.com precise/universe Sources                                                                                           
Hit http://ru.archive.ubuntu.com precise/main amd64 Packages                                                                                        
Hit http://ru.archive.ubuntu.com precise/restricted amd64 Packages                                                                                  
Hit http://ru.archive.ubuntu.com precise/multiverse amd64 Packages                                                                                  
Hit http://ru.archive.ubuntu.com precise/universe amd64 Packages                                                                                    
Hit http://deb.opera.com stable Release.gpg                                                                                                         
Hit http://repo.acestream.org precise Release.gpg                                                                                                   
Hit http://repo.yandex.ru stable/main amd64 Packages                                                                                                
Ign http://www.bunkus.org ./ Release.gpg                                                                                                            
Hit http://ru.archive.ubuntu.com precise-updates/main Sources                                                                                       
Hit http://ru.archive.ubuntu.com precise-updates/restricted Sources                                                                                 
Hit http://download.virtualbox.org precise Release.gpg                                                                                              
Hit http://ru.archive.ubuntu.com precise-updates/multiverse Sources                                                                                 
Hit http://ru.archive.ubuntu.com precise-updates/universe Sources                                                                                   
Hit http://ru.archive.ubuntu.com precise-updates/main amd64 Packages                                                                                
Hit http://ru.archive.ubuntu.com precise-updates/restricted amd64 Packages                                                                          
Hit http://ru.archive.ubuntu.com precise-updates/multiverse amd64 Packages                                                                          
Hit http://deb.playonlinux.com precise Release.gpg                                                                                                  
Hit http://archive.canonical.com precise Release.gpg                                                                                                
Hit http://ru.archive.ubuntu.com precise-updates/universe amd64 Packages                                                                            
Hit http://ru.archive.ubuntu.com precise-security/main Sources                                                                                      
Hit http://ru.archive.ubuntu.com precise-security/restricted Sources                                                                                
Hit http://apt.mucommander.com stable Release.gpg                                                                                                   
Hit http://ru.archive.ubuntu.com precise-security/multiverse Sources                                                                                
Hit http://ru.archive.ubuntu.com precise-security/universe Sources                                                                                  
Hit http://ru.archive.ubuntu.com precise-security/main amd64 Packages                                                                               
Hit http://ru.archive.ubuntu.com precise-security/restricted amd64 Packages                                                                         
Hit http://ru.archive.ubuntu.com precise-security/multiverse amd64 Packages                                                                         
Hit http://extras.ubuntu.com precise Release.gpg                                                                                                    
Ign http://download.skype.com stable Release.gpg                                                                                                    
Hit http://repo.acestream.org precise Release                                                                                                       
Hit http://ru.archive.ubuntu.com precise-security/universe amd64 Packages                                                                           
Hit http://ru.archive.ubuntu.com precise-backports/main Sources                                                                                     
Hit http://deb.opera.com stable Release                                                                                                             
Ign http://dl.google.com testing Release.gpg                                                                                                        
Ign http://plex.r.worldssl.net lucid Release.gpg                                                                                                    
Hit http://download.virtualbox.org precise Release                                                                                                  
Hit http://dl.google.com stable Release.gpg                                                                                                         
Hit http://ru.archive.ubuntu.com precise-backports/restricted Sources                                                                               
Hit http://ru.archive.ubuntu.com precise-backports/multiverse Sources                                                                               
Hit http://ru.archive.ubuntu.com precise-backports/universe Sources                                                                                 
Hit http://ru.archive.ubuntu.com precise-backports/main amd64 Packages                                                                              
Hit http://ru.archive.ubuntu.com precise-backports/restricted amd64 Packages                                                                        
Hit http://www.bunkus.org ./ Release                                                                                                                
Hit http://ru.archive.ubuntu.com precise-backports/multiverse amd64 Packages                                                                        
Hit http://ru.archive.ubuntu.com precise-backports/universe amd64 Packages                                                                          
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Get:1 http://ppa.launchpad.net precise Release.gpg [316 B]                                                                                          
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://deb.playonlinux.com precise Release                                                                                                      
Hit http://archive.canonical.com precise Release                                                                                                    
Hit http://repo.acestream.org precise/main amd64 Packages                                                                                           
Hit http://apt.mucommander.com stable Release                                                                                                       
Hit http://deb.opera.com stable/non-free amd64 Packages                                                                                             
Ign http://dl.google.com testing Release                                                                                                            
Hit http://extras.ubuntu.com precise Release                                                                                                        
Ign http://plex.r.worldssl.net lucid Release                                                                                                        
Ign http://www.bunkus.org ./ Sources/DiffIndex                                                                                                      
Hit http://download.virtualbox.org precise/contrib amd64 Packages                                                                                   
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Ign http://download.skype.com stable Release                                                                                                        
Hit http://dl.google.com stable Release                                                                                                             
Hit http://deb.playonlinux.com precise/main amd64 Packages                                                                                          
Hit http://archive.canonical.com precise/partner Sources                                                                                            
Ign http://www.bunkus.org ./ Packages/DiffIndex                                                                                                     
Hit http://apt.mucommander.com stable/main amd64 Packages                                                                                           
Hit http://extras.ubuntu.com precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://repo.daniil.it lenny Release.gpg                                                                                                         
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Ign http://ppa.launchpad.net ppa/ppa/ubuntu Release.gpg                                                                                             
Hit http://www.bunkus.org ./ Sources                                                                                                                
Hit http://www.bunkus.org ./ Packages                                                                                                               
Ign http://dl.google.com testing/non-free TranslationIndex                                                                                          
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                                    
Hit http://archive.canonical.com precise/partner amd64 Packages                                                                                     
Hit http://apt.mucommander.com stable/non-free amd64 Packages                                                                                       
Hit http://apt.mucommander.com stable/contrib amd64 Packages                                                                                        
Hit http://extras.ubuntu.com precise/main amd64 Packages                                                                                            
Hit http://dl.google.com stable/main amd64 Packages                                                                                                 
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Get:2 http://update.yuuguu.com hardy Release.gpg [197 B]                                                                                            
Ign http://plex.r.worldssl.net lucid/main TranslationIndex                                                                                          
Hit http://downloads-distro.mongodb.org dist Release.gpg                                                                                            
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Ign http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                    
Hit http://repo.daniil.it lenny Release                                                                                                             
Hit http://update.yuuguu.com hardy Release                                                                                                          
Ign http://update.yuuguu.com hardy Release                                                                                                          
Ign http://ppa.launchpad.net precise Release.gpg                                                                                                    
Ign http://download.skype.com stable/non-free i386 Packages/DiffIndex                                                                               
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Ign http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Ign http://www.bunkus.org ./ Translation-en                                                                                                         
Ign http://download.skype.com stable/non-free TranslationIndex                                                                                      
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Ign http://www.bunkus.org ./ Translation-ru                                                                                                         
Ign http://update.yuuguu.com hardy/multiverse amd64 Packages/DiffIndex                                                                              
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://downloads-distro.mongodb.org dist Release                                                                                                
Hit http://repo.daniil.it lenny/main amd64 Packages                                                                                                 
Hit http://ppa.launchpad.net precise Release                                                                                                        
Ign http://ppa.launchpad.net ppa/ppa/ubuntu Release                                                                                                 
Err http://dl.google.com testing/non-free amd64 Packages                                                                                            
  404  Not Found [IP: 64.233.162.190 80]
Hit http://ppa.launchpad.net oneiric Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net oneiric Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Err http://dl.google.com testing/non-free foreign-architecture Packages                                                                             
  404  Not Found [IP: 64.233.162.190 80]
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://download.skype.com stable/non-free i386 Packages                                                                                         
Err http://dl.google.com testing/non-free i386 Packages                                                                                             
  404  Not Found [IP: 64.233.162.190 80]
Hit http://ppa.launchpad.net oneiric Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Ign http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net oneiric Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Ign http://dl.google.com testing/non-free Translation-en                                                                                            
Get:3 http://deb.torproject.org precise Release.gpg [490 B]                                                                                         
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Ign http://dl.google.com testing/non-free Translation-ru                                                                                            
Hit http://archive.getdeb.net precise-getdeb Release.gpg                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                        
Err http://plex.r.worldssl.net lucid/main amd64 Packages                                                                                            
  404  Not Found
Ign http://update.yuuguu.com hardy/multiverse i386 Packages/DiffIndex                                                                               
Ign http://update.yuuguu.com hardy/multiverse TranslationIndex                                                                                      
Ign http://ppa.launchpad.net precise Release                                                                                                        
Err http://plex.r.worldssl.net lucid/main foreign-architecture Packages                                                                             
  404  Not Found
Err http://plex.r.worldssl.net lucid/main i386 Packages                                                                                             
  404  Not Found
Hit http://downloads-distro.mongodb.org dist/10gen amd64 Packages                                                                                   
Hit http://deb.torproject.org precise Release                                                                                                       
Ign http://deb.torproject.org precise Release                                                                                                       
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                                                                                         
Ign http://ppa.launchpad.net precise/main amd64 Packages/DiffIndex                                                                                  
Ign http://plex.r.worldssl.net lucid/main Translation-en                                                                                            
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex                                                                                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                          
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Ign http://plex.r.worldssl.net lucid/main Translation-ru                                                                                            
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Ign http://deb.torproject.org precise/main Sources/DiffIndex                                                                                        
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://archive.getdeb.net precise-getdeb Release                                                                                                
Ign http://deb.torproject.org precise/main amd64 Packages/DiffIndex                                                                                 
Ign http://deb.torproject.org precise/main i386 Packages/DiffIndex                                                                                  
Ign http://deb.torproject.org precise/main TranslationIndex                                                                                         
Ign http://ppa.launchpad.net ppa/ppa/ubuntu/main TranslationIndex                                                                                   
Ign http://ppa.launchpad.net ppa/ppa/ubuntu/precise TranslationIndex                                                                                
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net oneiric/main Sources                                                                                                   
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                    
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net oneiric/main Sources                                                                                                   
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                          
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://free.nchc.org.tw drbl Release.gpg                                                                                                        
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net oneiric/main Sources                                                                                                   
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                                                                                            
Err http://download.skype.com stable/non-free amd64 Packages                                                                                        
  404  Not Found [IP: 195.12.232.195 80]
Hit http://archive.getdeb.net precise-getdeb/apps amd64 Packages                                                                                    
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Err http://download.skype.com stable/non-free foreign-architecture Packages                                                                         
  404  Not Found [IP: 195.12.232.195 80]
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                          
Hit http://ppa.launchpad.net precise/main Sources                                                                                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                            
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                                             
Ign http://download.skype.com stable/non-free Translation-en                                                                                        
Hit http://archive.getdeb.net precise-getdeb/games amd64 Packages                                                                                   
Hit http://free.nchc.org.tw drbl Release                                                                                                            
Ign http://download.skype.com stable/non-free Translation-ru                                                                            
Hit http://update.yuuguu.com hardy/multiverse amd64 Packages                                                      
Err http://update.yuuguu.com hardy/multiverse foreign-architecture Packages                                                        
  404  Not Found
Hit http://deb.torproject.org precise/main Sources                                                                
Hit http://free.nchc.org.tw drbl/stable amd64 Packages                                                                             
Err http://ppa.launchpad.net precise/main foreign-architecture Packages                                           
  404  Not Found
Hit http://update.yuuguu.com hardy/multiverse i386 Packages                                 
Err http://ppa.launchpad.net ppa/ppa/ubuntu/precise Sources                                                  
  404  Not Found
Err http://ppa.launchpad.net ppa/ppa/ubuntu/main Sources                                    
  404  Not Found
Err http://ppa.launchpad.net ppa/ppa/ubuntu/precise amd64 Packages    
  404  Not Found
Hit http://deb.torproject.org precise/main amd64 Packages             
Err http://deb.torproject.org precise/main foreign-architecture Packages                                      
  404  Not Found [IP: 154.35.132.70 80]
Hit http://deb.torproject.org precise/main i386 Packages                                                      
Err http://ppa.launchpad.net ppa/ppa/ubuntu/main amd64 Packages                                               
  404  Not Found
Err http://ppa.launchpad.net ppa/ppa/ubuntu/precise foreign-architecture Packages           
  404  Not Found
Err http://ppa.launchpad.net ppa/ppa/ubuntu/main foreign-architecture Packages              
  404  Not Found
Err http://ppa.launchpad.net ppa/ppa/ubuntu/precise i386 Packages                           
  404  Not Found
Err http://ppa.launchpad.net ppa/ppa/ubuntu/main i386 Packages        
  404  Not Found
Err http://ppa.launchpad.net precise/main amd64 Packages              
  404  Not Found
Err http://ppa.launchpad.net precise/main foreign-architecture Packages
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages               
  404  Not Found
Err http://ppa.launchpad.net precise/main Sources                     
  404  Not Found
Err http://ppa.launchpad.net precise/main amd64 Packages              
  404  Not Found
Err http://ppa.launchpad.net precise/main foreign-architecture Packages
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages                                     
  404  Not Found
Ign http://ppa.launchpad.net precise/main Translation-en                                    
Ign http://ppa.launchpad.net precise/main Translation-ru              
Ign http://ppa.launchpad.net ppa/ppa/ubuntu/main Translation-en       
Ign http://ppa.launchpad.net ppa/ppa/ubuntu/main Translation-ru       
Ign http://ppa.launchpad.net ppa/ppa/ubuntu/precise Translation-en    
Ign http://ppa.launchpad.net ppa/ppa/ubuntu/precise Translation-ru    
Ign http://update.yuuguu.com hardy/multiverse Translation-en          
Ign http://ppa.launchpad.net precise/main Translation-en              
Ign http://ppa.launchpad.net precise/main Translation-ru              
Ign http://deb.torproject.org precise/main Translation-en                                   
Ign http://ppa.launchpad.net precise/main Translation-en                                    
Ign http://ppa.launchpad.net precise/main Translation-ru              
Ign http://update.yuuguu.com hardy/multiverse Translation-ru          
Ign http://deb.torproject.org precise/main Translation-ru             
Ign http://www.fbreader.org stable Release.gpg                                                                                                      
Ign http://www.fbreader.org stable Release 
Ign http://www.fbreader.org stable/main TranslationIndex
Err http://www.fbreader.org stable/main Sources
  Undetermined Error
Err http://www.fbreader.org stable/main amd64 Packages
  Undetermined Error
Err http://www.fbreader.org stable/main foreign-architecture Packages
  Undetermined Error
Err http://www.fbreader.org stable/main i386 Packages
  Undetermined Error
Ign http://www.fbreader.org stable/main Translation-en
Ign http://www.fbreader.org stable/main Translation-ru
Fetched 1003 B in 6min 42s (2 B/s)
Reading package lists... Done
W: GPG error: http://update.yuuguu.com hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 483881FD2506E8CC
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7778990EEEB23232
W: GPG error: http://deb.torproject.org precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810
W: Failed to fetch http://packages.dorkfolio.net/ubuntu/dists/precise/Release.gpg  Could not resolve 'packages.dorkfolio.net'


W: Failed to fetch http://ru.archive.ubuntu.com/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ru.archive.ubuntu.com/ubuntu/dists/precise-updates/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ru.archive.ubuntu.com/ubuntu/dists/precise-security/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ru.archive.ubuntu.com/ubuntu/dists/precise-backports/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://repo.yandex.ru/yandex-disk/deb/dists/stable/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release  Unable to find expected entry 'non-free/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://repo.acestream.org/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/precise/Release  Unable to find expected entry 'contrib/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://deb.playonlinux.com/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/Release  Unable to find expected entry 'partner/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://apt.mucommander.com/dists/stable/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/network-manager/trunk/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/audacity-team/daily/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/shnatsel/cairo-compmgr/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/flacon/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/gcstar/gcstar-dev/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://dl.google.com/linux/deb/dists/testing/non-free/binary-amd64/Packages  404  Not Found [IP: 64.233.162.190 80]


W: Failed to fetch http://dl.google.com/linux/deb/dists/testing/non-free/binary-foreign-architecture/Packages  404  Not Found [IP: 64.233.162.190 80]


W: Failed to fetch http://dl.google.com/linux/deb/dists/testing/non-free/binary-i386/Packages  404  Not Found [IP: 64.233.162.190 80]


W: Failed to fetch http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo/dists/lucid/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo/dists/lucid/main/binary-foreign-architecture/Packages  404  Not Found


W: Failed to fetch http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo/dists/lucid/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/motumedia/mplayer-daily/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/smplayer2/daily/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/tualatrix/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/diesch/testing/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages  404  Not Found [IP: 195.12.232.195 80]


W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-foreign-architecture/Packages  404  Not Found [IP: 195.12.232.195 80]


W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://repo.daniil.it/dists/lenny/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/alexandr-surkov/xbmc-pvr/ubuntu/dists/oneiric/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/oneiric/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/chris-lea/node.js/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://downloads-distro.mongodb.org/repo/ubuntu-upstart/dists/dist/Release  Unable to find expected entry '10gen/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/foobnix-player/foobnix/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/gcstar/ppa/ubuntu/dists/oneiric/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/gnote/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/john.vrbanac/cuckoo/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/relan/exfat/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/synce/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/team-xbmc/unstable/ubuntu/dists/oneiric/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/tualatrix/next/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/upubuntu-com/system/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/webupd8team/unstable/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://update.yuuguu.com/repositories/apt/dists/hardy/multiverse/binary-foreign-architecture/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/ripps818/coreavc/ubuntu/dists/precise/main/binary-foreign-architecture/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/dists/ppa/ppa/ubuntu/precise/source/Sources  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/dists/ppa/ppa/ubuntu/main/source/Sources  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/dists/ppa/ppa/ubuntu/precise/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/dists/ppa/ppa/ubuntu/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/dists/ppa/ppa/ubuntu/precise/binary-foreign-architecture/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/dists/ppa/ppa/ubuntu/main/binary-foreign-architecture/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/dists/ppa/ppa/ubuntu/precise/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/dists/ppa/ppa/ubuntu/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-foreign-architecture/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/Release  Unable to find expected entry 'apps/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/dists/precise/main/binary-foreign-architecture/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://deb.torproject.org/torproject.org/dists/precise/main/binary-foreign-architecture/Packages  404  Not Found [IP: 154.35.132.70 80]


W: Failed to fetch http://free.nchc.org.tw/drbl-core/dists/drbl/Release  Unable to find expected entry 'stable/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://www.fbreader.org/desktop/debian/dists/stable/main/source/Sources  Undetermined Error


W: Failed to fetch http://www.fbreader.org/desktop/debian/dists/stable/main/binary-amd64/Packages  Undetermined Error


W: Failed to fetch http://www.fbreader.org/desktop/debian/dists/stable/main/binary-foreign-architecture/Packages  Undetermined Error


W: Failed to fetch http://www.fbreader.org/desktop/debian/dists/stable/main/binary-i386/Packages  Undetermined Error


W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry http://ru.archive.ubuntu.com/ubuntu/ precise/multiverse amd64 Packages (/var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://ru.archive.ubuntu.com/ubuntu/ precise-updates/multiverse amd64 Packages (/var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/banshee-team/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_banshee-team_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_libreoffice_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/motumedia/mplayer-daily/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_motumedia_mplayer-daily_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://download.virtualbox.org/virtualbox/debian/ precise/contrib amd64 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry http://download.virtualbox.org/virtualbox/debian/ precise/contrib amd64 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/chromium-daily/stable/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_chromium-daily_stable_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_danielrichter2007_grub-customizer_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://download.skype.com/linux/repos/debian/ stable/non-free i386 Packages (/var/lib/apt/lists/download.skype.com_linux_repos_debian_dists_stable_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_weather-indicator-team_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)


anton@anton-bung:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


anton@anton-bung:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  librtmp0
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 56.8 kB of archives.
After this operation, 17.4 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/alexandr-surkov/xbmc-pvr/ubuntu/ oneiric/main librtmp0 amd64 2.4~git20120222.60218d3-ppa2~oneiric [56.8 kB]
Fetched 56.8 kB in 0s (152 kB/s)    
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "ru_RU.UTF-8",
	LC_ALL = "ru_RU.UTF-8",
	LC_TIME = "ru_RU.UTF-8",
	LC_MONETARY = "ru_RU.UTF-8",
	LC_CTYPE = "ru_RU.UTF-8",
	LC_COLLATE = "ru_RU.UTF-8",
	LC_ADDRESS = "ru_RU.UTF-8",
	LC_TELEPHONE = "ru_RU.UTF-8",
	LC_MESSAGES = "ru_RU.UTF-8",
	LC_NAME = "ru_RU.UTF-8",
	LC_MEASUREMENT = "ru_RU.UTF-8",
	LC_IDENTIFICATION = "ru_RU.UTF-8",
	LC_NUMERIC = "ru_RU.UTF-8",
	LC_PAPER = "ru_RU.UTF-8",
	LANG = "ru_RU.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: error processing archive /var/cache/apt/archives/librtmp0_2.4~git20120222.60218d3-ppa2~oneiric_amd64.deb (--unpack):
 librtmp0:amd64 2.4~git20120222.60218d3-ppa2~oneiric (Multi-Arch: no) is not co-installable with librtmp0 which has multiple installed instances
Errors were encountered while processing:
 /var/cache/apt/archives/librtmp0_2.4~git20120222.60218d3-ppa2~oneiric_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by TheFu on 2015-08-23
First - remove all the duplicate sources in the APT settings.  They are in /etc/apt/ somewhere. Check sources.list and sources.list.d/.

Don't move forward until all those warnings are gone from the "update" cmd.  Basically, fix the first error and move to the next. Stay with the current command, running it over and over until all the errors and warnings are corrected.

---

### Post by anton37 on 2015-08-23
A bit messed up with finding duplacates.

```
W: Duplicate sources.list entry http://ru.archive.ubuntu.com/ubuntu/ precise/multiverse amd64 Packages (/var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages)
```

In sources.list there're some entries which look like this:
```
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to     4    # newer versions of the distribution.
     5    deb http://ru.archive.ubuntu.com/ubuntu/ precise main restricted multiverse universe
     6    deb-src http://ru.archive.ubuntu.com/ubuntu/ precise main restricted multiverse universe
```

and 
```
    20    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu     
21    ## team, and may not be under a free licence. Please satisfy yourself as to 
    22    ## your rights to use the software. Also, please note that software in 
    23    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    24    ## security team.
    25    deb http://ru.archive.ubuntu.com/ubuntu/ precise multiverse
    26    deb-src http://ru.archive.ubuntu.com/ubuntu/ precise multiverse
```

In /var/lib/apt/lists/ I see only one file:
ru.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages

What should be deleted?

---

### Post by anton37 on 2015-08-23
I cleaned some duplicates (but not all) in sources.list using:
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

Then

```
bash: warning: setlocale: LC_ALL: cannot change locale (ru_RU.UTF-8)bash: warning: setlocale: LC_ALL: cannot change locale (ru_RU.UTF-8)
bash: warning: setlocale: LC_ALL: cannot change locale (ru_RU.UTF-8)
anton@anton-bung:~$ sudo apt-get clean 
```

```
anton@anton-bung:~$ sudo apt-get autoremoveReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Duplicate sources.list entry http://ppa.launchpad.net/banshee-team/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_banshee-team_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_libreoffice_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://download.virtualbox.org/virtualbox/debian/ precise/contrib amd64 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry http://download.virtualbox.org/virtualbox/debian/ precise/contrib amd64 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://download.skype.com/linux/repos/debian/ stable/non-free i386 Packages (/var/lib/apt/lists/download.skype.com_linux_repos_debian_dists_stable_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

Can't figure out what is to be removed.

In \var\lib\apt\lists I have
```
download.skype.com_linux_repos_debian_dists_stable_non-free_binary-i386_Packages

download.virtualbox.org_virtualbox_debian_dists_precise_Release
download.virtualbox.org_virtualbox_debian_dists_precise_Release.gpg
download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages


ppa.launchpad.net_banshee-team_banshee-daily_ubuntu_dists_precise_Release
ppa.launchpad.net_banshee-team_banshee-daily_ubuntu_dists_precise_Release.gpg
ppa.launchpad.net_banshee-team_banshee-daily_ubuntu_dists_precise_main_binary-amd64_Packages
ppa.launchpad.net_banshee-team_ppa_ubuntu_dists_precise_Release
ppa.launchpad.net_banshee-team_ppa_ubuntu_dists_precise_Release.gpg
ppa.launchpad.net_banshee-team_ppa_ubuntu_dists_precise_main_binary-amd64_Packages
ppa.launchpad.net_banshee-team_ppa_ubuntu_dists_precise_main_source_Sources


ppa.launchpad.net_libreoffice_libreoffice-4-0_ubuntu_dists_precise_Release
ppa.launchpad.net_libreoffice_libreoffice-4-0_ubuntu_dists_precise_Release.gpg
ppa.launchpad.net_libreoffice_libreoffice-4-0_ubuntu_dists_precise_main_binary-amd64_Packages
ppa.launchpad.net_libreoffice_libreoffice-4-0_ubuntu_dists_precise_main_source_Sources
ppa.launchpad.net_libreoffice_ppa_ubuntu_dists_precise_Release
ppa.launchpad.net_libreoffice_ppa_ubuntu_dists_precise_Release.gpg
ppa.launchpad.net_libreoffice_ppa_ubuntu_dists_precise_main_binary-amd64_Packages
ppa.launchpad.net_libreoffice_ppa_ubuntu_dists_precise_main_source_Sources


ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_Release
ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_Release.gpg
ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_main_binary-amd64_Packages
ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_main_source_Sources


ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_Release
ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_Release.gpg
ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_main_binary-amd64_Packages
ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_main_source_Sources
```

In etc\apt\sources.list.d:
```
skype.list
skype.list.distUpgrade
skype.list.save


virtualbox-offical-source.list
virtualbox-offical-source.list.distUpgrade
virtualbox-offical-source.list.save


banshee-team-banshee-daily-precise.list
banshee-team-banshee-daily-precise.list.distUpgrade
banshee-team-banshee-daily-precise.list.save
banshee-team-ppa-precise.list
banshee-team-ppa-precise.list.distUpgrade
banshee-team-ppa-precise.list.save


libreoffice-libreoffice-4-0-precise.list
libreoffice-libreoffice-4-0-precise.list.distUpgrade
libreoffice-libreoffice-4-0-precise.list.save
libreoffice-ppa-precise.list
libreoffice-ppa-precise.list.distUpgrade
libreoffice-ppa-precise.list.save


ubuntu-wine-ppa-precise.list
ubuntu-wine-ppa-precise.list.distUpgrade
ubuntu-wine-ppa-precise.list.save


ubuntu-x-swat-x-updates-precise.list
ubuntu-x-swat-x-updates-precise.list.distUpgrade
ubuntu-x-swat-x-updates-precise.list.save

```

Sources:
```
anton@anton-bung:~$ cat -n /etc/apt/sources.list tail -v -n +1 /etc/apt/sources.list.d/*     1    ###### Ubuntu Main Repos
     2    deb http://ru.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 
     3    deb-src http://ru.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 
     4    
     5    ###### Ubuntu Update Repos
     6    deb http://ru.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
     7    deb http://ru.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
     8    deb http://ru.archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
     9    deb http://ru.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 
    10    deb-src http://ru.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
    11    deb-src http://ru.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
    12    deb-src http://ru.archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
    13    deb-src http://ru.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 
    14    
    15    ###### Ubuntu Partner Repo
    16    deb http://archive.canonical.com/ubuntu precise partner
    17    deb-src http://archive.canonical.com/ubuntu precise partner
    18    
    19    ###### Ubuntu Extras Repo
    20    deb http://extras.ubuntu.com/ubuntu precise main
    21    deb-src http://extras.ubuntu.com/ubuntu precise main
    22    
    23    # Repository for 3.x
    24    # deb http://apt.tvheadend.org/stable precise main
    25    # deb-src http://apt.tvheadend.org/stable precise main
    26    # deb http://apt.tvheadend.org/beta precise main
    27    # deb-src http://apt.tvheadend.org/beta precise main
    28    # deb http://apt.tvheadend.org/unstable precise main
    29    # deb-src http://apt.tvheadend.org/unstable precise main
    30    # Repository for 4.x
    31    # deb https://dl.bintray.com/tvheadend/ubuntu stable main
    32    # deb https://dl.bintray.com/tvheadend/ubuntu testing main
    33    # deb https://dl.bintray.com/tvheadend/ubuntu master main
    34    # deb https://dl.bintray.com/tvheadend/ubuntu unstable main
    35    
    36    #Remastersys Precise
    37    # deb http://www.remastersys.com/ubuntu precise main
    38    deb http://free.nchc.org.tw/drbl-core drbl stable
    39    
    40    deb http://ppa.launchpad.net/network-manager/trunk/ubuntu precise main
    41    deb-src http://ppa.launchpad.net/network-manager/trunk/ubuntu precise main
    42    
    43    #### Audacity - http://audacity.sourceforge.net/
    44    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BB901940
    45    deb http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main
    46    deb-src http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main
    47    
    48    #### Banshee - https://edge.launchpad.net/~banshee-team
    49    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
    50    deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main
    51    deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main
    52    
    53    #### Cairo Composite Manager - http://cairo-compmgr.tuxfamily.org/
    54    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 75198A89
    55    deb http://ppa.launchpad.net/shnatsel/cairo-compmgr/ubuntu precise main
    56    
    57    #### CoreAVC-for-Ubuntu  - http://code.google.com/p/coreavc-for-linux/w/list
    58    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEEB23232
    59    deb http://ppa.launchpad.net/ripps818/coreavc/ubuntu precise main
    60    deb-src http://ppa.launchpad.net/ripps818/coreavc/ubuntu precise main
    61    
    62    #### Daniil's Bash Video Download - http://daniil.it
    63    ## Run this command: wget -q -O - http://dano.cu.cc/1Aci9Qp | sudo apt-key add - && sudo apt-get update
    64    deb http://repo.daniil.it lenny main
    65    
    66    #### DeaDBeeF - http://deadbeef.sourceforge.net/
    67    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3C8E2A7F
    68    deb http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu precise main
    69    deb-src http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu precise main
    70    
    71    #### Dorkfolio Kernel Repository - http://www.dorkfolio.net/
    72    ## Run this command: gpg --keyserver keyserver.ubuntu.com --recv-keys F8274BD4 && sudo gpg --armor --export F8274BD4 | sudo apt-key add -
    73    deb http://packages.dorkfolio.net/ubuntu precise main
    74    deb-src http://packages.dorkfolio.net/ubuntu precise main
    75    
    76    #### Flacon - http://kde-apps.org/content/show.php?content=113388
    77    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
    78    deb http://ppa.launchpad.net/flacon/ppa/ubuntu precise main
    79    deb-src http://ppa.launchpad.net/flacon/ppa/ubuntu precise main
    80    
    81    #### GCstar - http://www.gcstar.org/
    82    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5BE6AD9A
    83    deb http://ppa.launchpad.net/gcstar/gcstar-dev/ubuntu precise main
    84    deb-src http://ppa.launchpad.net/gcstar/gcstar-dev/ubuntu precise main
    85    
    86    #### GetDeb - http://www.getdeb.net
    87    ## Run this command: wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
    88    deb http://archive.getdeb.net/ubuntu precise-getdeb apps
    89    
    90    #### Gimp - https://launchpad.net/~otto-kesselgulasch/+archive/gimp
    91    ## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
    92    deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
    93    deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
    94    
    95    #### Glx-Dock / Cairo-Dock - http://www.glx-dock.org
    96    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
    97    deb http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu precise main
    98    deb-src http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu precise main
    99    
   100    #### GNOME3 extra apps - https://launchpad.net/~gnome3-team/+archive/gnome3
   101    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
   102    deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main
   103    
   104    #### Google Linux Software Repositories (Testing) - http://www.google.com/linuxrepositories/
   105    ## Run this command: wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add  -
   106    deb http://dl.google.com/linux/deb/ testing non-free
   107    
   108    #### Gwibber (Daily) - https://launchpad.net/gwibber
   109    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
   110    deb http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu precise main
   111    deb-src http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu precise main
   112    
   113    #### HandBrake Snapshots - http://handbrake.fr/
   114    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 816950D8
   115    deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu precise main
   116    deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu precise main
   117    
   118    #### LibreOffice - http://www.documentfoundation.org/download/
   119    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
   120    deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
   121    deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
   122    
   123    #### MPlayer Daily Builds - https://launchpad.net/~motumedia/+archive/mplayer-daily
   124    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 06438B87
   125    deb http://ppa.launchpad.net/motumedia/mplayer-daily/ubuntu precise main
   126    deb-src http://ppa.launchpad.net/motumedia/mplayer-daily/ubuntu precise main
   127    
   128    #### MKVToolnix - http://www.bunkus.org/videotools/mkvtoolnix/
   129    ## Run this command: wget -q http://www.bunkus.org/gpg-pub-moritzbunkus.txt -O- | sudo apt-key add -
   130    deb http://www.bunkus.org/ubuntu/precise/ ./
   131    deb-src http://www.bunkus.org/ubuntu/precise/ ./
   132    
   133    #### MongoDB - http://www.mongodb.org/
   134    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
   135    deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen
   136    
   137    #### muCommander - http://www.mucommander.com/
   138    ## Run this command: sudo wget -O - http://apt.mucommander.com/apt.key | sudo apt-key add - 
   139    deb http://apt.mucommander.com stable main non-free contrib
   140    
   141    #### OpenShot - http://www.openshotvideo.com
   142    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B9BA26FA
   143    deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu precise main
   144    deb-src http://ppa.launchpad.net/openshot.developers/ppa/ubuntu precise main
   145    
   146    #### Opera - http://www.opera.com/
   147    ## Run this command: sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
   148    deb http://deb.opera.com/opera/ stable non-free
   149    
   150    #### PlayDeb - http://www.playdeb.net/
   151    ## Run this command: wget -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
   152    deb http://archive.getdeb.net/ubuntu precise-getdeb games
   153    
   154    #### PlayOnLinux - http://www.playonlinux.com/en
   155    ## Run this command: wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
   156    deb http://deb.playonlinux.com/ precise main
   157    
   158    #### SMPlayer2 PPA - https://launchpad.net/~smplayer2/+archive/daily
   159    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3A17F739
   160    deb http://ppa.launchpad.net/smplayer2/daily/ubuntu precise main
   161    deb-src http://ppa.launchpad.net/smplayer2/daily/ubuntu precise main
   162    
   163    #### Tor: anonymity online - http://www.torproject.org/
   164    ## Run this command: gpg --keyserver subkeys.pgp.net --recv 886DDD89 && gpg --export --armor 886DDD89  | sudo apt-key add -
   165    deb http://deb.torproject.org/torproject.org precise main
   166    deb-src http://deb.torproject.org/torproject.org precise main
   167    
   168    #### Ubuntu Tweak - http://ubuntu-tweak.com/
   169    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
   170    deb http://ppa.launchpad.net/tualatrix/ubuntu precise main
   171    deb-src http://ppa.launchpad.net/tualatrix/ubuntu precise main
   172    
   173    #### Unsettings - http://www.florian-diesch.de/software/unsettings/
   174    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0FEB6DD9
   175    deb http://ppa.launchpad.net/diesch/testing/ubuntu precise main
   176    deb-src http://ppa.launchpad.net/diesch/testing/ubuntu precise main
   177    
   178    #### VirtualBox - http://www.virtualbox.org
   179    ## Run this command: wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
   180    deb http://download.virtualbox.org/virtualbox/debian precise contrib
   181    
   182    #### Wine - https://launchpad.net/~ubuntu-wine/+archive/ppa/
   183    ## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
   184    deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
   185    deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
   186    
   187    #### X Updates - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
   188    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
   189    deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
   190    deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
cat: tail: No such file or directory
cat: +1: No such file or directory
   191    deb http://ppa.launchpad.net/ ppa/ppa/ubuntu precise main
   192    deb-src http://ppa.launchpad.net/ ppa/ppa/ubuntu precise main
   193    deb http://ppa.launchpad.net/ ppa/ppa/ubuntu precise main
   194    deb-src http://ppa.launchpad.net/ ppa/ppa/ubuntu precise main
   195    deb http://ppa.launchpad.net/ ppa/ppa/ubuntu precise main
   196    deb-src http://ppa.launchpad.net/ ppa/ppa/ubuntu precise main
   197    # deb http://ppa.launchpad.net/aap/kodi/ubuntu precise main
   198    # deb-src http://ppa.launchpad.net/aap/kodi/ubuntu precise main
   199    # deb http://ppa.launchpad.net/aap/kodi/ubuntu precise main
   200    # deb-src http://ppa.launchpad.net/aap/kodi/ubuntu precise main
   201    # deb http://ppa.launchpad.net/aap/kodi/ubuntu precise main
   202    # deb-src http://ppa.launchpad.net/aap/kodi/ubuntu precise main
   203    # deb http://ppa.launchpad.net/aap/xbmc/ubuntu precise main
   204    # deb-src http://ppa.launchpad.net/aap/xbmc/ubuntu precise main
   205    # deb http://ppa.launchpad.net/aap/xbmc/ubuntu precise main
   206    # deb-src http://ppa.launchpad.net/aap/xbmc/ubuntu precise main
   207    # deb http://ppa.launchpad.net/aap/xbmc/ubuntu precise main
   208    # deb-src http://ppa.launchpad.net/aap/xbmc/ubuntu precise main
   209    deb http://repo.acestream.org/ubuntu/ precise main
   210    deb http://repo.acestream.org/ubuntu/ precise main
   211    deb http://repo.acestream.org/ubuntu/ precise main
   212    deb http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu precise main #Banshee daily builds
   213    deb http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu precise main #Banshee daily builds
   214    deb http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu precise main #Banshee daily builds
   215    deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main #Banshee Team PPA
   216    deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main #Banshee Team PPA
   217    deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main #Banshee Team PPA
   218    deb http://ppa.launchpad.net/chris-lea/node.js/ubuntu precise main
   219    deb-src http://ppa.launchpad.net/chris-lea/node.js/ubuntu precise main
   220    deb http://ppa.launchpad.net/chris-lea/node.js/ubuntu precise main
   221    deb-src http://ppa.launchpad.net/chris-lea/node.js/ubuntu precise main
   222    deb http://ppa.launchpad.net/chris-lea/node.js/ubuntu precise main
   223    deb-src http://ppa.launchpad.net/chris-lea/node.js/ubuntu precise main
   224    deb http://ppa.launchpad.net/chromium-daily/stable/ubuntu precise main #Ubuntu Chromium - Stable Channel PPA
   225    deb http://ppa.launchpad.net/chromium-daily/stable/ubuntu precise main #Ubuntu Chromium - Stable Channel PPA
   226    deb http://ppa.launchpad.net/chromium-daily/stable/ubuntu precise main #Ubuntu Chromium - Stable Channel PPA
   227    deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main #Grub Customizer PPA
   228    deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main #Grub Customizer PPA
   229    deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main #Grub Customizer PPA
   230    deb http://ppa.launchpad.net/gnote/ppa/ubuntu precise main #gnote stable
   231    deb http://ppa.launchpad.net/gnote/ppa/ubuntu precise main #gnote stable
   232    deb http://ppa.launchpad.net/gnote/ppa/ubuntu precise main #gnote stable
   233    deb http://dl.google.com/linux/chrome/deb/ stable main #Google Chrome Stable M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   234    deb http://dl.google.com/linux/chrome/deb/ stable main #Google Chrome Stable M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   235    deb http://dl.google.com/linux/chrome/deb/ stable main #Google Chrome Stable M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   236    deb http://ppa.launchpad.net/john.vrbanac/cuckoo/ubuntu precise main
   237    deb-src http://ppa.launchpad.net/john.vrbanac/cuckoo/ubuntu precise main
   238    deb http://ppa.launchpad.net/john.vrbanac/cuckoo/ubuntu precise main
   239    deb-src http://ppa.launchpad.net/john.vrbanac/cuckoo/ubuntu precise main
   240    deb http://ppa.launchpad.net/john.vrbanac/cuckoo/ubuntu precise main
   241    deb-src http://ppa.launchpad.net/john.vrbanac/cuckoo/ubuntu precise main
   242    deb http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
   243    deb-src http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
   244    deb http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
   245    deb-src http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
   246    deb http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
   247    deb-src http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
   248    deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
   249    deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
   250    deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
   251    deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
   252    deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
   253    deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
   254    ## Please report any bug on https://bugs.launchpad.net/medibuntu/
   255    ## Please report any bug on https://bugs.launchpad.net/medibuntu/
   256    ## Please report any bug on https://bugs.launchpad.net/medibuntu/
   257    deb http://ppa.launchpad.net/relan/exfat/ubuntu precise main
   258    deb-src http://ppa.launchpad.net/relan/exfat/ubuntu precise main
   259    deb http://ppa.launchpad.net/relan/exfat/ubuntu precise main
   260    deb-src http://ppa.launchpad.net/relan/exfat/ubuntu precise main
   261    deb http://ppa.launchpad.net/relan/exfat/ubuntu precise main
   262    deb-src http://ppa.launchpad.net/relan/exfat/ubuntu precise main
   263    deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   264    deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
   265    deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   266    deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
   267    deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   268    deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
   269    deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
   270    deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
   271    deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
   272    deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
   273    deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
   274    deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
   275    deb http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
   276    deb-src http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
   277    deb http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
   278    deb-src http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
   279    deb http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
   280    deb-src http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
   281    deb http://ppa.launchpad.net/synce/ppa/ubuntu precise main
   282    deb-src http://ppa.launchpad.net/synce/ppa/ubuntu precise main
   283    deb http://ppa.launchpad.net/synce/ppa/ubuntu precise main
   284    deb-src http://ppa.launchpad.net/synce/ppa/ubuntu precise main
   285    deb http://ppa.launchpad.net/synce/ppa/ubuntu precise main
   286    deb-src http://ppa.launchpad.net/synce/ppa/ubuntu precise main
   287    # deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu precise main #XBMC PPA
   288    # deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu precise main #XBMC PPA
   289    # deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu precise main #XBMC PPA
   290    # deb http://ppa.launchpad.net/team-xbmc/unstable/ubuntu precise main
   291    # deb-src http://ppa.launchpad.net/team-xbmc/unstable/ubuntu precise main
   292    # deb http://ppa.launchpad.net/team-xbmc/unstable/ubuntu precise main
   293    # deb-src http://ppa.launchpad.net/team-xbmc/unstable/ubuntu precise main
   294    # deb http://ppa.launchpad.net/team-xbmc/unstable/ubuntu precise main
   295    # deb-src http://ppa.launchpad.net/team-xbmc/unstable/ubuntu precise main
   296    # deb http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu precise main
   297    # deb-src http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu precise main
   298    # deb http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu precise main
   299    # deb-src http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu precise main
   300    # deb http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu precise main
   301    # deb-src http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu precise main
   302    deb http://ppa.launchpad.net/tiheum/equinox/ubuntu precise main #Faenza icon theme
   303    deb http://ppa.launchpad.net/tiheum/equinox/ubuntu precise main #Faenza icon theme
   304    deb http://ppa.launchpad.net/tiheum/equinox/ubuntu precise main #Faenza icon theme
   305    deb http://ppa.launchpad.net/transmissionbt/ppa/ubuntu precise main #Transmission Stable builds
   306    deb http://ppa.launchpad.net/transmissionbt/ppa/ubuntu precise main #Transmission Stable builds
   307    deb http://ppa.launchpad.net/transmissionbt/ppa/ubuntu precise main #Transmission Stable builds
   308    deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu precise main #Ubuntu Tweak Stable PPA
   309    deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu precise main #Ubuntu Tweak Stable PPA
   310    deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu precise main #Ubuntu Tweak Stable PPA
   311    deb http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu precise main #Firefox Aurora Builds Official PPA
   312    deb http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu precise main #Firefox Aurora Builds Official PPA
   313    deb http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu precise main #Firefox Aurora Builds Official PPA
   314    deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main #Ubuntu Wine Team PPA
   315    deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main #Ubuntu Wine Team PPA
   316    deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main #Ubuntu Wine Team PPA
   317    deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
   318    deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
   319    deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
   320    deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
   321    deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
   322    deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
   323    deb http://ppa.launchpad.net/upubuntu-com/system/ubuntu precise main
   324    deb-src http://ppa.launchpad.net/upubuntu-com/system/ubuntu precise main
   325    deb http://ppa.launchpad.net/upubuntu-com/system/ubuntu precise main
   326    deb-src http://ppa.launchpad.net/upubuntu-com/system/ubuntu precise main
   327    deb http://ppa.launchpad.net/upubuntu-com/system/ubuntu precise main
   328    deb-src http://ppa.launchpad.net/upubuntu-com/system/ubuntu precise main
   329    deb http://download.virtualbox.org/virtualbox/debian precise contrib #VirtualBox Offical Source M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   330    deb http://download.virtualbox.org/virtualbox/debian precise contrib #VirtualBox Offical Source
   331    deb http://download.virtualbox.org/virtualbox/debian precise contrib #VirtualBox Offical Source M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   332    deb http://download.virtualbox.org/virtualbox/debian precise contrib #VirtualBox Offical Source
   333    deb http://download.virtualbox.org/virtualbox/debian precise contrib #VirtualBox Offical Source M-PM-7M-PM-0M-PM-1M-PM-;M-PM->M-PM-:M-PM-8M-QM-^@M-PM->M-PM-2M-PM-0M-PM-=M-PM-> M-PM-?M-QM-^@M-PM-8 M-PM->M-PM-1M-PM-=M-PM->M-PM-2M-PM-;M-PM-5M-PM-=M-PM-8M-PM-8 M-PM-4M-PM-> precise
   334    deb http://download.virtualbox.org/virtualbox/debian precise contrib #VirtualBox Offical Source
   335    deb http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu precise main #Weather Indicator PPA
   336    deb http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu precise main #Weather Indicator PPA
   337    deb http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu precise main #Weather Indicator PPA
   338    deb http://ppa.launchpad.net/webupd8team/unstable/ubuntu precise main
   339    deb-src http://ppa.launchpad.net/webupd8team/unstable/ubuntu precise main
   340    deb http://ppa.launchpad.net/webupd8team/unstable/ubuntu precise main
   341    deb-src http://ppa.launchpad.net/webupd8team/unstable/ubuntu precise main
   342    deb http://ppa.launchpad.net/webupd8team/unstable/ubuntu precise main
   343    deb-src http://ppa.launchpad.net/webupd8team/unstable/ubuntu precise main
   344    deb http://repo.yandex.ru/yandex-disk/deb/ stable main
   345    deb http://repo.yandex.ru/yandex-disk/deb/ stable main
   346    deb http://repo.yandex.ru/yandex-disk/deb/ stable main
   347    deb http://ppa.launchpad.net/zeitgeist/ppa/ubuntu precise main
   348    deb-src http://ppa.launchpad.net/zeitgeist/ppa/ubuntu precise main
   349    deb http://ppa.launchpad.net/zeitgeist/ppa/ubuntu precise main
   350    deb-src http://ppa.launchpad.net/zeitgeist/ppa/ubuntu precise main
   351    deb http://ppa.launchpad.net/zeitgeist/ppa/ubuntu precise main
   352    deb-src http://ppa.launchpad.net/zeitgeist/ppa/ubuntu precise main
```

When updating:
```
anton@anton-bung:~$ sudo apt-get updateErr http://packages.dorkfolio.net precise Release.gpg
  Could not resolve 'packages.dorkfolio.net'
Hit http://ru.archive.ubuntu.com precise Release.gpg                                                                                                                    
Hit http://ru.archive.ubuntu.com precise-security Release.gpg                                                                                                           
Hit http://ru.archive.ubuntu.com precise-updates Release.gpg                                                                                                            
Hit http://ru.archive.ubuntu.com precise-proposed Release.gpg                                                                                                           
Hit http://ru.archive.ubuntu.com precise-backports Release.gpg                                                                                                          
Hit http://repo.yandex.ru stable Release.gpg                                                                                                                            
Ign http://dl.google.com testing Release.gpg                                                                                                                            
Hit http://ru.archive.ubuntu.com precise Release                                                                                                                        
Hit http://ru.archive.ubuntu.com precise-security Release                                                                                                               
Hit http://ru.archive.ubuntu.com precise-updates Release                                                                                                                
Hit http://ru.archive.ubuntu.com precise-proposed Release                                                                                                               
Hit http://dl.google.com stable Release.gpg                                                                                                                             
Hit http://repo.yandex.ru stable Release                                                                                                                                
Hit http://ru.archive.ubuntu.com precise-backports Release                                                                                                              
Ign http://dl.google.com testing Release                                                                                                                                
Hit http://ru.archive.ubuntu.com precise/main Sources                                                                                                                   
Hit http://ru.archive.ubuntu.com precise/restricted Sources                                                                                                             
Hit http://ru.archive.ubuntu.com precise/universe Sources                                                                                                               
Hit http://ru.archive.ubuntu.com precise/multiverse Sources                                                                                                             
Hit http://ru.archive.ubuntu.com precise/main amd64 Packages                                                                                                            
Hit http://ru.archive.ubuntu.com precise/restricted amd64 Packages                                                                                                      
Ign http://www.bunkus.org ./ Release.gpg                                                                                                                                
Hit http://deb.opera.com stable Release.gpg                                                                                                                             
Get:1 http://deb.torproject.org precise Release.gpg [490 B]                                                                                                             
Hit http://ru.archive.ubuntu.com precise/universe amd64 Packages                                                                                                        
Hit http://ru.archive.ubuntu.com precise/multiverse amd64 Packages                                                                                                      
Hit http://ru.archive.ubuntu.com precise-security/main Sources                                                                                                          
Hit http://ru.archive.ubuntu.com precise-security/restricted Sources                                                                                                    
Hit http://dl.google.com stable Release                                                                                                                                 
Hit http://download.virtualbox.org precise Release.gpg                                                                                                                  
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Get:2 http://ppa.launchpad.net precise Release.gpg [316 B]                                                                                                              
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://extras.ubuntu.com precise Release.gpg                                                                                                                        
Hit http://deb.playonlinux.com precise Release.gpg                                                                                                                      
Hit http://archive.canonical.com precise Release.gpg                                                                                                                    
Hit http://apt.mucommander.com stable Release.gpg                                                                                                                       
Hit http://ru.archive.ubuntu.com precise-security/universe Sources                                                                                                      
Hit http://ru.archive.ubuntu.com precise-security/multiverse Sources                                                                                                    
Hit http://ru.archive.ubuntu.com precise-security/main amd64 Packages                                                                                                   
Hit http://ru.archive.ubuntu.com precise-security/restricted amd64 Packages                                                                                             
Hit http://ru.archive.ubuntu.com precise-security/universe amd64 Packages                                                                                               
Hit http://ru.archive.ubuntu.com precise-security/multiverse amd64 Packages                                                                                             
Hit http://repo.yandex.ru stable/main amd64 Packages                                                                                                                    
Ign http://download.skype.com stable Release.gpg                                                                                                                        
Hit http://ru.archive.ubuntu.com precise-updates/main Sources                                                                                                           
Hit http://ru.archive.ubuntu.com precise-updates/restricted Sources                                                                                                     
Hit http://ru.archive.ubuntu.com precise-updates/universe Sources                                                                                                       
Hit http://ru.archive.ubuntu.com precise-updates/multiverse Sources                                                                                                     
Hit http://ru.archive.ubuntu.com precise-updates/main amd64 Packages                                                                                                    
Hit http://ru.archive.ubuntu.com precise-updates/restricted amd64 Packages                                                                                              
Hit http://ru.archive.ubuntu.com precise-updates/universe amd64 Packages                                                                                                
Hit http://ru.archive.ubuntu.com precise-updates/multiverse amd64 Packages                                                                                              
Hit http://ru.archive.ubuntu.com precise-proposed/main Sources                                                                                                          
Hit http://repo.daniil.it lenny Release.gpg                                                                                                                             
Ign http://dl.google.com testing/non-free TranslationIndex                                                                                                              
Hit http://download.virtualbox.org precise Release                                                                                                                      
Hit http://deb.opera.com stable Release                                                                                                                                 
Hit http://www.bunkus.org ./ Release                                                                                                                                    
Hit http://deb.torproject.org precise Release                                                                                                                           
Hit http://ru.archive.ubuntu.com precise-proposed/restricted Sources                                                                                                    
Hit http://ru.archive.ubuntu.com precise-proposed/universe Sources                                                                                                      
Hit http://ru.archive.ubuntu.com precise-proposed/multiverse Sources                                                                                                    
Hit http://ru.archive.ubuntu.com precise-proposed/main amd64 Packages                                                                                                   
Hit http://ru.archive.ubuntu.com precise-proposed/restricted amd64 Packages                                                                                             
Hit http://ru.archive.ubuntu.com precise-proposed/universe amd64 Packages                                                                                               
Ign http://deb.torproject.org precise Release                                                                                                                           
Hit http://dl.google.com stable/main amd64 Packages                                                                                                                     
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ru.archive.ubuntu.com precise-proposed/multiverse amd64 Packages                                                                                             
Hit http://deb.playonlinux.com precise Release                                                                                                                          
Hit http://ru.archive.ubuntu.com precise-backports/main Sources                                                                                                         
Hit http://ru.archive.ubuntu.com precise-backports/restricted Sources                                                                                                   
Hit http://ru.archive.ubuntu.com precise-backports/universe Sources                                                                                                     
Hit http://extras.ubuntu.com precise Release                                                                                                                            
Hit http://archive.canonical.com precise Release                                                                                                                        
Hit http://apt.mucommander.com stable Release                                                                                                                           
Hit http://download.virtualbox.org precise/contrib amd64 Packages                                                                                                       
Hit http://ru.archive.ubuntu.com precise-backports/multiverse Sources                                                                                                   
Hit http://ru.archive.ubuntu.com precise-backports/main amd64 Packages                                                                                                  
Hit http://ru.archive.ubuntu.com precise-backports/restricted amd64 Packages                                                                                            
Hit http://ru.archive.ubuntu.com precise-backports/universe amd64 Packages                                                                                              
Hit http://ru.archive.ubuntu.com precise-backports/multiverse amd64 Packages                                                                                            
Hit http://repo.daniil.it lenny Release                                                                                                                                 
Hit http://deb.opera.com stable/non-free amd64 Packages                                                                                                                 
Ign http://www.bunkus.org ./ Sources/DiffIndex                                                                                                                          
Ign http://deb.torproject.org precise/main Sources/DiffIndex                                                                                                            
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Ign http://ppa.launchpad.net ppa/ppa/ubuntu Release.gpg                                                                                                                 
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Ign http://download.skype.com stable Release                                                                                                                            
Hit http://deb.playonlinux.com precise/main amd64 Packages                                                                                                              
Ign http://www.bunkus.org ./ Packages/DiffIndex                                                                                                                         
Hit http://extras.ubuntu.com precise/main Sources                                                                                                                       
Ign http://deb.torproject.org precise/main amd64 Packages/DiffIndex                                                                                                     
Ign http://deb.torproject.org precise/main i386 Packages/DiffIndex                                                                                                      
Ign http://deb.torproject.org precise/main TranslationIndex                                                                                                             
Hit http://archive.canonical.com precise/partner Sources                                                                                                                
Hit http://repo.daniil.it lenny/main amd64 Packages                                                                                                                     
Hit http://apt.mucommander.com stable/main amd64 Packages                                                                                                               
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://www.bunkus.org ./ Sources                                                                                                                                    
Hit http://www.bunkus.org ./ Packages                                                                                                                                   
Hit http://extras.ubuntu.com precise/main amd64 Packages                                                                                                                
Hit http://archive.canonical.com precise/partner amd64 Packages                                                                                                         
Hit http://apt.mucommander.com stable/non-free amd64 Packages                                                                                                           
Hit http://apt.mucommander.com stable/contrib amd64 Packages                                                                                                            
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Err http://dl.google.com testing/non-free amd64 Packages                                                                                                                
  404  Not Found [IP: 64.233.161.93 80]
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Err http://dl.google.com testing/non-free foreign-architecture Packages                                                                                                 
  404  Not Found [IP: 64.233.161.93 80]
Hit http://downloads-distro.mongodb.org dist Release.gpg                                                                                                                
Err http://dl.google.com testing/non-free i386 Packages                                                                                                                 
  404  Not Found [IP: 64.233.161.93 80]
Ign http://dl.google.com testing/non-free Translation-en                                                                                                                
Ign http://ppa.launchpad.net precise Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Ign http://dl.google.com testing/non-free Translation-ru                                                                                                                
Ign http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Ign http://download.skype.com stable/non-free i386 Packages/DiffIndex                                                                                                   
Hit http://deb.torproject.org precise/main Sources                                                                                                                      
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Ign http://www.bunkus.org ./ Translation-en                                                                                                                             
Hit http://deb.torproject.org precise/main amd64 Packages                                                                                                               
Err http://deb.torproject.org precise/main foreign-architecture Packages                                                                                                
  404  Not Found [IP: 82.195.75.101 80]
Hit http://deb.torproject.org precise/main i386 Packages                                                                                                                
Ign http://download.skype.com stable/non-free TranslationIndex                                                                                                          
Ign http://ppa.launchpad.net ppa/ppa/ubuntu Release                                                                                                                     
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Ign http://www.bunkus.org ./ Translation-ru                                                                                                                             
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Ign http://deb.torproject.org precise/main Translation-en                                                                                                               
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Hit http://downloads-distro.mongodb.org dist Release                                                                                                                    
Ign http://deb.torproject.org precise/main Translation-ru                                                                                                               
Hit http://download.skype.com stable/non-free i386 Packages                                                                                                             
Hit http://free.nchc.org.tw drbl Release.gpg                                                                                                                            
Hit http://downloads-distro.mongodb.org dist/10gen amd64 Packages                                                                                                       
Hit http://repo.acestream.org precise Release.gpg                                                                                                                       
Hit http://ppa.launchpad.net precise Release                                                                                                      
Hit http://ppa.launchpad.net precise Release                                                                                
Hit http://ppa.launchpad.net precise Release                                                                                                      
Hit http://ppa.launchpad.net precise Release                                                                                                                            
Ign http://ppa.launchpad.net precise Release                                                                                                      
Hit http://ppa.launchpad.net precise/main Sources                                                                                                 
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                          
Hit http://ppa.launchpad.net precise/main Sources                                                                                                 
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                          
Hit http://ppa.launchpad.net precise/main Sources                                                                                                 
Hit http://free.nchc.org.tw drbl Release                                                                                                                                
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                          
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                          
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                                                                                       
Ign http://ppa.launchpad.net precise/main amd64 Packages/DiffIndex                                                                                
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex                                                           
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                  
Hit http://ppa.launchpad.net precise/main Sources                                                                                                 
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                          
Hit http://ppa.launchpad.net precise/main Sources                                                                                                 
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                          
Hit http://ppa.launchpad.net precise/main Sources                                                                                                 
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                          
Hit http://ppa.launchpad.net precise/main Sources                                                                                                 
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                                                
Hit http://ppa.launchpad.net precise/main Sources                                                                                                 
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                    
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                    
Hit http://ppa.launchpad.net precise/main Sources                                                                                                 
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                          
Hit http://ppa.launchpad.net precise/main Sources                                                                           
Hit http://repo.acestream.org precise Release                                                                                                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                          
Hit http://ppa.launchpad.net precise/main Sources                                                                                                
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                   
Hit http://ppa.launchpad.net precise/main Sources                                                                          
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                   
Hit http://ppa.launchpad.net precise/main Sources                                                                          
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                   
Hit http://ppa.launchpad.net precise/main Sources                                                                          
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                         
Hit http://ppa.launchpad.net precise/main Sources                                                                                               
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                        
Hit http://ppa.launchpad.net precise/main Sources                                                                                               
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                        
Hit http://ppa.launchpad.net precise/main Sources                                                                                               
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                        
Hit http://ppa.launchpad.net precise/main Sources                                                                                                 
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                          
Hit http://free.nchc.org.tw drbl/stable amd64 Packages                                                                                            
Hit http://repo.acestream.org precise/main amd64 Packages                                                                   
Err http://download.skype.com stable/non-free amd64 Packages                                                                
  404  Not Found [IP: 23.60.69.23 80]
Ign http://ppa.launchpad.net ppa/ppa/ubuntu/main TranslationIndex                                     
Ign http://ppa.launchpad.net ppa/ppa/ubuntu/precise TranslationIndex                                 
Hit http://ppa.launchpad.net precise/main amd64 Packages                                             
Hit http://ppa.launchpad.net precise/main Sources                                                    
Hit http://ppa.launchpad.net precise/main amd64 Packages                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                              
Hit http://ppa.launchpad.net precise/main Sources                                                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                                            
Hit http://ppa.launchpad.net precise/main Sources                                                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                                             
Hit http://ppa.launchpad.net precise/main Sources                                                    
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main Sources                                                    
Err http://download.skype.com stable/non-free foreign-architecture Packages                          
  404  Not Found [IP: 23.60.69.23 80]
Hit http://ppa.launchpad.net precise/main amd64 Packages                           
Hit http://ppa.launchpad.net precise/main Sources            
Hit http://ppa.launchpad.net precise/main amd64 Packages                           
Hit http://ppa.launchpad.net precise/main Sources                                                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                           
Hit http://ppa.launchpad.net precise/main amd64 Packages                           
Hit http://ppa.launchpad.net precise/main amd64 Packages                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                              
Hit http://ppa.launchpad.net precise/main Sources                                  
Hit http://ppa.launchpad.net precise/main amd64 Packages                                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                           
Ign http://ppa.launchpad.net precise/main TranslationIndex                                           
Hit http://ppa.launchpad.net precise/main Sources                                  
Hit http://ppa.launchpad.net precise/main amd64 Packages                                             
Hit http://ppa.launchpad.net precise/main Sources                                  
Hit http://ppa.launchpad.net precise/main amd64 Packages                           
Hit http://ppa.launchpad.net precise/main i386 Packages                                               
Ign http://download.skype.com stable/non-free Translation-en                                          
Ign http://download.skype.com stable/non-free Translation-ru                       
Err http://ppa.launchpad.net precise/main foreign-architecture Packages                 
  404  Not Found
Err http://ppa.launchpad.net ppa/ppa/ubuntu/precise Sources  
  404  Not Found
Err http://ppa.launchpad.net ppa/ppa/ubuntu/main Sources     
  404  Not Found
Err http://ppa.launchpad.net ppa/ppa/ubuntu/precise amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net ppa/ppa/ubuntu/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net ppa/ppa/ubuntu/precise foreign-architecture Packages
  404  Not Found
Err http://ppa.launchpad.net ppa/ppa/ubuntu/main foreign-architecture Packages
  404  Not Found
Err http://ppa.launchpad.net ppa/ppa/ubuntu/precise i386 Packages
  404  Not Found
Err http://ppa.launchpad.net ppa/ppa/ubuntu/main i386 Packages
  404  Not Found
Err http://ppa.launchpad.net precise/main Sources
  404  Not Found
Err http://ppa.launchpad.net precise/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net precise/main foreign-architecture Packages
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-ru
Ign http://ppa.launchpad.net ppa/ppa/ubuntu/main Translation-en
Ign http://ppa.launchpad.net ppa/ppa/ubuntu/main Translation-ru
Ign http://ppa.launchpad.net ppa/ppa/ubuntu/precise Translation-en
Ign http://ppa.launchpad.net ppa/ppa/ubuntu/precise Translation-ru
Ign http://ppa.launchpad.net precise/main Translation-en     
Ign http://ppa.launchpad.net precise/main Translation-ru     
Hit http://archive.getdeb.net precise-getdeb Release.gpg                                                                                                                
Hit http://archive.getdeb.net precise-getdeb Release                                                                                                                    
Hit http://archive.getdeb.net precise-getdeb/apps amd64 Packages                                                                                                        
Hit http://archive.getdeb.net precise-getdeb/games amd64 Packages                                                                                                       
Fetched 806 B in 11s (70 B/s)                                                                                                                                           
Reading package lists... Done
W: GPG error: http://deb.torproject.org precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7778990EEEB23232
W: Failed to fetch http://packages.dorkfolio.net/ubuntu/dists/precise/Release.gpg  Could not resolve 'packages.dorkfolio.net'


W: Failed to fetch http://ru.archive.ubuntu.com/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ru.archive.ubuntu.com/ubuntu/dists/precise-security/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ru.archive.ubuntu.com/ubuntu/dists/precise-updates/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ru.archive.ubuntu.com/ubuntu/dists/precise-proposed/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ru.archive.ubuntu.com/ubuntu/dists/precise-backports/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://repo.yandex.ru/yandex-disk/deb/dists/stable/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://dl.google.com/linux/deb/dists/testing/non-free/binary-amd64/Packages  404  Not Found [IP: 64.233.161.93 80]


W: Failed to fetch http://dl.google.com/linux/deb/dists/testing/non-free/binary-foreign-architecture/Packages  404  Not Found [IP: 64.233.161.93 80]


W: Failed to fetch http://dl.google.com/linux/deb/dists/testing/non-free/binary-i386/Packages  404  Not Found [IP: 64.233.161.93 80]


W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release  Unable to find expected entry 'non-free/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/precise/Release  Unable to find expected entry 'contrib/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/network-manager/trunk/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/audacity-team/daily/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/shnatsel/cairo-compmgr/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/flacon/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/gcstar/gcstar-dev/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://deb.playonlinux.com/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/Release  Unable to find expected entry 'partner/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://apt.mucommander.com/dists/stable/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://repo.daniil.it/dists/lenny/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://deb.torproject.org/torproject.org/dists/precise/main/binary-foreign-architecture/Packages  404  Not Found [IP: 82.195.75.101 80]


W: Failed to fetch http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/motumedia/mplayer-daily/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/smplayer2/daily/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/tualatrix/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/diesch/testing/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/chris-lea/node.js/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages  404  Not Found [IP: 23.60.69.23 80]


W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-foreign-architecture/Packages  404  Not Found [IP: 23.60.69.23 80]


W: Failed to fetch http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/gnote/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/john.vrbanac/cuckoo/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/relan/exfat/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/synce/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/upubuntu-com/system/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/webupd8team/unstable/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://downloads-distro.mongodb.org/repo/ubuntu-upstart/dists/dist/Release  Unable to find expected entry '10gen/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/ripps818/coreavc/ubuntu/dists/precise/main/binary-foreign-architecture/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/dists/ppa/ppa/ubuntu/precise/source/Sources  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/dists/ppa/ppa/ubuntu/main/source/Sources  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/dists/ppa/ppa/ubuntu/precise/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/dists/ppa/ppa/ubuntu/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/dists/ppa/ppa/ubuntu/precise/binary-foreign-architecture/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/dists/ppa/ppa/ubuntu/main/binary-foreign-architecture/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/dists/ppa/ppa/ubuntu/precise/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/dists/ppa/ppa/ubuntu/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://free.nchc.org.tw/drbl-core/dists/drbl/Release  Unable to find expected entry 'stable/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://repo.acestream.org/ubuntu/dists/precise/Release  Unable to find expected entry 'main/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/dists/precise/main/binary-foreign-architecture/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/Release  Unable to find expected entry 'apps/binary-foreign-architecture/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry http://ppa.launchpad.net/banshee-team/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_banshee-team_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_libreoffice_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://download.virtualbox.org/virtualbox/debian/ precise/contrib amd64 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry http://download.virtualbox.org/virtualbox/debian/ precise/contrib amd64 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://download.skype.com/linux/repos/debian/ stable/non-free i386 Packages (/var/lib/apt/lists/download.skype.com_linux_repos_debian_dists_stable_non-free_binary-i386_Packages)
```

```
anton@anton-bung:~$ sudo apt-get dist-upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

```
anton@anton-bung:~$ sudo apt-get install wine1.7Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine1.7 : Depends: wine1.7-i386 (= 1:1.7.18-0ubuntu1) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

```
anton@anton-bung:~$ sudo apt-get install skype  Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.
```

```
anton@anton-bung:~$ sudo apt-get install nfs-kernel-serverReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 nfs-kernel-server : Depends: libtirpc1 but it is not going to be installed
                     Depends: nfs-common (= 1:1.2.5-3ubuntu3.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


anton@anton-bung:~$ sudo apt-get install nfs-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 nfs-common : Depends: libtirpc1 but it is not going to be installed
              Depends: rpcbind (>= 0.2.0-6ubuntu1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by TheFu on 2015-08-23
Looks like you have conflicting dependencies caused by all the different PPAs.  I generally don't use more than 2-3 PPAs on a system and each of those comes from someone actively maintaining their packages who is trusted in this community. It is always a risk that one of those PPAs can break stuff.

**Daily** repos are especially dangerous.

I can't tell you want to do.  I can say that I would **remove all PPAs**, get current on the core system updates. Only then, work forward to get the top 3 specific software items you absolutely require installed after the core system is working.

BTW - posting so much data scares many people away from attempting to help. 1 small issue, get that solved - only then move onto the next one.

Fix everything in **sudo apt-get update**.

---

### Post by anton37 on 2015-08-23
Do you mean I'd clean my source.list clean, autoremove and update?

---

