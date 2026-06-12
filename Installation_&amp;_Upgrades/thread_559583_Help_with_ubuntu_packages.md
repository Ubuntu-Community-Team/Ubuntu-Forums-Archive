---
title: "Help with ubuntu packages"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by Martje_001 on 2007-09-25
Hi,
I have to type the following commands to install OpenFTD (dutch program).
```
sudo apt-get -y install subversion libtool automake build-essential libglib2.0-dev libxml2-dev libsqlite3-dev libdbus-glib-1-dev libcurl4-openssl-dev libgtk2.0-dev libgnome2-dev libgtkhtml3.8-dev libnotify-dev libgtkspell-dev libsexy-dev libxslt1-dev
svn checkout http://svn.openftd.org/svn/openftd/trunk openftd
cd openftd
./autogen.sh
./configure
make
sudo make install
sudo apt-get -y remove subversion libtool automake build-essential libglib2.0-dev libxml2-dev libsqlite3-dev libdbus-glib-1-dev libcurl4-openssl-dev libgtk2.0-dev libgnome2-dev libgtkhtml3.8-dev libnotify-dev libgtkspell-dev libsexy-dev libxslt1-dev
sudo apt-get autoremove
sudo rm -r ../openftd
```
How do I make an Ubuntu-package?

---

### Post by pay on 2007-09-25
You can use checkinstall to make a simple package. just do ```
sudo aptitude install checkinstall
sudo checkinstall
```instead of sudo make install

---

### Post by Martje_001 on 2007-09-25
Please see this video:
[http://www.xs4all.nl/~mgj1/out.ogg](http://www.xs4all.nl/~mgj1/out.ogg)

What's the problem? :S
(I did ./autogen.sh, ./configure and make)

---

### Post by pay on 2007-09-25
Hmm, It compiled and installed fine so you should be able to use it but I don't understand why the package failed. Sorry. The only thing I can think of is maybe try compiling checkinstall from source. There might be a problem with the ubuntu package of it or something but thats probably a long shot. Good luck,

---

