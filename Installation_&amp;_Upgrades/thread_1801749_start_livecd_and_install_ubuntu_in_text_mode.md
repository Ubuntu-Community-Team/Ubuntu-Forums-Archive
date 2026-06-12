---
title: "start livecd and install ubuntu in text mode"
date: 2011-07-11
forum: Installation &amp; Upgrades
---

### Post by linux_ub on 2011-07-11
Managed to install ubuntu from remote with GUI
cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"



**_ubuntu computer_**
[COLOR="Green"]apt-get install openssh-server
sudo su
passwd ubuntu
[/COLOR]
**_remote computer_**
s[COLOR="green"]sh ubuntu -X @192.168.0.4
./ubuquity # Installer launches[/COLOR]

Is it possible to run the installer remote in text mode?

Thanks in advance :-)

---

