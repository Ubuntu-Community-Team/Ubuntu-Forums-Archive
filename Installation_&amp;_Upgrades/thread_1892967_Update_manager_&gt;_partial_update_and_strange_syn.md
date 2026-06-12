---
title: "Update manager &gt; partial update and strange synaptic things"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by editheraven on 2011-12-09
I have recently generated a new sources.list from a website, adding all ppas and keys. When i want to update, it says that i can only partial update. This is my new list

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://ro.archive.ubuntu.com/ubuntu/ natty main restricted universe multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ natty main restricted universe multiverse

###### Ubuntu Update Repos
deb http://ro.archive.ubuntu.com/ubuntu/ natty-security main restricted universe multiverse
deb http://ro.archive.ubuntu.com/ubuntu/ natty-updates main restricted universe multiverse
deb http://ro.archive.ubuntu.com/ubuntu/ natty-proposed main restricted universe multiverse
deb http://ro.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ natty-security main restricted universe multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ natty-updates main restricted universe multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ natty-proposed main restricted universe multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Audacity - http://audacity.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys     1024R/BB901940
deb http://ppa.launchpad.net/audacity-team/daily/ubuntu natty main

#### AWN (Avant Window Navigator) Testing Packages - http://awn-project.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu natty main

#### Banshee - https://edge.launchpad.net/~banshee-team
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu natty main

#### Chromium Project - http://code.google.com/chromium/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E5E17B5
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu natty main

#### DeaDBeeF - http://deadbeef.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3C8E2A7F
deb http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu natty main

#### Deluge BitTorrent - http://www.deluge-torrent.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 249AD24C
deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu natty main

#### Equinox - https://launchpad.net/~tiheum/+archive/equinox
## Run this command: sudo apt-get update && sudo apt-get install faenza-icon-theme && sudo apt-get install equinox-theme    
deb http://ppa.launchpad.net/tiheum/equinox/ubuntu natty main

#### Esmska - http://code.google.com/p/esmska/ 
## Run this command: wget -q -O - http://repo.palatinus.cz/repo.key | sudo apt-key add -
deb http://repo.palatinus.cz/stable /

#### FBReader - http://www.fbreader.org/desktop/
## Run this command: http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc -O- | sudo apt-key add -
deb http://www.fbreader.org/desktop/debian stable main

#### Flacon - http://kde-apps.org/content/show.php?content=113388
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
deb http://ppa.launchpad.net/flacon/ppa/ubuntu natty main

#### Fritz Fun (ffgtk) - http://www.tabos.org/ffgtk/index.php
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key 928EDC6B
deb http://ppa.launchpad.net/stevi/ppa/ubuntu natty main

#### GCstar - http://www.gcstar.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5BE6AD9A
deb http://ppa.launchpad.net/gcstar/gcstar-dev/ubuntu natty main

#### GetDeb - http://www.getdeb.net
## Run this command: wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
deb http://archive.getdeb.net/ubuntu natty-getdeb apps

#### Glx-Dock / Cairo-Dock - http://www.glx-dock.org
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
deb http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu natty main

#### GNUzilla and IceCat - http://www.gnu.org/software/gnuzilla/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 
deb http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu natty main

#### Google Linux Software Repositories - http://www.google.com/linuxrepositories/
## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/deb/ stable non-free

#### Google Linux Software Repositories (Testing) - http://www.google.com/linuxrepositories/
## Run this command: wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add  -
deb http://dl.google.com/linux/deb/ testing non-free

#### Gwibber (Daily) - https://launchpad.net/gwibber
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
deb http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu natty main

#### HandBrake Releases - http://handbrake.fr/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 816950D8
deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu natty main

#### HandBrake Snapshots - http://handbrake.fr/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 816950D8
deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu natty main

#### Kubuntu Backports - https://edge.launchpad.net/~kubuntu-ppa/+archive/backports
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
#deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu natty main

#### Kubuntu Beta Backports - https://launchpad.net/~kubuntu-ppa/+archive/beta
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
#deb http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu natty main

#### Kubuntu Experimental - https://launchpad.net/~kubuntu-ppa/+archive/experimental
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 493B3065
#deb http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu natty main

#### Kubuntu Updates - https://edge.launchpad.net/~kubuntu-ppa/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
#deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu natty main

#### LibreOffice 3.3 - http://www.documentfoundation.org/download/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu natty main

#### Liferea Unstable - http://liferea.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 412F055D
deb http://ppa.launchpad.net/liferea/liferea-unstable/ubuntu natty main

#### Medibuntu - http://www.medibuntu.org/ 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb http://packages.medibuntu.org/ natty free non-free

#### Mendeley Desktop - http://www.mendeley.com/
## Run this command: no gpg keys supplied
deb http://www.mendeley.com/repositories/xUbuntu_11.04 /

#### Midori - https://launchpad.net/~midori/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
deb http://ppa.launchpad.net/midori/ppa/ubuntu natty main

#### Miro HD Video Player - http://www.getmiro.com/
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D75E850
deb http://ppa.launchpad.net/pcf/miro-releases/ubuntu natty main

#### MKVToolnix - http://www.bunkus.org/videotools/mkvtoolnix/
## Run this command: wget -q http://www.bunkus.org/gpg-pub-moritzbunkus.txt -O- | sudo apt-key add -
deb http://www.bunkus.org/ubuntu/natty/ ./

#### MongoDB - http://www.mongodb.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen

#### Mozilla Daily Build Team - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu natty main

#### muCommander - http://www.mucommander.com/
## Run this command: sudo wget -O - http://apt.mucommander.com/apt.key | sudo apt-key add - 
deb http://apt.mucommander.com stable main non-free contrib

#### OpenShot - http://www.openshotvideo.com
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B9BA26FA
deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu natty main

#### Opera - http://www.opera.com/
## Run this command: sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
deb http://deb.opera.com/opera/ lenny non-free

#### Opera Beta - http://www.opera.com/
## Run this command: sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
deb http://deb.opera.com/opera-beta/ lenny non-free

#### Oracle 10g DB - http://oss.oracle.com
## Run this command: wget http://oss.oracle.com/el4/RPM-GPG-KEY-oracle  -O- | sudo apt-key add -
deb http://oss.oracle.com/debian unstable main non-free

#### Paissad's Repo - http://deb.paissad.net
## Run this command: wget -q -O - http://deb.paissad.net/public-key.asc | sudo apt-key add -
deb http://deb.paissad.net unstable main contrib non-free personal

#### Pidgin - http://pidgin.im
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu natty main

#### Playdeb - http://www.playdeb.net/
## Run this command: wget -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
deb http://archive.getdeb.net/ubuntu natty-getdeb games

#### PlayOnLinux - http://www.playonlinux.com
## Run this command: wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
deb http://deb.playonlinux.com/ natty main

#### qBittorrent - http://qbittorrent.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 47B4D1C4
deb http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu natty main

#### SABnzbd - http://sabnzbd.org/
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4BB9F05F
deb http://ppa.launchpad.net/jcfp/ppa/ubuntu natty main

#### Terminator - http://www.tenshu.net/terminator/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1BD3A65C
deb http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu natty main

#### Themes for GNOME and Ubuntu - https://edge.launchpad.net/~bisigi/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu natty main

#### Tor: anonymity online - http://www.torproject.org/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 886DDD89 && gpg --export --armor 94C09C7F  | sudo apt-key add -
deb http://deb.torproject.org/torproject.org lucid main

#### Ubuntu Tweak - http://ubuntu-tweak.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu natty main

#### UbuntuGIS (unstable) - http://trac.osgeo.org/ubuntugis/wiki
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 314DF160
deb http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu natty main

#### UNetbootin - http://unetbootin.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu natty main

#### VirtualBox - http://www.virtualbox.org
## Run this command: wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
deb http://download.virtualbox.org/virtualbox/debian natty contrib

#### VLC Media Player  - http://www.videolan.org/vlc/
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb http://ppa.launchpad.net/c-korn/ppa/ubuntu maverick main

#### WebKit Team PPA - https://launchpad.net/~webkit-team/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D9A3C5B
deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu natty main

#### Webmin - http://www.webmin.com
## Run this command: wget http://www.webmin.com/jcameron-key.asc -O- | sudo apt-key add -
deb http://download.webmin.com/download/repository sarge contrib

#### Wine - https://launchpad.net/~ubuntu-wine/+archive/ppa/
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu natty main

#### X Updates - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu natty main

#### Xorg Edgers - https://launchpad.net/~xorg-edgers
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542  
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu natty main

#### Yuuguu - http://yuuguu.com
#deb http://update.yuuguu.com/repositories/apt hardy multiverse


####### 3rd Party Source Repos

#### Audacity (Source) - http://audacity.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys     1024R/BB901940
deb-src http://ppa.launchpad.net/audacity-team/daily/ubuntu natty main

#### AWN (Avant Window Navigator) Testing Packages (Source) - http://awn-project.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
deb-src http://ppa.launchpad.net/awn-testing/ppa/ubuntu natty main

#### Banshee (Source) - https://edge.launchpad.net/~banshee-team
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu natty main

#### Chromium Project (Source) - http://code.google.com/chromium/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E5E17B5
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu natty main

#### DeaDBeeF (Source) - http://deadbeef.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3C8E2A7F
deb-src http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu natty main

#### Deluge BitTorrent (Source) - http://www.deluge-torrent.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 249AD24C
deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu natty main

#### Equinox (Source) - https://launchpad.net/~tiheum/+archive/equinox
## Run this command: sudo apt-get update && sudo apt-get install faenza-icon-theme && sudo apt-get install equinox-theme    
deb-src http://ppa.launchpad.net/tiheum/equinox/ubuntu natty main

#### FBReader (Source) - http://www.fbreader.org/desktop/
## Run this command: http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc -O- | sudo apt-key add -
deb-src http://www.fbreader.org/desktop/debian stable main

#### Flacon (Source) - http://kde-apps.org/content/show.php?content=113388
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
deb-src http://ppa.launchpad.net/flacon/ppa/ubuntu natty main

#### Fritz Fun (ffgtk) (Source) - http://www.tabos.org/ffgtk/index.php
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key 928EDC6B
deb-src http://ppa.launchpad.net/stevi/ppa/ubuntu natty main

#### GCstar (Source) - http://www.gcstar.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5BE6AD9A
deb-src http://ppa.launchpad.net/gcstar/gcstar-dev/ubuntu natty main

#### Glx-Dock / Cairo-Dock (Source) - http://www.glx-dock.org
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
deb-src http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu natty main

#### GNUzilla and IceCat (Source) - http://www.gnu.org/software/gnuzilla/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 
deb-src http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu natty main

#### Gwibber (Daily) (Source) - https://launchpad.net/gwibber
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
deb-src http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu natty main

#### HandBrake Releases (Source) - http://handbrake.fr/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 816950D8
deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu natty main

#### HandBrake Snapshots (Source) - http://handbrake.fr/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 816950D8
deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu natty main

#### Kubuntu Backports (Source) - https://edge.launchpad.net/~kubuntu-ppa/+archive/backports
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu natty main

#### Kubuntu Beta Backports (Source) - https://launchpad.net/~kubuntu-ppa/+archive/beta
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb-src http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu natty main

#### Kubuntu Experimental (Source) - https://launchpad.net/~kubuntu-ppa/+archive/experimental
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 493B3065
deb-src http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu natty main

#### Kubuntu Updates (Source) - https://edge.launchpad.net/~kubuntu-ppa/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb-src http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu natty main

#### LibreOffice 3.3 (Source) - http://www.documentfoundation.org/download/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu natty main

#### Liferea Unstable (Source) - http://liferea.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 412F055D
deb-src http://ppa.launchpad.net/liferea/liferea-unstable/ubuntu natty main

#### Medibuntu (Source) - http://www.medibuntu.org/ 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb-src http://packages.medibuntu.org/ natty free non-free

#### Midori (Source) - https://launchpad.net/~midori/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
deb-src http://ppa.launchpad.net/midori/ppa/ubuntu natty main

#### Miro HD Video Player (Source) - http://www.getmiro.com/
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D75E850
deb-src http://ppa.launchpad.net/pcf/miro-releases/ubuntu natty main

#### MKVToolnix (Source) - http://www.bunkus.org/videotools/mkvtoolnix/
## Run this command: wget -q http://www.bunkus.org/gpg-pub-moritzbunkus.txt -O- | sudo apt-key add -
deb-src http://www.bunkus.org/ubuntu/natty/ ./

#### Mozilla Daily Build Team (Source) - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu natty main

#### OpenShot (Source) - http://www.openshotvideo.com
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B9BA26FA
deb-src http://ppa.launchpad.net/openshot.developers/ppa/ubuntu natty main

#### Paissad's Repo (Source) - http://deb.paissad.net
## Run this command: wget -q -O - http://deb.paissad.net/public-key.asc | sudo apt-key add -
deb-src http://deb.paissad.net unstable main contrib non-free personal

#### Pidgin (Source) - http://pidgin.im
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu natty main

#### qBittorrent (Source) - http://qbittorrent.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 47B4D1C4
deb-src http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu natty main

#### Terminator (Source) - http://www.tenshu.net/terminator/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1BD3A65C
deb-src http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu natty main

#### Themes for GNOME and Ubuntu (Source) - https://edge.launchpad.net/~bisigi/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu natty main

#### Tor: anonymity online (Source) - http://www.torproject.org/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 886DDD89 && gpg --export --armor 94C09C7F  | sudo apt-key add -
deb-src http://deb.torproject.org/torproject.org lucid main

#### Ubuntu Tweak (Source) - http://ubuntu-tweak.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb-src http://ppa.launchpad.net/tualatrix/ubuntu natty main

#### UbuntuGIS (unstable) (Source) - http://trac.osgeo.org/ubuntugis/wiki
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 314DF160
deb-src http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu natty main

#### UNetbootin (Source) - http://unetbootin.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
deb-src http://ppa.launchpad.net/gezakovacs/ppa/ubuntu natty main

#### VLC Media Player  (Source) - http://www.videolan.org/vlc/
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb-src http://ppa.launchpad.net/c-korn/ppa/ubuntu maverick main

#### WebKit Team PPA (Source) - https://launchpad.net/~webkit-team/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D9A3C5B
deb-src http://ppa.launchpad.net/webkit-team/ppa/ubuntu natty main

#### Wine (Source) - https://launchpad.net/~ubuntu-wine/+archive/ppa/
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu natty main

#### X Updates (Source) - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu natty main

#### Xorg Edgers (Source) - https://launchpad.net/~xorg-edgers
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542  
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu natty main



#google
deb http://ppa.launchpad.net/googlegadgets/ubuntu hardy main
deb-src http://ppa.launchpad.net/googlegadgets/ubuntu hardy main

# Google software repository
deb http://dl.google.com/linux/deb/ stable non-free main
# deb http://www.bunkus.org/debian/squeeze/ ./
# deb-src http://www.bunkus.org/debian/squeeze/ ./
deb http://www.bunkus.org/debian/squeeze/ ./
deb-src http://www.bunkus.org/debian/squeeze/ ./
```And this is my old one

```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ro.archive.ubuntu.com/ubuntu/ natty main universe restricted
deb-src http://ro.archive.ubuntu.com/ubuntu/ natty main universe restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ro.archive.ubuntu.com/ubuntu/ natty-updates main universe restricted
deb-src http://ro.archive.ubuntu.com/ubuntu/ natty-updates main universe restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ro.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://ro.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ro.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://ro.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse



deb http://security.ubuntu.com/ubuntu natty-security main universe restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main universe restricted
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://ppa.launchpad.net/s-elser/winelol/ubuntu natty main
deb-src http://ppa.launchpad.net/s-elser/winelol/ubuntu natty main

#google
deb http://ppa.launchpad.net/googlegadgets/ubuntu hardy main
deb-src http://ppa.launchpad.net/googlegadgets/ubuntu hardy main

# Google software repository
deb http://dl.google.com/linux/deb/ stable non-free main
# deb http://www.bunkus.org/debian/squeeze/ ./
# deb-src http://www.bunkus.org/debian/squeeze/ ./
deb http://www.bunkus.org/debian/squeeze/ ./
deb-src http://www.bunkus.org/debian/squeeze/ ./


#interpid

# deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
# deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
# deb http://security.ubuntu.com/ubuntu intrepid-security universe
# deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
# deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
```With the old one i had no problem. Now, if i want to purge/remove libecairo 2, i "must" remove also most of important packages. Of course, it's a bug. I'll post here the screenshot

[[URL=http://i.imgur.com/nlCAo.jpg][IMG]http://i.imgur.com/nlCAol.jpg[/IMG]]("http://imgur.com/nlCAo")[/URL]

---

### Post by bluexrider on 2011-12-09
isn't that the "perl" package you are trying to remove? the  libecairo 2 is down on the list a little further (the Cairo 2D vector graphics library)

---

### Post by editheraven on 2011-12-09
No. I'll post a longer log.

```
editheraven@editheraven-T-Systems-PC-P5LD2-VM:~$ sudo apt-get remove libcairo2
[sudo] password for editheraven: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcommons-collections3-java liblash3 lirc libstdc++5 junit4
  vim-addon-manager libecj-java bicyclerepair libasm3-java python-renderpm
  libgcj-bc librcc0 librcd0 libxine1-x libfontforge1 libbinio1ldbl
  deluge-common libxfce4util-bin twolame libbluray0 libcommons-el-java
  libaudclient2 libsvga1 sp-auth python-pygame libresid-builder0c2a junit
  libcommons-compress-java libxine1-misc-plugins libregexp-java libavidemux0
  avidemux-plugins-common mplayer libcdt4 libjasper-java python-dev
  libcommons-httpclient-java python-lxml libaften0 python-reportlab-accel
  libservlet2.4-java libxine1-bin liblucene2-java mencoder
  libboost-thread1.42.0 pidgin-data libslf4j-java eclipse-platform-data
  exuberant-ctags libboost-date-time1.42.0 libgcj11 libxfce4util4
  cairo-dock-data ruby1.8 libdb4.7-java-gcj libcue1 libtorrent-rasterbar6
  setserial libxfce4util-common ant python-numpy ruby libcommons-logging-java
  libcommons-codec-java libxine1-ffmpeg jarwrapper libequinox-osgi-java
  python-compizconfig hal libgcj-common libsdl-ttf2.0-0 libmikmod2
  libjaxp1.3-java icedax avidemux-common libjetty-java jython libjline-java
  libxerces2-java libwmf-bin libspiro0 netpbm libmowgli2 libmagick++3
  libcommons-beanutils-java libfluidsynth1 python-uniconvertor libportmidi0
  libdb-je-java libreadline-java libsdl-mixer1.2 pulseaudio-module-zeroconf
  libmagickwand3 libsidplay2 fastjar libdb4.7-java gcj-4.5-jre-lib
  libcommons-digester-java libvdpau1 pulseaudio-module-gconf libnetpbm10
  gnome-commander-data libhamcrest-java libjtidy-java imagemagick
  libicu4j-java libgc1c2 libgconfmm-2.6-1c2 libgraph4 hal-info libmcs1
  libuninameslist0 librcd-dev xfconf libjsch-java cairo-dock-plug-ins-data
  libimlib2 libxfconf-0-2 perlmagick ant-optional python-reportlab
  libpathplan4 libetpan13 python2.7-dev python-libtorrent
  libboost-python1.42.0 gcj-4.5-base libxine1-console libxine1 libsmpeg0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  akonadi-server apturl-kde gsfonts-x11 kdepim-runtime kdepimlibs-kio-plugins
  kdesudo libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4
  libakonadiprotocolinternals1 libkabc4 libkcal4 libkimap4 libkldap4 libkmime4
  libknewstuff2-4 libkpimutils4 libkprintutils4 libkresources4
  libmailtransport4 libmicroblog4 mysql-client-core-5.1 mysql-server-core-5.1
  python-kde4 software-properties-kde sun-java6-bin sun-java6-jre
Suggested packages:
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts ttf-kochi-gothic
  ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho ttf-arphic-uming
The following packages will be REMOVED:
  acroread adobeair aisleriot alacarte appmenu-gtk apport-gtk apturl at-spi
  audacious audacious-plugins avidemux avidemux-plugins-gtk bamfdaemon baobab
  boot-repair boot-repair-common boot-repair-ubuntu brasero brasero-cdrkit
  browser-plugin-gnash browser-plugin-lightspark checkbox-gtk
  cnijfilter-mp250series compiz compiz-fusion-plugins-extra
  compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-plugins-extra
  compiz-plugins-main compizconfig-settings-manager computer-janitor-gtk conky
  conky-all dconf-tools default-jdk default-jre deluge deluge-gtk divfix++
  easytag eclipse eclipse-cdt eclipse-jdt eclipse-pde eclipse-platform
  eclipse-plugin-cvs eclipse-pydev eclipse-rcp eclipse-sdk emerald empathy eog
  evince evolution evolution-data-server evolution-exchange
  evolution-indicator evolution-plugins evolution-webcal exo-utils file-roller
  firefox firefox-globalmenu firefox-gnome-support flashplugin-installer
  fontforge frei0r-plugins gamix gbrainy gcalctool gconf-editor gdm
  gdm-guest-session gedit gimp ginn gir1.2-appindicator-0.1 gir1.2-freedesktop
  gir1.2-gtk-2.0 gir1.2-panelapplet-3.0 gir1.2-pango-1.0 gir1.2-vte-0.0 gksu
  gnash gnash-common gnome-about gnome-accessibility-themes gnome-alsamixer
  gnome-applets gnome-bluetooth gnome-brave-icon-theme gnome-codec-install
  gnome-colors-common gnome-commander gnome-control-center
  gnome-device-manager gnome-disk-utility gnome-dust-icon-theme
  gnome-games-common gnome-human-icon-theme gnome-icon-theme
  gnome-illustrious-icon-theme gnome-keyring gnome-mag gnome-mahjongg
  gnome-media gnome-media-player gnome-menus gnome-nettool
  gnome-noble-icon-theme gnome-orca gnome-panel gnome-panel-bonobo
  gnome-power-manager gnome-pulse-applet gnome-screensaver gnome-screenshot
  gnome-search-tool gnome-session gnome-session-bin gnome-session-canberra
  gnome-settings-daemon gnome-sudoku gnome-system-log gnome-system-monitor
  gnome-system-tools gnome-terminal gnome-themes-selected gnome-themes-ubuntu
  gnome-user-guide gnome-user-share gnome-wise-icon-theme gnomebaker gnomine
  gparted grub-customizer gstreamer0.10-plugins-bad gstreamer0.10-plugins-good
  gstreamer0.10-x gtk-recordmydesktop gtk2-engines gtk2-engines-murrine
  gtk2-engines-pixbuf gucharmap gvfs gvfs-backends gvfs-fuse gwibber
  gwibber-service gwibber-service-facebook gwibber-service-identica
  gwibber-service-twitter humanity-icon-theme ibus ibus-gtk ibus-pinyin
  ibus-table icedtea-netx icedtea-plugin icedtea6-plugin indicator-applet
  indicator-applet-appmenu indicator-applet-complete indicator-applet-session
  indicator-application indicator-appmenu indicator-datetime indicator-me
  indicator-messages indicator-session indicator-sound inkscape jockey-gtk
  language-selector-gnome libaccess-bridge-java libaccess-bridge-java-jni
  libappindicator0.1-cil libappindicator1 libaudcore1 libavahi-ui0 libbamf0
  libbonoboui2-0 libbrasero-media1 libcairo-gobject2 libcairo-perl
  libcairo-ruby1.8 libcairo2 libcairomm-1.0-1 libcanberra-gtk-module
  libcanberra-gtk0 libcheese-gtk18 libcodeblocks0 libcryptui0 libcvaux2.1
  libdbusmenu-gtk3 libdevhelp-2-1 libecal1.2-8 libedata-cal1.2-10
  libedataserverui1.2-11 libemeraldengine0 libevdocument3 libevolution
  libevview3 libexo-1-0 libgail-common libgail-gnome-module libgail18 libgcr0
  libgdiplus libgdk-pixbuf2-ruby1.8 libgdl-1-3 libgdraw4 libgdu-gtk0
  libgegl-0.0-0 libgimp2.0 libgksu2-0 libglade2-0 libglade2-ruby
  libglade2-ruby1.8 libglade2.0-cil libglade2.0-cil-dev libglademm-2.4-1c2a
  libgladeui-1-11 libgnome-bluetooth8 libgnome-desktop-2-17
  libgnome-device-manager0 libgnome-media0 libgnome-window-settings1
  libgnome2.24-cil libgnomecanvas2-0 libgnomekbd4 libgnomeui-0 libgoocanvas3
  libgstfarsight0.10-0 libgtk-3-0 libgtk-3-bin libgtk-sharp-beans-cil
  libgtk-vnc-1.0-0 libgtk2-perl libgtk2-ruby1.8 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-cil libgtk2.0-cil-dev libgtkglext1 libgtkhtml-editor0
  libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtkspell0
  libgtkspell3-0 libgucharmap7 libgvc5 libgweather1 libgwibber-gtk2
  libgwibber1 libgwibber2 libhighgui2.1 libido-0.1-0 libindicate-gtk2
  libindicator3 liblaunchpad-integration1 liblaunchpad-integration1.0-cil
  libmagickcore3-extra libmetacity-private0 libmlt++3 libmlt3
  libmono-addins-gui0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil
  libmono-cil-dev libmono-system-data-linq2.0-cil
  libmono-system-runtime1.0-cil libmono-system-runtime2.0-cil
  libmono-system-web-mvc1.0-cil libmono-system-web-mvc2.0-cil
  libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-wcf3.0-cil
  libmono-winforms1.0-cil libmono-winforms2.0-cil libmono1.0-cil
  libmono2.0-cil libmultisync-plugin-backup libmultisync-plugin-evolution
  libmultisync-plugin-irmc libnautilus-extension1 libnotify0.4-cil libnotify1
  libnunit-cil-dev libnunit2.4-cil libnux-0.9-0 liboverlay-scrollbar-0.1-0
  libpanel-applet-3-0 libpanel-applet2-0 libpango-perl libpango1-ruby1.8
  libpango1.0-0 libpangomm-1.4-1 libpolkit-gtk-1-0 libpoppler-glib6 libpurple0
  librcc-dev librccgtk2-0 libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress
  libreoffice-math libreoffice-style-human libreoffice-writer librsvg2-2
  librsvg2-common libsexy2 libswt3.2-gtk-java libswt3.2-gtk-jni
  libsyncdaemon-1.0-1 libtelepathy-farsight0 libubuntuone-1.0-1
  libubuntuone1.0-cil libunique-1.0-0 libunity-misc0 libvte9 libwebkit1.1-cil
  libwebkitgtk-1.0-0 libwnck22 libwxgtk2.8-0 libxfce4ui-1-0 light-themes
  lightspark-common melt metacity mjpegtools mkvtoolnix-gui mono-2.0-devel
  mono-devel mono-xsp2 mono-xsp2-base monodoc-base monodoc-browser
  monodoc-manual mousetweaks multisync nautilus nautilus-sendto
  nautilus-sendto-empathy nautilus-share network-manager-gnome
  network-manager-pptp-gnome notify-osd onboard openjdk-6-jdk openjdk-6-jre
  overlay-scrollbar padevchooser paman paprefs pavucontrol pavumeter pidgin
  pidgin-guifications pidgin-libnotify pidgin-musictracker pinentry-gtk2
  pitivi plymouth-label plymouth-theme-ubuntu-logo policykit-1-gnome pychess
  python-appindicator python-aptdaemon-gtk python-aptdaemon.gtk3widgets
  python-aptdaemon.gtkwidgets python-cairo python-eggtrayicon python-farsight
  python-glade2 python-gmenu python-gnome2 python-gnomeapplet
  python-gnomecanvas python-gnomedesktop python-gnomekeyring
  python-gobject-cairo python-gtk2 python-gtksourceview2 python-gtkspell
  python-ibus python-indicate python-launchpad-integration python-mlt3
  python-notify python-papyon python-pyatspi python-pygoocanvas python-rsvg
  python-ubuntuone-client python-ubuntuone-control-panel python-uno
  python-virtkey python-vte python-webkit python-wnck python-wxgtk2.8
  python-wxversion sat4j scangearmp-common scangearmp-mp250series seahorse
  sessioninstaller shotwell simple-scan software-center
  software-properties-gtk soundconverter ssh-askpass-gnome startupmanager
  synaptic system-config-printer-gnome telepathy-butterfly telepathy-haze
  thewidgetfactory tint2 tomboy transmission-gtk tsclient tv-maxe
  ubuntu-artwork ubuntu-docs ubuntu-mono ubuntu-sso-client ubuntu-tweak
  ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel
  ubuntuone-control-panel-gtk unity unity-asset-pool unity-place-applications
  unity-place-files update-manager update-notifier usb-creator-gtk vinagre
  vino vlc-plugin-notify winff winff-doc xdg-user-dirs-gtk xfce4-panel
  xul-ext-ubufox xulrunner-1.9.2 yelp zeitgeist zeitgeist-datahub
  zeitgeist-extension-fts zenity
The following NEW packages will be installed:
  akonadi-server apturl-kde gsfonts-x11 kdepim-runtime kdepimlibs-kio-plugins
  kdesudo libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4
  libakonadiprotocolinternals1 libkabc4 libkcal4 libkimap4 libkldap4 libkmime4
  libknewstuff2-4 libkpimutils4 libkprintutils4 libkresources4
  libmailtransport4 libmicroblog4 mysql-client-core-5.1 mysql-server-core-5.1
  python-kde4 software-properties-kde sun-java6-bin sun-java6-jre
0 upgraded, 28 newly installed, 464 to remove and 0 not upgraded.
Need to get 50.2 MB of archives.
After this operation, 1,396 MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
```

---

### Post by editheraven on 2011-12-09
Bump. If i run gtkorphan it shows almost all needed packages as orphaned.If i reinstall apt-get and synaptic, i'll solve it?

---

