---
title: "Installing GCC 3.2 in Ubuntu 9.04"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by nethdeco on 2009-12-18
hi all;

 Im facing a great difficulty in installing GCC 3.2 in the ubuntu 9.04. The reason is have to build a library with it and due to changes in GCC 4.3 which is currently in the system the compilation fails. 

So i tried various post but still couldn't get it done. I reffed to the post at 

[http://www.linuxquestions.org/questi...tu-8.4-764285/]("http://www.linuxquestions.org/questions/linux-software-2/installing-gcc-3.4-in-ubuntu-8.4-764285/")

and installed GCC 3.4 but when i tried 

./configure CC=gcc-4.1 CXX=g++-4.1

 i get errors 

configure: warning: CXX=g++-3.4.6: invalid host type
configure: warning: CXX=g++-3.4.6: invalid host type
configure: error: can only configure for one host and one target at a time

I have already installed GCC 3.4 using apt-get and also build essentials.

 I would be grateful if some one could guide me on installing GCC 3.2 in my ubuntu box.

thankz 
deco

---

