---
title: "apt-get update W: Duplicate sources.list entry Problem"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by biebo on 2013-02-06
hi all,

I am running Ubuntu Linaro on ARM. I have to install Mali GPU driver and for that I need the linux headers. To get the kernel headers I need to sudo apt-get update

apt-get update doesn't work. Any help in this regard. Below is the output.

> 
linaro@linaro-ubuntu-desktop:~$ sudo apt-get update
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates Release.gpg                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise Release    
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates Release                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/universe Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/main armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/universe armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/main TranslationIndex
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/universe TranslationIndex
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/universe Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/main armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/universe armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/main TranslationIndex
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/main Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/universe Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/main armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/universe armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/main Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/universe Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/main Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/universe Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/main Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/universe Translation-en
Reading package lists... Done
W: Duplicate sources.list entry [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) precise/main armhf Packages (/var/lib/apt/lists/ports.ubuntu.com_ubuntu-ports_dists_precise_main_binary-armhf_Packages)
W: Duplicate sources.list entry [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) precise/universe armhf Packages (/var/lib/apt/lists/ports.ubuntu.com_ubuntu-ports_dists_precise_universe_binary-armhf_Packages)
W: Duplicate sources.list entry [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) precise-security/main armhf Packages (/var/lib/apt/lists/ports.ubuntu.com_ubuntu-ports_dists_precise-security_main_binary-armhf_Packages)
W: Duplicate sources.list entry [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) precise-security/universe armhf Packages (/var/lib/apt/lists/ports.ubuntu.com_ubuntu-ports_dists_precise-security_universe_binary-armhf_Packages)
W: Duplicate sources.list entry [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) precise-updates/main armhf Packages (/var/lib/apt/lists/ports.ubuntu.com_ubuntu-ports_dists_precise-updates_main_binary-armhf_Packages)
W: Duplicate sources.list entry [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) precise-updates/universe armhf Packages (/var/lib/apt/lists/ports.ubuntu.com_ubuntu-ports_dists_precise-updates_universe_binary-armhf_Packages)
W: You may want to run apt-get update to correct these problems




---

### Post by biebo on 2013-02-06
ok I got is working with 

cd /etc/apt/sources.list.d
sudo rm -fr hwpack*

but still the kernel headers couldn't be installed


> 
[email]linaro@linaro-ubuntu-desktop:/etc/apt/sources.list[/email].d$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.6.2
E: Couldn't find any package by regex 'linux-headers-3.6.2'
[email]linaro@linaro-ubuntu-desktop:/etc/apt/sources.list[/email].d$ 



---

