---
title: "Enabling Audio on Zekr?"
date: 2009-08-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by n3had on 2009-08-20
I've installed the application via synaptic

    *  To add the Zekr repository, run the following command in a terminal: 

sudo gedit /etc/apt/sources.list

    * Add ONLY ONE of the following lines based on your OS (Ubuntu Hardy 8.04, Ubuntu Intrepid 8.10) at the end of /etc/apt/sources.list 

deb [http://ppa.launchpad.net/zekr/ubuntu](http://ppa.launchpad.net/zekr/ubuntu) hardy main
deb [http://ppa.launchpad.net/zekr/ubuntu](http://ppa.launchpad.net/zekr/ubuntu) intrepid main

    * To install Zekr and the necessary fonts, run the following commands in the terminal: 

[B]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EF400C7C
sudo apt-get update
sudo apt-get install zekr ttf-me-quran ttf-sil-scheherazade
sudo apt-get install ttf-farsiweb [/B]
*sudo apt-get install flashplugin-nonfree*



AND as i've already installed flash 64bitalpha manually i don't want to *sudo apt-get install flashplugin-nonfree* and if don't install it i don't have audio playback feature.. 

Any help?

thanks
nehad

---

