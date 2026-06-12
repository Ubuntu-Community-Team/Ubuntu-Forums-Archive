---
title: "'Software Update Center' throwing error"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by subinvarghesein on 2011-05-15
'Software update center' is throwing error. The error was uploaded to LaunchPad. Following is the like to it:
[https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/783023](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/783023)

Following is the description on how it started misbehaving which I added to the bug description:
Was trying to install chromium, vlc & restricted-ubuntu-extras in my first restart after installing ubuntu 11.04.
during installing chromium (which was the first on the list), Ubuntu  Software Center stopped responding after downloading about 16MB. I  restarted my machine. after which it said that chrome is installed. on  installing restricted-ubuntu-extras, this error came.

Now I am not able to install anything using 'Software Update Center'. 

Please give me help me out here.

---

### Post by zvacet on 2011-05-15
In terminal

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by lechien73 on 2011-05-15
**EDIT: **Sorry - same as zvacet above. I got distracted while I was typing my reply :)

--
Hello & welcome to the forums,

Please could you let me know what happens when you issue the following commands:

```
sudo dpkg --configure -a

sudo apt-get install -f
```

Have you tried going into the Synaptic Package Manager and choosing Edit -> Fix Broken Packages?

---

