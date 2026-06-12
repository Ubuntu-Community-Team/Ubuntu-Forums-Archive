---
title: "Blank (0 byte) upgrade?"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by tr333 on 2007-08-27
I just tried to do an 'apt-get upgrade', and it's wanting me to install a blank nameless update:

```
tom@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?
```

Is this a bug, or just a temporary error?

---

### Post by ajgreeny on 2007-08-27
> tom@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
**1 not fully installed or removed.**
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?It looks like you may have a broken package that needs fixing.  Have a look in synaptic to see if in the status bar there is any indication of a broken package and if so fix it.

---

### Post by Steve1961 on 2007-08-27
Also try:

sudo apt-get -f install

---

### Post by tr333 on 2007-08-27
I found the offending package:  libxml-sax-perl

Thanks for the help on this.

---

