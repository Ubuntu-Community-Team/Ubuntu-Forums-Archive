---
title: "installing a tar.gz?"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by kuliand on 2007-01-11
ok i need help to install a tar.gz file? i know it has to be done in the terminal but i don't know what the comands are to do it.

---

### Post by null0 on 2007-01-11
tar.gz is a tarball compressed with the gzip format. This is one of those things you should learn first when you're starting to use linux, and is a topic with widely available online documentation. Just run a search in google.

---

### Post by linnerd40 on 2007-01-11
First you must extract them (at the command line, issue the following):

tar xzvf /path/to/tarball

Then, you can change to its directory

cd /path/to/newly/extracted/directory/

Then, run the following usually:

./configure
make

and as root run:

make install


Have fun!

---

### Post by PriceChild on 2007-01-11
I suggest you read [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by kuliand on 2007-01-11
ok im getting somewhere now but i have come upto another problem. i keep getting the following error
root@andrew-desktop:/home/andrew/vmware-distrib# '/home/andrew/vmware-distrib/vmware-install.pl' 
A previous installation of VMware software has been detected.

Failure

Execution aborted.

root@andrew-desktop:/home/andrew/vmware-distrib#

---

### Post by PriceChild on 2007-01-11
remove the previous instillation of vmware then?

something like...
```
sudo /usr/bin/vmware-uninstall.pl
```but not completely sure.

If you installed from repos originally then remove from there first!!!

---

### Post by KDE_rocks2345 on 2008-04-04
> **linnerd40 said:**
> First you must extract them (at the command line, issue the following):

tar xzvf /path/to/tarball

Then, you can change to its directory

cd /path/to/newly/extracted/directory/

Then, run the following usually:

./configure
make

and as root run:

make install


Have fun!

Thanks that helps me as well. :KS

---

