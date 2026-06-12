---
title: "problem (libkpathsea4) while upgrading"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by istyll on 2010-11-30
i've got installed ubuntu 9.10 (karmic) in a dell netbook
while i was trying to upgrade in 10.04 lts
the process stopped.
Now the synaptic does not function
i made the following actions

1. sudo apt-get autoclean
the result:
Reading package lists... Done
Building dependency tree       
Reading state information... Done

2. sudo apt-get install -f
the result
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package libkpathsea4 needs to be reinstalled, but I can't find an archive for it.

3. sudo apt-get upgrade
the result
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package libkpathsea4 needs to be reinstalled, but I can't find an archive for it.

The Synaptic does not work and i can't make an upgrade
Advice?


Thank you
istyll

---

### Post by surfer on 2010-11-30
did you try:
```
$ sudo apt-get install --reinstall libkpathsea4
```
?

---

### Post by surfer on 2010-11-30
oh, i'm running ubuntu 10.10 maverick, but maybe it's the same on 10.04 lucid already: libkpathsea4 is now libkpathsea5 . so maybe you have to completely remove version 4 and install version 5?

---

### Post by istyll on 2010-11-30
the same result:

sudo apt-get install --reinstall libkpathsea4
[sudo] password for istyl: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: The package libkpathsea4 needs to be reinstalled, but I can't find an archive for it.

---

### Post by surfer on 2010-11-30
if you find libkpathsea5 in your sources, remove libkpathsea4 and install libkpathsea5. that might work. (as i said, i'm not on 10.04 so i can't try it myself...)

---

### Post by istyll on 2010-11-30
my system is 9.10(karmic)

---

### Post by surfer on 2010-11-30
didn't you say you upgraded to 10.04?

either way: if you find libkpathsea5 in your package manager, install it.

---

### Post by istyll on 2010-11-30
i said i was trying to upgrade
the upgrade didn't finish

---

### Post by surfer on 2010-11-30
but then you probably already have the new sources.list . check if libkpathsea5 is available. if it is, install it. that's all i can suggest...

---

