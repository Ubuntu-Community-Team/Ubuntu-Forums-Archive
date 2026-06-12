---
title: "fully unattended updates"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by gelowe on 2008-08-18
After various apt-get update/install/upgrade you will get prompted for various data or notified of changes and it then requires the user acknowledgment before continuing. Is there any way to completely suppress this? i have tried the -q -y but that does not stop these types of prompts.

---

### Post by SkonesMickLoud on 2008-08-19
Try -f.

---

### Post by gelowe on 2008-08-19
I figured this out after some research. The prompts that appear after a package has been installed/updated/upgraded have to do with dpkg. In the dpkg docs there is reference how to control the dpkg tool. If I run apt-get lines with DEBIAN_FRONTEND=noninteractive pre-pended then no prompts will be given. I am also attaching a document that describes some of the other options. Also I still need to put in the –q –y flags as those are for apt and not dpgk. So for example a dist update would be 

 

DEBIAN_FRONTEND=noninteractive apt-get -q -y dist-upgrade


[http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/debconf.8.gz](http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/debconf.8.gz)

Hopefully this is helpful to others

---

