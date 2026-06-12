---
title: "there is no network"
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dinu88 on 2009-09-18
After succesful installation, I configured the network as in the instructions: "[http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/)" but the internet does not work .. anyway, what's the problem??, can someone help me?

---

### Post by LKjell on 2009-09-18
Hi there is a bug. You should be able to use wireless though =p

What I did is to downgrade the packages. You need libnm-glib, network-manager and network-manager-gnome from jaunty. Use a livecd to download them if you have problems.

There is another way too to manually configure the files. But since I use wpa-enterprise it is much easier to just downgrade the packeges.

---

