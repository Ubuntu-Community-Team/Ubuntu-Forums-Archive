---
title: "E: Unable to locate package libhal-storage1"
date: 2014-07-22
forum: Installation &amp; Upgrades
---

### Post by Andre_Hofseth on 2014-07-22
I am trying to install Adobe Air on Ubuntu 14.04 by using an old guide
[http://jeffhendricks.net/?p=68](http://jeffhendricks.net/?p=68)

I stop at the first step
sudo apt-get install libhal-storage1 libgnome-keyring0 lib32nss-mdns

This is log from my terminal
sudo apt-get install libhal-storage1 libgnome-keyring0 lib32nss-mdns
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libhal-storage1

Where do I find libhal-storage1 to install it?
Is this because Im running windows 8 on the same hdd?

---

### Post by ian-weisser on 2014-07-22
No, it's because are using two-year-old instructions off some random internet blog. libhal-storage1 was dropped from Ubuntu after 12.04.

Try something newer: [http://askubuntu.com/questions/87447/how-can-i-install-adobe-air](http://askubuntu.com/questions/87447/how-can-i-install-adobe-air)

---

