---
title: "I wrote my first script!!!"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by Stray Wolf on 2011-01-18
Yeah, I'm sure this script needs improvements but it runs just fine.  I've always thought of myself as computer illiterate so this is an accomplishment for me.  I use it on fresh installs for quicker set up.  I know this is elementary compared to the coding most of you folks here do.  But it's a good start for me.  If anyone has any suggestions I want to hear them.

echo "deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) $(lsb_release -sc) main ## Cairo-Dock-PPA" | sudo tee -a /etc/apt/sources.list
    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
    sudo apt-get update

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

sudo apt-get install cairo-dock-core

sudo apt-get install cario-dock-plug-ins

sudo apt-get install cario-dock-plug-ins-integration

sudo apt-get install sun-java6-jre sun-java6-plugin

sudo apt-get install ubuntu-restricted-extras

sudo apt-get install libdvdcss2

sudo apt get install thunderbird

sudo apt-get install skype

sudo apt-add-repository ppa:pidgin-developers/ppa

sudo apt-get update

sudo apt-get install pidgin

sudo apt-get install pidgin-plugin-pack

sudo apt-get install digikam

sudo apt-get install showfoto

sudo apt-get install hardinfo

---

