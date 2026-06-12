---
title: "Software Centre cannot install Brasero"
date: 2014-11-04
forum: Installation &amp; Upgrades
---

### Post by hamiljf on 2014-11-04
I seldom need to burn a CD, and used to use Brasero.  However, I've been getting upgrade error messages for some time and now find that I cannot properly get a clean (re)installation of Brasero...
brasero:
 Depends: libbrasero-media3-1 but it is not going to be installed
 Depends: libtotem-plparser17 (>=2.32) but it is not installable
 Depends: brasero-common but it is not going to be installed
 Recommends: brasero-cdrkit but it is not going to be installed
Obviously, I've got/done something wrong, but have no idea how to fix it.  All the expected repositories seem to be enabled.  Advice would be appreciated.
And, by the way, if you suggest I use CD/DVD Creator, please tell my why the application on my system (14.04) doesn't match its help system.

---

### Post by Anayonkar.Shivalkar on 2014-11-04
Hi,

I faced similar issue once (for other package) and below worked for me:

Try to uninstall it.
```
sudo apt-get clean
sudo apt-get autoclean
```
Remove all the relevant .deb files from /var/cache/apt/archives/partial/ and /var/cache/apt/archives/

And give it another try.

By the way does the output mentions anything else?

---

### Post by ibjsb4 on 2014-11-04
Odd, its asking for an outdated package.

libtotem-plparser17
[http://packages.ubuntu.com/saucy/libs/libtotem-plparser17](http://packages.ubuntu.com/saucy/libs/libtotem-plparser17)

Should be asking for libtotem-plparser18
[http://packages.ubuntu.com/trusty/brasero](http://packages.ubuntu.com/trusty/brasero)

Got any old sources still laying around?
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/*.list
```

---

