---
title: "Need help to install yahoo 2016 plugin"
date: 2016-11-22
forum: MINT
---

### Post by harald1 on 2016-11-22
I am trying to get yahoo working on pidgin and after a lot of web searching I have tried to install it following these instructions from [https://github.com/EionRobb/funyahoo-plusplus/blob/master/README.md](https://github.com/EionRobb/funyahoo-plusplus/blob/master/README.md) :

```
sudo apt-get install libpurple-dev libjson-glib-dev libglib2.0-dev git make;
git clone https://github.com/EionRobb/funyahoo-plusplus.git && cd funyahoo-plusplus;
make && sudo make install

```

The last command fails, this is what it says in the terminal window (it is the second time I have executed them):


harald@haraldkPc ~ $ sudo apt-get install libpurple-dev libjson-glib-dev libglib2.0-dev git make;
[sudo] password for harald: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
git is already the newest version (1:2.7.4-0ubuntu1).
libjson-glib-dev is already the newest version (1.1.2-0ubuntu1).
make is already the newest version (4.1-6).
libglib2.0-dev is already the newest version (2.48.1-1~ubuntu16.04.1).
libpurple-dev is already the newest version (1:2.10.12-0ubuntu5.1).
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 128 nicht aktualisiert.

harald@haraldkPc ~ $ git clone [https://github.com/EionRobb/funyahoo-plusplus.git](https://github.com/EionRobb/funyahoo-plusplus.git) && cd funyahoo-plusplus;
fatal: destination path 'funyahoo-plusplus' already exists and is not an empty directory.

harald@haraldkPc ~ $ make && sudo make install
make: *** No targets specified and no makefile found.  Stop.


What can I do to make the last command to run through and have this plugin installed?

My system:
Kernel: 4.4.0-21-generic i686 (32 bit)
           Desktop: Xfce 4.12.3 Distro: Linux Mint 18 Sarah



Thank you.

---

