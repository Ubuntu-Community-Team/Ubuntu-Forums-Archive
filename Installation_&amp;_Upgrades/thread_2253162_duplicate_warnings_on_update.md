---
title: "duplicate warnings on update"
date: 2014-11-17
forum: Installation &amp; Upgrades
---

### Post by bricro on 2014-11-17
After trying to update my ubuntu 14.04.1 I received the following warning:"W: Duplicate sources.list entry [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/restricted i386 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/multiverse i386 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-i386_Packages)" Can anyone explain in layman terms what it refers to and how to rectify the problem so i can continue updating my system through update manager. PS. I opened synaptic and reloaded then applied marked upgrades with the same warning however this time after shutting the window synaptic upgraded but i don't know if the things in the warning was just ignored or what, as software update would just not carry on so why did synaptic? Thanks to anyone that can shed light on this as i don't know what is important and what is irrelevant. It appears to me that there are duplicate entries in sources.list but only guessing however if there are i would need instructions as to how to edit it. Thanks for any help forthcomming, much appreciated.

---

### Post by claracc on 2014-11-18
Error indicates that there is duplicate lines with same repository address in your /etc/apt/sources.list file.

To test it, you can post the contents inside your /etc/apt/sources.list file, you can access it through xterm. Please, post contents inside code tags.

---

