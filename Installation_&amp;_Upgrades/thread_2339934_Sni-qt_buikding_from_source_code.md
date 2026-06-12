---
title: "Sni-qt buikding from source code"
date: 2016-10-14
forum: Installation &amp; Upgrades
---

### Post by yorkio on 2016-10-14
0         down vote          [favorite]("http://askubuntu.com/questions/834340/trouble-with-building-and-installing-sni-qt-from-source#")                                 

       I run Ubuntu 16.04.
  I want to build sni-qt package from it's source code. But I am running into some troubles and do not know how to fix them.
  I started from doing command 

  sudo apt-get purge --auto-remove sni-qt
  and
  sudo apt-get purge sni-qt
  
to remove all previous versions and their configurations. 
Then download sources to src folder: 
  apt-get source sni-qt
  
Then I go to folder with sni-qt. From there I run: 
  sudo apt-get build-dep sni-qt
  
Then I create .deb file:
  dpkg-buildpackage -rfakeroot -uc -b
  
And install it using command
  sudo dpkg -i ../sni-qt_0.2.7+15.10.20150729-0ubuntu1_amd64.deb 
  
But the result is that nothing installed, if I run for example skype its icons will still be invisible.
  What am I doing wrong here?
I would be glad to hear any hints.

---

### Post by yorkio on 2016-10-17
Maybe some ideas?

---

### Post by mc4man on 2016-10-17
Maybe - 
remove your build of sni-qt or upgrade back to repo package
Then install the repo i386 package
```
sudo apt install sni-qt:i386
```

---

### Post by yorkio on 2016-10-18
It works.
Is it possible to build i386 package from amd64 system?

---

