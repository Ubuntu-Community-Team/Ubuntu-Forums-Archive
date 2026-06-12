---
title: "Change installation media"
date: 2006-05-19
forum: Installation &amp; Upgrades
---

### Post by bkraut on 2006-05-19
I finished the installation of Ubuntu from a CD. Now whenever I'd like to install something, the system asks me for a cd. How can I change this, to automatically go to interent to search for a package?

Thanks in advance.
 
                        Bojan

---

### Post by 5-HT on 2006-05-19
[LIST=1]
[*]Save your old sources.list ```
 sudo cp /etc/apt/sources.list /etc/apt/sources.list.default 
```
[*]Open the file up for editing (any editor will do, I'll use nano here) ```
 sudo nano -w /etc/apt/sources.list 
```
[*]Find the first line that beggins with 'deb cdrom:' and comment it out. ```
 deb cdrom:... 
``````
 #deb cdrom:... 
```
[*]Save and exit (for nano, ctrl+x will do the trick).
[*]Refresh repository information ```
 sudo apt-get update 
```[/LIST]Hope that helps.

---

### Post by Wiebelhaus on 2007-10-21
> **5-HT said:**
> [LIST=1]
[*]Save your old sources.list ```
 sudo cp /etc/apt/sources.list /etc/apt/sources.list.default 
```
[*]Open the file up for editing (any editor will do, I'll use nano here) ```
 sudo nano -w /etc/apt/sources.list 
```
[*]Find the first line that beggins with 'deb cdrom:' and comment it out. ```
 deb cdrom:... 
``````
 #deb cdrom:... 
```
[*]Save and exit (for nano, ctrl+x will do the trick).
[*]Refresh repository information ```
 sudo apt-get update 
```[/LIST]Hope that helps.

Thanks mate!

---

