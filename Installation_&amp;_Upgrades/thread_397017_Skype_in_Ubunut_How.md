---
title: "Skype in Ubunut How?"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by rpaco on 2007-03-30
I have tried to install Skype in Ubuntu 6.10 using the Debian Package from the Skype site. I have tried before and got the same result as follows:

root@rpaco-pc:~/Desktop# dpkg -i skype_debian-1.3.0.53-1_i386.deb
(Reading database ... 88242 files and directories currently installed.)
Preparing to replace skype 1.3.0.53-1 (using skype_debian-1.3.0.53-1_i386.deb) ...
Unpacking replacement skype ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt3-mt | libqt3c102-mt (>= 3:3.3.3.2); however:
  Package libqt3-mt is not installed.
  Package libqt3c102-mt is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype
 
So how/where do I get the libqt3-mt and libqt3c102-mt.

OR do I use the "tar" version from skype and if I do will I have to compile something?

Any offers please.

---

### Post by Jussi Kukkonen on 2007-03-30
Searching for "skype ubuntu" on google takes you here:
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

### Post by ubukool on 2007-03-30
Hi there,

A very simple way to get Skype is to install Automatix2 using synaptic.  It's a great program that enable you to install very useful stuff like codecs and so forth very easily and simply, as well as media players and Skype.  It's better than untaring, configuring, making, etc!

Have fun!

---

### Post by Rohen on 2007-06-20
Jussi Kukkonen's post does the trick, I installed it with no problems!  :D

---

