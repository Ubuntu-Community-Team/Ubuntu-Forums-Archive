---
title: "cant install deb packeges from cache"
date: 2018-03-26
forum: Installation &amp; Upgrades
---

### Post by behelme on 2018-03-26
Hello !

[COLOR=#212121][FONT=arial]I installed 16.04 from dvd-iso and performed the updates (sudo apt-get update && sudo apt-get upgrade). Then I took all the deb packages from /var/cache/apt/archives and copied it to the USB flash drive.

Then I installed 16.04 on another computer and try to update it with the command: sudo dpkg -i ./*.deb, but some packages do not want to be put right away. 
If i repeat the same command again, then all ok
I cant use internet on that computer - only than usb flash drive.

How to install all these packages in rigth way without rerun same command twice ?

One of these installation errors:

[/FONT][/COLOR][FONT=monospace][COLOR=#000000]Preparing to unpack .../libreoffice-common_1%3a5.1.6~rc2-0ubuntu1~xenial3_all.deb ...[/COLOR]
Unpacking libreoffice-common (1:5.1.6~rc2-0ubuntu1~xenial3) over (1:5.1.2-0ubuntu1) ...
dpkg: regarding .../libreoffice-core_1%3a5.1.6~rc2-0ubuntu1~xenial3_amd64.deb containing libreoffice-core:
 libreoffice-core breaks libreoffice-draw (<< 1:5.1.6~rc2-0ubuntu1~xenial3)
  libreoffice-draw (version 1:5.1.2-0ubuntu1) is present and installed.

dpkg: error processing archive ./deb0/libreoffice-core_1%3a5.1.6~rc2-0ubuntu1~xenial3_amd64.deb (--install):
 installing libreoffice-core would break libreoffice-draw, and
 deconfiguration is not permitted (--auto-deconfigure might help)

[/FONT]

---

### Post by behelme on 2018-03-26
I found solution: sudo DEBIAN_FRONTEND=noninteractive apt install ./*.deb

---

