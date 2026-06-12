---
title: "Server insall, cant apt-get install"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by Vladimirm on 2006-07-01
I did a server install a while back, and decided to install xubuntu.
Whenever i try to apt-get install anything, it asks me to update, i update and the same message appears.

any advice?

---

### Post by aysiu on 2006-07-01
Can you post the output of these commands? ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` Please copy and paste the output instead of describing what happens. Thanks.

---

### Post by Vladimirm on 2006-07-01
Sorry i didn't make myself clear, xubuntu installed succesfully, however i cannot install anyting else

sudo apt-get install update gives

Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/deb Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/http://security.ubuntu.com/ubuntu Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/breezy-security Sources
Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/main Sources [5185B]
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/restricted Sources [14B]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/deb-src Packages
  404 Not Found [IP: 85.133.25.7 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/http://gb.archive.ubuntu.com/ubuntu Packages
  404 Not Found [IP: 85.133.25.7 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/breezy-updates Packages
  404 Not Found [IP: 85.133.25.7 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/deb Sources
  404 Not Found [IP: 85.133.25.7 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/http://security.ubuntu.com/ubuntu Sources
  404 Not Found [IP: 85.133.25.7 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/breezy-security Sources
  404 Not Found [IP: 85.133.25.7 80]
Fetched 283kB in 4s (63.5kB/s)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Bad header line [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/deb-src/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/deb-src/binary-i386/Packages.gz)  404 Not Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/http://gb.archive.ubuntu.com/ubuntu/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/http://gb.archive.ubuntu.com/ubuntu/binary-i386/Packages.gz)  404 Not Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/breezy-updates/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/breezy-updates/binary-i386/Packages.gz)  404 Not Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/deb/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/deb/source/Sources.gz)  404 Not Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/http://security.ubuntu.com/ubuntu/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/http://security.ubuntu.com/ubuntu/source/Sources.gz)  404 Not Found [IP: 85.133.25.7 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/breezy-security/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/breezy-security/source/Sources.gz)  404 Not Found [IP: 85.133.25.7 80]
Reading package lists... Done
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

which i reckon pretty much is my main problem

---

### Post by aysiu on 2006-07-01
Well, it looks as if you have two problems:

1. Duplicate entries in your sources.list
2. 404 not found for the server address

Can you try this? [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
It'll make a backup copy of your old sources.list, but it'll also give you a fresh list with no duplicates and a different mirror of the repositories.

Do that and then ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` If you already have Xubuntu installed, the second command will simply tell you that *xubuntu-desktop* is already the latest version.

---

### Post by user1397 on 2006-07-01
the command is not **sudo apt-get install update**, it's **sudo apt-get update**

anyway, don't even bother using apt-get, use aptitude instead like what aysiu suggested.  for more info on how to install different desktop environments, read my guide in my signature called "install gnome, kde, or xfce"

---

### Post by Vladimirm on 2006-07-01
Thats great cheers!!! Problem sorted

---

### Post by Vladimirm on 2006-07-01
sorry, i didnt mean sudo apt-get install update, didnt  read what i'd written.
Whats aptitude? i'm a little new to ubuntu

---

### Post by aysiu on 2006-07-01
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by alapa on 2006-07-01
Hello,

I would like to ask you for help... I have been dealing with this problem two days, reading forums etc. but cannot resolve it! :(((((

My synaptics or Update manager etc cannot fetch the files from the servers. I tried a lot of versions of sources.list and the current one is a copy from psychocat as you recommended it. There will not be the trouble. It is connecting to the server and after quite a long time (one minute or so) it says that the connection failed.

It is strange that I can ping the address and also browse it with firefox - I just cannot get synaptics connect to it. Sometimes I tried to download the first failed package manually - without any problem. And after that - if I made one more attempt with update manager or synaptics - the whole installation worked fine!

I connect to the Internet via an ADSL router - I have just its address in /etc/resolv.conf because it provides a nameserver.

So the installation sometimes goes (rarely) and sometimes not. Where could be the problem? :confused:

---

### Post by aysiu on 2006-07-01
Can you post the output of this command? ```
sudo aptitude update
```

---

### Post by alapa on 2006-07-01
sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://sk.archive.ubuntu.com](http://sk.archive.ubuntu.com) dapper Release.gpg
  Could not connect to sk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done

---

### Post by aysiu on 2006-07-01
Maybe [this](http://www.ubuntuforums.org/showthread.php?t=14410) might help?

---

