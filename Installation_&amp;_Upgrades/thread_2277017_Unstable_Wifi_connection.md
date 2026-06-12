---
title: "Unstable Wifi connection"
date: 2015-05-06
forum: Installation &amp; Upgrades
---

### Post by Archana_Hegde on 2015-05-06
[COLOR=#444444][FONT=Lato][SIZE=2]in my   dell laptop, ([/SIZE][COLOR=#222222][FONT=Verdana]Intel® Core™ i3 CPU M 330 @ 2.13GHz × 4, [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]Gallium 0.4 on AMD RV710, [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]64-bit,Ubuntu 14.04 LTS_)_[/FONT][/COLOR][COLOR=#222222][FONT=Verdana] [/FONT][/COLOR]wireless is not working in Ubuntu 14.04.
The wireless is not even displayed in the network settings.
Installed Ubuntu 14.04.1 as it has the latest kernel updates for wireless drivers.
The wireless works now, but it has very frequent disconnection.
I just found some commands,
[/FONT][/COLOR]
cd /tmp/

wget [FONT=inherit][/FONT][SIZE=2][/SIZE][SIZE=1][FONT=inherit]http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600-generic_3.16.0-031600.201408031935_amd64.deb[/FONT][/SIZE]

wget [FONT=inherit][/FONT][SIZE=2][/SIZE][SIZE=1][FONT=inherit]http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600_3.16.0-031600.201408031935_all.deb[/FONT][/SIZE]

wget [FONT=inherit][/FONT][SIZE=2][/SIZE][SIZE=1][FONT=inherit]http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-image-3.16.0-031600-generic_3.16.0-031600.201408031935_amd64.deb[/FONT][/SIZE]

sudo dpkg -i linux-headers-3.16.0-*.deb linux-image-3.16.0-*.deb

But stil it is not working. Please anybody help me.
Thank You!

---

