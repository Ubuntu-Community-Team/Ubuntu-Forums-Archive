---
title: "Upgrade"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by thejem on 2008-02-13
I am trying to upgrade from 7.04 to 7.10. If iI use the gui uprade manager it goes thru numerous fetches and then I get this error message,
 Failed to fetch [http://www.getautomatix.com/apt/dists/fiesty/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/fiesty/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://www.getautomatix.com/apt/dists/fiesty/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/fiesty/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://people.ubuntu.com/~doko/OOo2/./Packages.gz](http://people.ubuntu.com/~doko/OOo2/./Packages.gz) 404 Not Found
I have checked and the Packages.gz are there at get automatix.
Then I tried the command line method and got the dbus error message. Added the import os and import dbus and still got the dbus error message. It runs thru after the message but just tells me my system is up to date. Dont really want to reinstall a new distro. Any help?

---

### Post by taurus on 2008-02-13
You _need_ to remove all the repos that automatix and any other 3rd party repos that you added to your /etc/apt/sources.list if you want to upgrade from Feisty to Gutsy.

---

### Post by thejem on 2008-04-04
Thanks for the reply it worked sorry it took so long to get back with the thanks

---

