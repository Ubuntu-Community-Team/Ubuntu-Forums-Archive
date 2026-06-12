---
title: "Error when using apt-get install"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2005-04-13
Each time I use apt-get install I get an error regarding to gaim. I just
installed MindTerm and got this error (I guess the mindterm installation
worked fine):

johs@ubuntu:~ $ sudo apt-get install mindterm
Reading Package Lists... Done
Building Dependency Tree... Done
mindterm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gaim (1.1.2-3ubuntu1-4.10ubp1) ...
rmdir: `/usr/share/doc/gaim': No such file or directory
dpkg: error processing gaim (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
gaim
E: Sub-process /usr/bin/dpkg returned an error code (1)
johs@ubuntu

How do I fix this gaim issue?

---

### Post by erkki70 on 2005-04-13
Hi,
 Looks like your Gaim version isn't appropriate to Hoary.
 You should at least have  the one  here:
[http://packages.ubuntu.com/hoary/net/gaim](http://packages.ubuntu.com/hoary/net/gaim)

You should have a look to your /etc/apt/sources.list and check you don't have anything Warty but Hoary.

Hope this helps.

Cheers,
Erkki

---

### Post by az on 2005-04-13
sudo mkdir /usr/share/doc/gaim
sudo apt-get -f install


for the moment.

---

### Post by bigblop on 2005-04-13
Just uninstalled and reinstalled gaim, and now the error is gone

---

