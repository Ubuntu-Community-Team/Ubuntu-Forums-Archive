---
title: "I want your apt-get..."
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by sr_guy on 2010-07-27
During a brand new install of a new distro (like the upcoming 10.10), I tend to use apt-get to install most of my apps. I saved my list, and am sharing it here. My hopes is that others will share their compiled list too, in case there are other apps out there that I was unaware of. 

```

apt-get install mythtv-frontend mythtv-common mythtv mythtv-transcode-utils mythtv-theme-titivillus-osd mythtv-database mythtv-theme-mythbuntu mythtv-theme-projectgrayhem-osd mythtv-backend mythtv-backend-master mythtv-theme-iulius-osd mythtvfs mythtv-doc mythtv-status mythbuntu-control-centre

apt-get install record my desk musescore streamtuner audacious recordmydesktop gtk-recordmydesktop

sudo apt-get install cvs build-essential automake autoconf bison flex libtool libncurses5-dev libssl-dev php5 php5-cli php5-curl php5-gd php5-mysql mysql-server php-pear php-db curl sox apache2 subversion libssl-dev libmysqlclient15-dev module-assistant dahdi dahdi-dkms dahdi-linux dahdi-source libmysql++-dev


 apt-get -y install gparted unetbootin pitivi gopchop openmovieeditor gpodder gtkpod avidemux kdenlive amsn deluge-torrent dvdrip miro brasero mldonkey-gui mldonkey-server compiz wine gimp openssh-server


```

---

### Post by oldfred on 2010-07-28
I reinstall everything from my previous install.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

I also have a script. The first part was from someone here but I forgot to save a link or who It was, so I cannot give credit. I then added my list of stuff to install. Anything I specifically install is redundant as it will be in my ubuntu-files.

dpkg --set-selections < ubuntu-files
#dselect
apt-get -y update
apt-get dselect-upgrade

---

### Post by u-slayer on 2010-07-28
I wrote a script to log everything I install. It also saves on typing. 

agi:
```

#!/bin/sh
#install program and log name

apt-get install $* && echo "$*" >> apt.log


```

---

### Post by u-slayer on 2010-07-28
#Install everything in this file: apt-get install `sed -e '/^#/d;s/#.*//' apt.log | tr '\n' ' '`
#(ignores comments)

#a/v
vlc soundconverter mplayer normalize-audio festival avidemux 
ubuntu-restricted-extras #mp3, dvd, codecs
banshee faad mpg321 mencoder gtkpod abcde

#system
portmap nfs-common nfs-kernel-server lvm2 rar cksfv hddtemp xfsprogs p7zip unrar sysinfo
meld okular md5deep smartmontools gparted

#file management
krusader nslint fdupes

sharutils	#Make archives to send over email
#sun-java6-bin
#sun-java6-bin	#broken?
#sun-java6-jdk
pv
gddrescue

#graphics
inkscape mkvtoolnix-gui

#internet
flashplugin-installer deluge vncviewer macchanger checkgmail

#coding
g++ gfortran gnuplot scite

#other
speedcrunch
ghex
wine
pdfedit
screenlets
compizconfig-settings-manager
alltray
lynx-cur
hashalot
gocr







#Installed later:
epiphany-browser
xtrlock
ksshaskpass
virtualbox-ose-qt
fdupes
wine cabextract binfmt-support
gimp
ffmpeg
kaffeine
smplayer

---

### Post by u-slayer on 2010-07-28
This fixes a lot of things in ubuntu.

#gconf fixes (run as user)

#Disable update manager pop up
gconftool -s --type bool /apps/update-notifier/auto_launch false

#No icons on desktop
gconftool-2 --type=Boolean --set /apps/nautilus/preferences/show_desktop false

#CTRL-ALT-DELETE
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

############################ 10.04 Fixes
#Buttons go on the right!
#[http://www.ubuntugeek.com/mark-shuttleworths-response-to-left-side-button-criticisms.html](http://www.ubuntugeek.com/mark-shuttleworths-response-to-left-side-button-criticisms.html)
gconftool-2 --set /apps/metacity/general/button_layout --type string “menu:minimize,maximize,close,spacer”

#Text address bar
#[http://www.webupd8.org/2010/05/use-text-mode-location-bar-in-nautilus.html](http://www.webupd8.org/2010/05/use-text-mode-location-bar-in-nautilus.html)
gconftool-2 --type=Boolean --set /apps/nautilus/preferences/always_use_location_entry true


#########own the home directory
sudo chown -R $user:$user /home

---

