---
title: "IPXE boot (all)buntu installation"
date: 2016-02-05
forum: Installation &amp; Upgrades
---

### Post by LMH1 on 2016-02-05
```
[INDENT] sudo apt-get install gparted
 parted -a optimal /dev/sda parted -a optimal /dev/sda
(parted) mklabel mkpart primary ext2 0% 100% set 1 lvm on *sudo* add-apt-repository ppa:ubuntu-desktop/ubuntu-make
 sudo *apt-get install ubuntu*-*desktop*
 *sudo [I]apt-get install kubuntu*-*desktop*[/I]
 *[I]add-apt-repository ppa:xubuntu-dev/[I]xfce*-4.12 *sudo apt-get* update[/I][/I]
 *sudo [I]apt-get install [I][I]xubuntu-dev/[I]xfce*-4.12[/I][/I][/I][/I]
 sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video sudo apt-get install linux-rt
 sudo apt-get install linux-lowlatency linux-lowlatency-pae linux-lowlatency-headers-3.8.0-19 sudo add-apt-repository ppa:tualatrix/ppa
 sudo add-apt-repository ppa:gwibber-daily/ppa sudo apt-get update
sudo apt-get install timidity timidity-interfaces-extra
sudo apt-get install prboom freedoom timidity timidity-interfaces-extra
sudo apt-get install dosbox
sudo apt-get install wine HQ
sudo apt-get install pinball
 
[/INDENT]

```

How to i make this script in ubuntu (Bootloader)?
Because i want to try IPXE
[http://ipxe.org/](http://ipxe.org/)
Can someone help me how to set it up?

Do i need "sudo -i *apt*-*get install lubuntu*-*core apt*-*get* dist-upgrade *apt*-*get* autoclean" to install linux core first?

[URL="https://gist.github.com/robinsmidsrod/2234639"]Bootstrapping full iPXE native menu with customizable default option  with timeout (also includes working Ubuntu 12.04 preseed install)

Its it some like this i should try?
[/URL]

---

