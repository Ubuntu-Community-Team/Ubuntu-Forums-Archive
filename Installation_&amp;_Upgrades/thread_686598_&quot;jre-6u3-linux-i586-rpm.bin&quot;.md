---
title: "&quot;jre-6u3-linux-i586-rpm.bin&quot;"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by lakinbrian on 2008-02-03
Hi I have downloaded realplayer to my desktop but it won't open i think its something to do java "jre-6u3-linux-i586-rpm.bin" but i cannot download this any help please

---

### Post by Partyboi2 on 2008-02-04
here's one way of installing it
open a terminal (Applications>Accessories>Terminal)
download the package
```
wget -c http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.8-0.1_i386.deb
```
then install the package
```
sudo dpkg -i realplayer_10.0.8-0.1_i386.deb
```
should then be installed :)

---

