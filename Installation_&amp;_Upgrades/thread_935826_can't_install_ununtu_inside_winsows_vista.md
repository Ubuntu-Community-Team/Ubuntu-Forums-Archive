---
title: "can't install ununtu inside winsows vista"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by dgupta on 2008-10-02
i am trying to install ubuntu 8.04 inside windows vista.
it tries to download some files from the internet but my connection is through a proxy server. hence, it is unable to connect and hence doesn't install.

any clues what can be done?

* the proxy requires authentication and it doesn't ask for it. hence there is no way it can connect without it.

---

### Post by Elfy on 2008-10-02
According to the wubi wiki downloading fromproxies is unsupported - [https://wiki.ubuntu.com/WubiGuide#Proxy](https://wiki.ubuntu.com/WubiGuide#Proxy) server

You will need to download the iso and move it to the appropriate directory - [https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) can I use a manually downloaded ISO?

---

### Post by dgupta on 2008-10-02
i am not using wubi
i am using microsoft virtual pc

---

### Post by dgupta on 2008-10-02
i am not using wubi
i am using microsoft virtual pc
i just put the live cd in and autoplay opens. it asks for the partition etc. and then it tries to download.

---

### Post by Elfy on 2008-10-02
Never used microsoft virtual pc - I'd assume that you need to download the iso and then mount it, so that when the virtual machine boots it installs from the iso

You can get the iso from here [http://releases.ubuntu.com/releases/8.04.1/](http://releases.ubuntu.com/releases/8.04.1/)

I know for a fact that virtualbox will boot directly froma  downloaded iso, you can install that in windows - [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Other than that I'm afraid I don't know.

---

