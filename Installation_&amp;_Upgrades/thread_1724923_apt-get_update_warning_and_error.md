---
title: "apt-get update warning and error"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by ashickur.noor on 2011-04-08
From few days I get this error when I try to update the repo 
```
 Failed to fetch file:///opt/locrepo/repository/dists/lucid/main/binary-amd64/Packages.gz  File not found

W: Failed to fetch file:///opt/locrepo/repository/dists/lucid/restricted/binary-amd64/Packages.gz  File not found

W: Failed to fetch file:///opt/locrepo/repository/dists/lucid/multiverse/binary-amd64/Packages.gz  File not found

W: Failed to fetch file:///opt/locrepo/repository/dists/lucid/universe/binary-amd64/Packages.gz  File not found


```

and error 
```
Err file: lucid/main Packages                                                  
  File not found
Err file: lucid/restricted Packages                                            
  File not found
Err file: lucid/multiverse Packages                                            
  File not found
Err file: lucid/universe Packages                                              
  File not found

```

---

### Post by ngubk on 2011-04-09
Could you post your source.list here?
gksudo gedit /etc/apt/sources.list
Is there any file in that directory /opt/locrepo/repository/dists/lucid/

---

### Post by ashickur.noor on 2011-04-09
```
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)]/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirrors.ispros.com.bd/ubuntu/ lucid main restricted
deb-src http://mirrors.ispros.com.bd/ubuntu/ lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.ispros.com.bd/ubuntu/ lucid-updates main restricted
deb-src http://mirrors.ispros.com.bd/ubuntu/ lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirrors.ispros.com.bd/ubuntu/ lucid universe
deb http://mirrors.ispros.com.bd/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.ispros.com.bd/ubuntu/ lucid multiverse
deb http://mirrors.ispros.com.bd/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://bd.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://bd.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://mirrors.ispros.com.bd/ubuntu/ lucid-security main restricted
deb-src http://mirrors.ispros.com.bd/ubuntu/ lucid-security restricted main multiverse universe #Added by software-properties
deb http://mirrors.ispros.com.bd/ubuntu/ lucid-security universe
deb http://mirrors.ispros.com.bd/ubuntu/ lucid-security multiverse
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://mirrors.ispros.com.bd/ubuntu/ lucid multiverse

###### Ubuntu Update Repos
deb http://mirrors.ispros.com.bd/ubuntu/ lucid-security multiverse
deb http://mirrors.ispros.com.bd/ubuntu/ lucid-updates multiverse

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Abiword - http://www.abisource.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2382D57E
# deb http://ppa.launchpad.net/abiword-stable/ubuntu lucid main

#### Ailurus - http://code.google.com/p/ailurus/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9A6FE242
deb http://ppa.launchpad.net/ailurus/ppa/ubuntu lucid main

#### AWN (Avant Window Navigator) Testing Packages - http://awn-project.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu lucid main

#### Banshee - https://edge.launchpad.net/~banshee-team
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu lucid main

#### Blueman - https://edge.launchpad.net/~blueman/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 951DC1E2
deb http://ppa.launchpad.net/blueman/ppa/ubuntu lucid main

#### Breathe Icon Set - https://edge.launchpad.net/~breathe-dev/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 45FFBBBA
deb http://ppa.launchpad.net/breathe-dev/ppa/ubuntu lucid main

#### Cairo Dock - http://www.glx-dock.org
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
deb http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu lucid main

#### Conky - https://launchpad.net/conky
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 95628707
deb http://ppa.launchpad.net/norsetto/ppa/ubuntu lucid main

#### Deluge BitTorrent - http://www.deluge-torrent.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 249AD24C
deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu lucid main

#### Dropbox - https://www.dropbox.com/
## Run this command: sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
deb http://linux.dropbox.com/ubuntu lucid main

#### Emesene - http://www.emesene.org
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E2314809
deb http://ppa.launchpad.net/bjfs/ppa/ubuntu lucid main

#### Enna - http://enna.geexbox.org
deb http://packages.geexbox.org/ lucid main

#### Epiphany - http://projects.gnome.org/epiphany/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D9A3C5B
deb http://ppa.launchpad.net/webkit-team/epiphany/ubuntu lucid main

#### Esmska - http://code.google.com/p/esmska/ 
## Run this command: wget -q -O - http://repo.palatinus.cz/repo.key | sudo apt-key add -
deb http://repo.palatinus.cz/stable /

#### Exaile - http://www.exaile.org
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 43CBFCC0
deb http://ppa.launchpad.net/exaile-devel/ppa/ubuntu lucid main

#### FBReader - http://www.fbreader.org/desktop/
## Run this command: http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc -O- | sudo apt-key add -
deb http://www.fbreader.org/desktop/debian stable main

#### Freeswitch Nightly Drivers - http://www.freeswitch.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 51AE93C
deb http://ppa.launchpad.net/freeswitch-drivers/freeswitch-nightly-drivers/ubuntu lucid main

#### GetDeb - http://www.getdeb.net
## Run this command: wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
deb http://archive.getdeb.net/ubuntu lucid-getdeb apps

#### Google Linux Software Repositories - http://www.google.com/linuxrepositories/index.html
## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/deb/ stable non-free

#### LibreOffice 3.3 - http://www.documentfoundation.org/download/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu lucid main

#### Liferea Stable - http://liferea.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 412F055D
deb http://ppa.launchpad.net/liferea/ppa/ubuntu lucid main

#### MediaInfo - http://mediainfo.sourceforge.net
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9D8BC54
deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu lucid main

#### Midori - https://launchpad.net/~midori/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
deb http://ppa.launchpad.net/midori/ppa/ubuntu lucid main

#### MKVToolnix - http://www.bunkus.org/videotools/mkvtoolnix/
## Run this command: wget -q http://www.bunkus.org/gpg-pub-moritzbunkus.txt -O- | sudo apt-key add -
deb http://www.bunkus.org/ubuntu/lucid/ ./

#### Pidgin - http://pidgin.im
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu lucid main

#### Playdeb - http://www.playdeb.net/
## Run this command: wget -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
deb http://archive.getdeb.net/ubuntu lucid-getdeb games

#### PlayOnLinux - http://www.playonlinux.com
## Run this command: sudo apt-get update && sudo apt-get install playonlinux
deb http://deb.playonlinux.com/ lucid main

#### SMPlayer - http://smplayer.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E4A4F4F4
deb http://ppa.launchpad.net/rvm/smplayer/ubuntu lucid main

#### Themes for GNOME and Ubuntu - https://edge.launchpad.net/~bisigi/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu lucid main

#### Ubuntu Tweak - http://ubuntu-tweak.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu lucid main

#### UNetbootin - http://unetbootin.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu lucid main

#### VirtualBox - http://www.virtualbox.org
## Run this command: wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
deb http://download.virtualbox.org/virtualbox/debian lucid contrib

#### VLC Media Player  - http://www.videolan.org/vlc/
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb http://ppa.launchpad.net/c-korn/ppa/ubuntu lucid main

#### Wine - https://launchpad.net/~ubuntu-wine/+archive/ppa/
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main


####### 3rd Party Source Repos

#### Abiword (Source) - http://www.abisource.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2382D57E
# deb-src http://ppa.launchpad.net/abiword-stable/ubuntu lucid main

#### Ailurus (Source) - http://code.google.com/p/ailurus/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9A6FE242
deb-src http://ppa.launchpad.net/ailurus/ppa/ubuntu lucid main

#### AWN (Avant Window Navigator) Testing Packages (Source) - http://awn-project.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
deb-src http://ppa.launchpad.net/awn-testing/ppa/ubuntu lucid main

#### Banshee (Source) - https://edge.launchpad.net/~banshee-team
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu lucid main

#### Blueman (Source) - https://edge.launchpad.net/~blueman/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 951DC1E2
deb-src http://ppa.launchpad.net/blueman/ppa/ubuntu lucid main

#### Breathe Icon Set (Source) - https://edge.launchpad.net/~breathe-dev/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 45FFBBBA
deb-src http://ppa.launchpad.net/breathe-dev/ppa/ubuntu lucid main

#### Conky (Source) - https://launchpad.net/conky
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 95628707
deb-src http://ppa.launchpad.net/norsetto/ppa/ubuntu lucid main

#### Deluge BitTorrent (Source) - http://www.deluge-torrent.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 249AD24C
deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu lucid main

#### Dropbox (Source) - https://www.dropbox.com/
## Run this command: sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
deb-src http://linux.dropbox.com/ubuntu lucid main

#### Emesene (Source) - http://www.emesene.org
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E2314809
deb-src http://ppa.launchpad.net/bjfs/ppa/ubuntu lucid main

#### Epiphany (Source) - http://projects.gnome.org/epiphany/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D9A3C5B
deb-src http://ppa.launchpad.net/webkit-team/epiphany/ubuntu lucid main

#### Exaile (Source) - http://www.exaile.org
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 43CBFCC0
deb-src http://ppa.launchpad.net/exaile-devel/ppa/ubuntu lucid main

#### FBReader (Source) - http://www.fbreader.org/desktop/
## Run this command: http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc -O- | sudo apt-key add -
deb-src http://www.fbreader.org/desktop/debian stable main

#### Freeswitch Nightly Drivers (Source) - http://www.freeswitch.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 51AE93C
deb-src http://ppa.launchpad.net/freeswitch-drivers/freeswitch-nightly-drivers/ubuntu lucid main

#### LibreOffice 3.3 (Source) - http://www.documentfoundation.org/download/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu lucid main

#### Liferea Stable (Source) - http://liferea.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 412F055D
deb-src http://ppa.launchpad.net/liferea/ppa/ubuntu lucid main

#### MediaInfo (Source) - http://mediainfo.sourceforge.net
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9D8BC54
deb-src http://ppa.launchpad.net/shiki/mediainfo/ubuntu lucid main

#### Midori (Source) - https://launchpad.net/~midori/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
deb-src http://ppa.launchpad.net/midori/ppa/ubuntu lucid main

#### MKVToolnix (Source) - http://www.bunkus.org/videotools/mkvtoolnix/
## Run this command: wget -q http://www.bunkus.org/gpg-pub-moritzbunkus.txt -O- | sudo apt-key add -
deb-src http://www.bunkus.org/ubuntu/lucid/ ./

#### Pidgin (Source) - http://pidgin.im
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu lucid main

#### SMPlayer (Source) - http://smplayer.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E4A4F4F4
deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu lucid main

#### Themes for GNOME and Ubuntu (Source) - https://edge.launchpad.net/~bisigi/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu lucid main

#### Ubuntu Tweak (Source) - http://ubuntu-tweak.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb-src http://ppa.launchpad.net/tualatrix/ubuntu lucid main

#### UNetbootin (Source) - http://unetbootin.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
deb-src http://ppa.launchpad.net/gezakovacs/ppa/ubuntu lucid main

#### VLC Media Player  (Source) - http://www.videolan.org/vlc/
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb-src http://ppa.launchpad.net/c-korn/ppa/ubuntu lucid main

#### Wine (Source) - https://launchpad.net/~ubuntu-wine/+archive/ppa/
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main



deb http://archive.canonical.com/ lucid partner
## Depôt MultiSystem
deb http://liveusb.info/multisystem/depot all main
```

---

### Post by ngubk on 2011-04-09
Sorry, i'm not that experienced yet. I can't see anything wrong with your source.list.
Could you try this:
[http://theindexer.wordpress.com/2010/03/21/to-do-list-after-installing-ubuntu-10-04-aka-lucid-lynx/](http://theindexer.wordpress.com/2010/03/21/to-do-list-after-installing-ubuntu-10-04-aka-lucid-lynx/)
This is the source.list i used when i installed lucid.

---

### Post by oldos2er on 2011-04-09
> **ashickur.noor said:**
> From few days I get this error 

Are there any files in /etc/apt/sources.list.d/ ?

---

### Post by ulrichard on 2011-06-06
Could be related to the fact that there are no natty packages yet for freeswitch in the ppa.
[https://launchpad.net/~freeswitch-drivers/+archive/freeswitch-nightly-drivers](https://launchpad.net/~freeswitch-drivers/+archive/freeswitch-nightly-drivers)

---

