---
title: "Psiphon"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by Damyan on 2010-05-11
Has anyone succeeded in installing Psiphon in Ubuntu ? I spent hours trying to do it on various versions.

I currently use Ubuntu 10.04. I downloaded Psiphon here:

[http://psiphon.ca/download/psiphon-src-1.6.tar.gz](http://psiphon.ca/download/psiphon-src-1.6.tar.gz)

And I tried to follow instructions in the "install-ubuntu.txt" file (which actually instructs to download the 1.3 version).

The first problem is when trying to install appweb. I get the following:

--------------------------------------------------------------
cp: cannot stat `./bin/httpClient': No such file or directory
# Can't copy: cp -pf ./bin/httpClient "/usr/sbin/httpClient"
make: *** [install-all] Error 2
--------------------------------------------------------------

I did install appweb using a downloadable deb file, but it does not help because at a later step, I need to copy a file (which does not exist due to the above failure) from the appweb directory.

I would really appreciate some help. I need to install Psiphon for a friend who is in a country where web access is censored. I don't have any Windows computer so I really need this to work on Linux.

---

