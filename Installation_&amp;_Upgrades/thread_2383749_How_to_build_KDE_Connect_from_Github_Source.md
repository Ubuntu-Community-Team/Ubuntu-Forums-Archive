---
title: "How to build KDE Connect from Github Source"
date: 2018-01-29
forum: Installation &amp; Upgrades
---

### Post by pankajk2526 on 2018-01-29
I tried installing KDE Connect on my Raspberry Pi 3 with following command...which didn't work.

```

sudo add-apt-repository ppa:webupd8team/indicator-kdeconnect
sudo apt update
sudo apt install indicator-kdeconnect
```


It gave an error " No Package found for ARM based linux machine in repository " in simple words.


So, I went to compile KDE connect from source, but I can't figure out how to compile it (there is no instructions and no ./configure or make file, there is one cmake file, please check the below link)


[https://github.com/KDE/kdeconnect-kde](https://github.com/KDE/kdeconnect-kde)


KDE Connect allows you to connect Android and Linux over Wifi providing many features but i am only interested in clipboard sync. Copy text on Android and Paste on linux directly.


I have also found clipbrd to sync clipboard, but this does so over Internet connection and not over local wifi network like KDE connect. [http://www.clipbrd.com/](http://www.clipbrd.com/). I am OK with installing chromium extension on my raspberry pi 3.

---

### Post by pankajk2526 on 2018-01-29
sudo apt-get install kdeconnect worked !

---

