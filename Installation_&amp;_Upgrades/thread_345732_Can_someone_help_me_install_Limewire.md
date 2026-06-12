---
title: "Can someone help me install Limewire?"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by mattmagician on 2007-01-24
ok, i need help downloading/installing Limewire for Ubuntu dapper please!
i had some problems with Edgy, and reinstalled Dapper, so i need my files and programs back! lol, thanks
Matt

---

### Post by Gerard Barberi on 2007-01-24
Make sure Java is installed

sudo apt-get install sun-java5-jre sun-java5-plugin

install alien

sudo apt-get install alien

download Limewire (the rpm)

[http://www.limewire.com/LimeWireSoftLinux](http://www.limewire.com/LimeWireSoftLinux)

(this is a direct link to the file)

convert the .rpm to a .deb

sudo alien "location of the .rpm file"

install the .deb

sudo dpkg -i "location of the .deb"

---

### Post by yabbadabbadont on 2007-01-24
[https://help.ubuntu.com/community/P2PHowTo#head-7fb2803e9171c3a6b582e29c5bf1a7b907b4044b](https://help.ubuntu.com/community/P2PHowTo#head-7fb2803e9171c3a6b582e29c5bf1a7b907b4044b)

---

### Post by mjm115 on 2007-01-24
You would be better off installing frostwire.  It is much better when compared to Limewire, as it doesn't come with all the advertisements.

Take a look [here]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_P2P_Gnutella_Client_.28FrostWire.29").

---

