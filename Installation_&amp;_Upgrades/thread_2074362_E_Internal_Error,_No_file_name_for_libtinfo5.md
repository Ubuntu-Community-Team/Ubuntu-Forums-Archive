---
title: "E: Internal Error, No file name for libtinfo5"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by nwngeek212 on 2012-10-21
Alright, so I upgraded my Ubuntu 12.04 to Ubuntu 12.10 (over ssh). Now before you guys all start bashing me for upgrading over ssh, I knew the risks and I took them. My system works fine-ish, but there are some problems. I cannot install any packages through aptitude, no matter what I try to do, I always end up getting the same error:

E: Internal Error, No file name for libtinfo5

I've tried

sudo apt-get -f install
sudo apt-get -f autoremove
sudo apt-get -f upgrade

All of them show me that there is something that needs to be removed or installed, but the process halts as soon as the libtinfo5 error appears. 

Any suggestions?

---

### Post by japher on 2012-10-22
I'm in a similar situation. The upgrade from 12.04 to 12.10 appears to have failed and broken my system.

The do-release-upgrade command made some progress but eventually failed with an error trying to upgrade **libdrm2**. I tried a manual **apt-get upgrade**, and this failed with the same package.

Now apt can't add or remove packages, it instructs me to try **apt-get install -f**, but when I do I get the same error as you have mentioned:

> E: Internal Error, No file name for libtinfo5

I really should have known better than to try an Ubuntu upgrade. I've lost count of the number of machines I have seen broken by failed upgrade attempts over the years :(

---

### Post by japher on 2012-10-22
I think I've managed to get past this by simply manually installing this package. Try the following:

```

wget "http://mirror.pnl.gov/ubuntu//pool/main/n/ncurses/libtinfo5_5.9-10ubuntu1_amd64.deb"

sudo dpkg -i libtinfo5_5.9-10ubuntu1_amd64.deb

```

---

### Post by nwngeek212 on 2012-10-24
It worked!! Thanks so much!

---

