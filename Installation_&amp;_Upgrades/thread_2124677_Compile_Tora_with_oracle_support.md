---
title: "Compile Tora with oracle support"
date: 2013-03-11
forum: Installation &amp; Upgrades
---

### Post by aitkiar on 2013-03-11
A simple google search will launch a lot of results on this topics, but i've traied several of them and not of them work. At the end, when i run my newly compiled Tora, I can only choose MYSQL as a connection provider.

These are some of the tutorial I tried:

[https://help.ubuntu.com/community/HowToBuildToraWithOracle](https://help.ubuntu.com/community/HowToBuildToraWithOracle) ( there is no configure line on debian/rules )
[http://www.pythian.com/blog/installing-tora-with-oracle-support-on-ubuntu-10-04-lucid-lynx/](http://www.pythian.com/blog/installing-tora-with-oracle-support-on-ubuntu-10-04-lucid-lynx/)
[http://gorbeia.wordpress.com/2012/11/14/installing-tora-with-oracle-support-on-ubuntu-12-10-quantal-quetzal/](http://gorbeia.wordpress.com/2012/11/14/installing-tora-with-oracle-support-on-ubuntu-12-10-quantal-quetzal/)

All of them use the tora source package as a source for the program, but I'm stating to think that something is changed in the most recent package, that prevents oracle support.

¿ Any ideas ?

---

### Post by aitkiar on 2013-03-11
I mannage to do it compiling from the tar.bz source in sourceforge. I've taked the following steps.

1) download the source to a new folder [https://sourceforge.net/projects/tora/?source=dlp](https://sourceforge.net/projects/tora/?source=dlp)
2) untar de source
3) Apply patch described in this issue: [https://sourceforge.net/p/tora/bugs/853/](https://sourceforge.net/p/tora/bugs/853/)
4) cmake -DORACLE_PATH_INCLUDES=/usr/include/oracle/10.2.0.5/client64/ -DORACLE_PATH_LIB=/usr/lib/oracle/10.2.0.5/client64/lib/   ( Change the values to whatever version you have of instantclient installed.
5) make
6) sudo make install

I've tried diferrent methods before, as stated in my previous post, so I'm not totally sure what the dependencies are for the compilling and running it. Probably installing and uninstalling the tora package and it's compile dependencies ( sudo apt-get build-dep tora ) will sort everithing out.

Still wanna try to get things working from repository source package. ¿ Any help on this ?

---

