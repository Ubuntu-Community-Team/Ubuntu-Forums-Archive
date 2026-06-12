---
title: "Installing KFreeFlight on Kubuntu"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by T1Oracle on 2008-10-18
When I tried to install KFreeFlight I had a lot of trouble and I didn't see any decent solutions.  But I have finally got it to work so I decided I should share the procedure that I used.

First I got the source from: [http://kde-apps.org/content/download.php?content=34410&id=1&tan=24302691&PHPSESSID=57a82d68a5364d7f8f8a3df59219e4bc](http://kde-apps.org/content/download.php?content=34410&id=1&tan=24302691&PHPSESSID=57a82d68a5364d7f8f8a3df59219e4bc)

Then I did this:
```
sudo apt-get install libc6-dev-i386
sudo aptitude install build-essential
sudo apt-get install xorg-dev
sudo apt-get install libqt4-dev
sudo apt-get install libqt3-headers libqt3-compat-headers
sudo apt-get install libavahi-qt4-dev
sudo apt-get install libavahi-qt3-dev
sudo apt-get install kdelibs4-dev
sudo apt-get install automake1.9
sudo ./configure
sudo make
sudo make install
```
To run it: kfreeflight

Do note that I installed flight gear first!  It's in the Add/Remove programs list.

Now I need to figure out how to get more airplanes...

---

