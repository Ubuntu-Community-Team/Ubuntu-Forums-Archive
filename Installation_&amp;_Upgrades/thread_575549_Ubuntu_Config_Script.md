---
title: "Ubuntu Config Script"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by nmckenna on 2007-10-14
Everyone, 

I've been using Ubuntu for a while now and over that time I've bolted together a basic shell script, from posts here on the forum and elsewhere on the net, to update a clean Ubuntu install with all the packages I find useful on a new system. Things like different codecs, mplayer, subversion and a few others.

With 7.10 coming out I pulled up my script and gave it a clean up for Gutsy so I thought I'd post it here in case anyone found it useful and to see if there were any ideas for interesting or useful stuff that could be added to it.

Nicol

```


#!/bin/sh

## This script is intended to be run on a clean install of Ubuntu 7.10 (Gutsy)
## It configures the Ubuntu install for a new user and sets up the following.

#################################################################################
## 1. Update sources list.
## 1.1 Add medibuntu repository
## -----
## 2. Archiving Tools
## 2.1 Cabextract
## 2.2 Rar & unrar
## -----
## 3. Multimedia Setup
## 3.1 Standard Codecs
## 3.2 DVD Playback
## 3.3 Remove Totem FF Plugins
## 3.4 Install mplayer + codecs  (http://www.mplayerhq.hu/design7/dload.html)
## 3.5 Install VLC
## -----
## 4. Fonts
## 4.1 Install Microsoft fonts
## 4.2 Install third party fonts
## -----
## 5. Document handling
## 5.1 Install Acrobat Reader + Mozilla plugin
## -----
## 6. Development
## 6.1 Install meld
## 6.2 Install Subversion
## -----
## 7. Internet
## 7.1 Install Flash plugin
## 7.2 Install JRE
## -----
## 8. Security
## 8.1 Install Truecrypt
## -----
## 9. Utilities
## 9.1 Install Emacs
## 9.2 Install RecordMyDesktop + GTK Frontend
#################################################################################

## 1. Update Sources list
## 1.1 Add medibuntu repository
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get update

## 2. Archiving Tools
## 2.1 Cabextract
sudo apt-get -y install cabextract 
## 2.1 Rar & unrar
sudo apt-get -y install rar
sudo apt-get -y install unrar


## 3. Multimedia Setup
## 3.1 Standard Codecs
sudo apt-get -y install w32codecs
sudo apt-get -y install libxine1-ffmpeg 
sudo apt-get -y install gstreamer0.10-plugins-base 
sudo apt-get -y install gstreamer0.10-plugins-good 
sudo apt-get -y install gstreamer0.10-plugins-bad 
sudo apt-get -y install gstreamer0.10-plugins-ugly
sudo apt-get -y install gstreamer0.10-pitfdll
sudo apt-get -y install gstreamer0.10-ffmpeg
sudo apt-get -y install gstreamer0.10-plugins-bad-multiverse
sudo apt-get -y install gstreamer0.10-plugins-ugly-multiverse

## 3.2 DVD Playback
sudo apt-get -y install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh

## 3.3 Remove Totem plugins from Firefox
sudo apt-get remove -y totem-mozilla

## 3.4 Install mplayer + codecs
sudo apt-get -y install mplayer 
sudo apt-get -y install mplayer-fonts
sudo apt-get -y install libxine-extracodecs
sudo apt-get -y install mozilla-mplayer
## Get the latest essential codec pack from the mplayer site (http://www.mplayerhq.hu/design7/dload.html)
wget http://www4.mplayerhq.hu/MPlayer/releases/codecs/essential-20061022.tar.bz2
tar -xjf essential-20061022.tar.bz2
sudo mv essential-20061022/* /usr/lib/win32
rm essential-20061022.tar.bz2
rm -rf essential-20061022

## 3.5 Install VLC
sudo apt-get -y install vlc 
sudo apt-get -y vlc-plugin-*

## 4. Fonts
## 4.1 Install Microsoft fonts
sudo apt-get -y install msttcorefonts 

## 4.2 Install third party fonts
sudo apt-get -y install gsfonts-other 
sudo apt-get -y install t1-xfree86-nonfree 
sudo apt-get -y install ttf-f500 
sudo apt-get -y install ttf-isabella 
sudo apt-get -y install ttf-larabie-deco 
sudo apt-get -y install ttf-larabie-straight 
sudo apt-get -y install ttf-larabie-uncommon 
sudo apt-get -y install ttf-staypuft 
sudo apt-get -y install ttf-summersby
sudo apt-get -y install ttf-ubuntu-title 
sudo apt-get -y install ttf-xfree86-nonfree 
sudo apt-get -y install xfonts-artwiz 
sudo apt-get -y install xfonts-intl-european

## 5. Document handling
## 5.1 Install Acrobat Reader + Mozilla plugin
sudo apt-get -y install acroread 
sudo apt-get -y install mozilla-acroread 
sudo apt-get -y install acroread-plugins

## 6. Development
## 6.1 Install Meld
sudo apt-get -y install meld 

## 6.2 Install Subversion
sudo apt-get -y install subversion

## 7. Internet
## 7.1 Install Flash plugin
sudo apt-get -y install flashplugin-nonfree

## 7.2 Install JRE
sudo apt-get -y install sun-java6-jre
sudo apt-get -y install sun-java6-plugin

## 8. Security
## 8.1 Install Truecrypt
wget http://www.truecrypt.org/downloads/truecrypt-4.3a-ubuntu-7.04-x86.tar.gz
tar -xvf truecrypt-4.3a-ubuntu-7.04-x86.tar.gz
sudo apt-get -y install dmsetup
sudo dpkg -i ./truecrypt-4.3a/truecrypt_4.3a-0_i386.deb
rm -rf truecrypt-4.3a
rm truecrypt-4.3a-ubuntu-7.04-x86.tar.gz

## 9. Editors
## 9.1 Install Emacs
sudo apt-get -y install emacs

## 9.2 Install RecordMyDesktop + GTK Frontend
sudo apt-get -y install recordmydesktop
sudo apt-get -y install gtk-recordmydesktop

## Finally do an upgrade to refresh everything.
sudo apt-get upgrade -y



```

---

### Post by K.Mandla on 2007-10-24
Moved to Installations and Upgrades.

---

