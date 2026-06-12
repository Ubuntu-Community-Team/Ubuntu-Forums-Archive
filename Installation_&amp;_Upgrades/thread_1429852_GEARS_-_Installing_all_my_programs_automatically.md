---
title: "GEARS - Installing all my programs automatically"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by kaffemonster on 2010-03-14
I guess I do too many re-installs since I took the time to write this, but I wanted a script to take care of all the tedious installs I do after installing Ubuntu. I'll keep adding to the script as I need it to restore my settings, preferences etc. 

```
## GEARS - Grand Elaborate Automagic Runonce Script ##
## Originally written by Soren Siim Nielsen ##
## Released under Creative Commons Attribution-Noncommercial-Share Alike 2.5 Generic - http://creativecommons.org/licenses/by-nc-sa/2.5/##
## Must be run with root access ##

## Add repositories ##
	## Pidgin ##
	apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
	echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu \     `lsb_release --short --codename` main | \tee /etc/apt/sources.list.d/pidgin-ppa.list
	
	## Ubuntuzilla ##
	echo "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | tee -a /etc/apt/sources.list > /dev/null
	
	## Virtualbox ##
	wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
	echo "\ndeb http://download.virtualbox.org/virtualbox/debian karmic non-free" | tee -a /etc/apt/sources.list > /dev/null	
	
## Update APT ##
apt-get update

## Add programs ##
apt-get install -y build-essential smbfs wine unetbootin virtualbox-3.1 pidgin ubuntu-restricted-extras filezilla gparted exaile ufraw scite vlc audacious sound-juicer thunderbird-mozilla-build firefox-mozilla-build mozilla-traybiff-common adblock-plus nautilus-image-converter soundconverter --force-yes

## Remove unwanted programs ##
apt-get remove -y empathy

## Download and install Bibble5Pro from my server ##
wget http://www.bagkameraet.dk/stuff/bibble5pro-5.0.2a_i386.deb
dpkg -i bibble5pro-5.0.2a_i386.deb

## Clean up APT ##
apt-get autoremove

## Fix sound bug on my HP Probook 5310M ##
echo -e "\nalias snd-card-0 snd-hda-intel \nalias sound-slot-0 snd-hda-intel \noptions snd-hda-intel model=dell-m4-1 \noptions snd-hda-intel enable_msi=1"  | tee -a /etc/modprobe.d/alsa-base.conf > /dev/null

## Install latest Java - I basically just scripted this guide: http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10 ##
wget http://www.bagkameraet.dk/stuff/jre-6u18-linux-i586.bin
sudo mkdir /opt/java
sudo mkdir /opt/java/32
sudo mv ~/jre-6u18-linux-i586.bin /opt/java/32
sudo chmod 755 /opt/java/32/jre-6u18-linux-i586.bin
cd /opt/java/32
sudo ./jre-6u18-linux-i586.bin
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jre1.6.0_18/bin/java" 1
## repeating the above, incase we're upgrading from a previous version
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jre1.6.0_18/bin/java" 1
sudo update-alternatives --set java /opt/java/32/jre1.6.0_18/bin/java
## installing Firefox plugin
mkdir ~/.mozilla/plugins
## Getting rid of iced tea plugin, if installed
sudo apt-get remove icedtea6-plugin
## Out with the old, in with the new
rm ~/.mozilla/plugins/libjavaplugin_oji.so
rm ~/.mozilla/plugins/libnpjp2.so
# ln -s /opt/java/32/jre1.6.0_18/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins/ ##For Firefox 3.5.X
ln -s /opt/java/32/jre1.6.0_18/lib/i386/libnpjp2.so ~/.mozilla/plugins/ ##For Firefox 3.6.X and newer


```

---

### Post by oldfred on 2010-03-14
I am working on something similar but I am using my history from my Karmic install. I had multiple sources of things to add and link, some worked better than others but I copied my history and plan to convert it to my bash file. I see a few things in yours that I used but I also have a lot of unique things to how I have my drives/partitions set up. 

It definitely helps one to understand and document what works or does not work.

---

