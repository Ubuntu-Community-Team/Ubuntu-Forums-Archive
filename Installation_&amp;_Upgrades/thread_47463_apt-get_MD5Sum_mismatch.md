---
title: "apt-get MD5Sum mismatch"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by incredio on 2005-07-08
Apparently I need libpng12-dev to successfully install
matplotlib (via the conventional setup.py).  But I get
an MD5Sum error when installing libpng12-dev.  What
are my options to proceed?

Here is what happens: 


$ sudo apt-get install libpng12-dev
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libpng12-dev
0 upgraded, 1 newly installed, 0 to remove and 28 not upgraded.
Need to get 241kB of archives.
After unpacking 602kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libpng12-dev 1.2.8rel-1 [241kB]
Fetched 241kB in 0s (301kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpng3/libpng12-dev_1.2.8rel-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpng3/libpng12-dev_1.2.8rel-1_i386.deb)  MD5Sum mismatch

---

### Post by PMO6022 on 2005-07-08
I was having a similar error a couple of days ago. It seems that us.archive.ubuntu.org is having some problems. You should edit /etc/apt/sources.list and remove the "us" part of the repository urls. In other words change us.archive.ubuntu.org to archive.ubuntu.org. 

Save the file, and run **sudo apt-get update** and things should work from there.

[QUOTE=incredio]Apparently I need libpng12-dev to successfully install
matplotlib (via the conventional setup.py).  But I get
an MD5Sum error when installing libpng12-dev.  What
are my options to proceed?

Here is what happens: 


$ sudo apt-get install libpng12-dev
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libpng12-dev
0 upgraded, 1 newly installed, 0 to remove and 28 not upgraded.
Need to get 241kB of archives.
After unpacking 602kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") hoary/main libpng12-dev 1.2.8rel-1 [241kB]
Fetched 241kB in 0s (301kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpng3/libpng12-dev_1.2.8rel-1_i386.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpng3/libpng12-dev_1.2.8rel-1_i386.deb")  MD5Sum mismatch[/QUOTE]

---

### Post by incredio on 2005-07-08
Thanks for the suggestion, but it did not work for me.
Instead, I found libpng12-dev_1.2.8rel-1_i386.deb in a debian
archive and downloaded it.  Installed it with
#dpkg -i libpng12-dev_1.2.8rel-1_i386.deb
Then, 
#python setup.py install 
got a bit farther.  The compilation
errors suggested I needed some more "-dev" packages.
(I cannot remember which ones..tk etc. comes to mind).
Finally matplotlib installed, but I got a runtime error on
$python polar_demo.py
Choked on "import Matrix".  Upgraded Numeric from
23.7 to 23.8 ....and it worked!

---

