---
title: "bad index image"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by lunarcloud on 2007-07-17
WTF....

How do I remove synaptic from my system NOW? No form of purging methods will let dpkg (in its many forms) remove it.

```
sam@zempharia:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libalut0 synaptic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up synaptic (0.60ubuntu2) ...
bad image index
The generated cache was invalid.
dpkg: error processing synaptic (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 synaptic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

A bit annoying, because every time I install anything it ends with an error and only sometimes installs what I wanted it to. Adept, apt-get, and aptitude suggest no methods of fixing this error.

Please help.

---

### Post by lunarcloud on 2007-07-18
FIXED!!!

[http://ubuntuforums.org/showthread.php?t=501893&page=2](http://ubuntuforums.org/showthread.php?t=501893&page=2)

>  If a package say evince is giving this error:

```
sudo rm /var/lib/dpkg/info/evince.*
sudo apt-get install evince
```

Repeat for each broken package.

---

