---
title: "Unable to install any package"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by Khafji on 2011-07-24
Hello,

I've run into an issue that appears to prevent me from installing anything using apt, or directly with dpkg. I get the following error when doing a basic sudo apt-get install upgrade:

....(all the stuff before 'Do you want to continue?')....

Preconfiguring packages ...
/bin/tar: 1: /home/dep: Permission denied
/bin/tar: 3: Syntax error: ")" unexpected
dpkg-deb: error: subprocess tar returned exit status 2

....(more junk)....


Any ideas? I definitely am running it as root, and I even tried changing the permissions on my home directory (why does it even use my home directory to untar the packages to?) to 777, nothing. Thanks for the help ahead of time,

--Khafji

---

