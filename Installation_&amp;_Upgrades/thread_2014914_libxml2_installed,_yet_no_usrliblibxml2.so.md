---
title: "libxml2 installed, yet no /usr/lib/libxml2.so"
date: 2012-07-02
forum: Installation &amp; Upgrades
---

### Post by ckottcil on 2012-07-02
Hi, 

I have a fresh 12.04 server base install with only the following (and of course their dependencies) added, all with the latest updates:
apache2 
emacs
g++ 
git 
libapache2-mod-proxy-html 
libxml2
libxml2-utils
libmysqlclient-dev
make 
php5 
php5-mysql
python-dev
subversion 
wget 

when I tried starting apache2, it gave an error about not being able to load /usr/lib/libxml2.so.2.  I then tried installing libxml only to find out that it was already installed, yet:

root@localhost:~# ls /usr/lib/libx*
/usr/lib/libxapian.so.22  /usr/lib/libxapian.so.22.4.2

What gives? Any ideas?

-Scott

---

### Post by ckottcil on 2012-07-02
hmm. I've answered my own question, 

the lib is at /usr/lib/x86_64-linux-gnu/libxml2.so

I'm new to Ubuntu, my last distro had 64bit libs in /usr/lib64/.

---

### Post by ckottcil on 2012-07-02
how do I mark this as SOLVED?

---

