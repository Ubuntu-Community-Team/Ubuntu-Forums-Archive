---
title: "ALSA isntall help!"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by ArchCorsair on 2007-12-08
Hi, im attempting to update ALSA (advanced linux sound architecture)

im following the directions from: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

In the "Setup Installation Directories" section:

```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver-1.0.15.tar.bz2
sudo tar xjf alsa-lib-1.0.15.tar.bz2
sudo tar xjf alsa-utils-1.0.15.tar.bz2
```

I'm not sure what to do with line #3?? I get the following error:
```
cp: cannot stat `/home/archcorsair/downloads/alsa*': No such file or directory
```

I've also tried putting in individual file names like this:
```
 sudo cp ~/downloads/alsa-driver-1.0.15.tar.bz2
```
Returns with:
```
cp: missing destination file operand after `/home/archcorsair/downloads/alsa-driver-1.0.15.tar.bz2'
```

Someone please help :confused:

---

### Post by Pumalite on 2007-12-08
sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
mkdir ~/alsa-src && cd ~/alsa-src
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)
sudo tar xjf alsa-driver-1.0.15.tar.bz2
sudo tar xjf alsa-lib-1.0.15.tar.bz2
sudo tar xjf alsa-utils-1.0.15.tar.bz2
cd alsa-driver-1.0.15
sudo ./configure
sudo make
sudo make install
cd ../alsa-lib-1.0.15
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils-1.0.15
sudo ./configure
sudo make
sudo make install

Reboot

---

### Post by ArchCorsair on 2007-12-08
thanks! rebooting now, hope it works


also, great quote on ur sig

---

### Post by Pumalite on 2007-12-08
Glad you liked it. Good luck.

---

### Post by ArchCorsair on 2007-12-08
it works! 

thank you so much!

**edit:** i have a few more questions, since i am new to the whole linux scene. im a fast learner :D is there anyway i can communicate with you, perhaps MSN?

---

### Post by Pumalite on 2007-12-08
You are welcome. Good luck. You'll always find me in the forums.

---

