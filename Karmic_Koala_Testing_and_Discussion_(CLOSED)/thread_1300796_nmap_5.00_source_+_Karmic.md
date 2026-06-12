---
title: "nmap 5.00 source + Karmic"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sefs on 2009-10-25
I use to be able to install on Jaunty nmap 5.00 from source where it would put the zenmap icons in the internet menu.

All I would have to do is...

```

sudo aptitude install build-essential
sudo apt-get install libssl-dev
mkdir src
cd src
wget -c http://nmap.org/dist/nmap-5.00.tar.bz2 bzip2 -cd nmap-5.00.tar.bz2 | tar xvf -      cd nmap-5.00/
./configure
make
sudo make install

```


This no longer works and places no icons in the internet menu in Karmic.

Anyone has this installed from source?

---

