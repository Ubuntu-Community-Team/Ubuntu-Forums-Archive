---
title: "awn extras install problems"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by pdreger on 2008-04-14
I followed the AWN installation instructions here [http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)

but when I tried to install the awn-extras package (awn-extras-applets-trunk) synaptics didn't find a package by that name. 

Any clues on what I'm doing wrong?

---

### Post by Partyboi2 on 2008-04-15
If you are using hardy then make sure you have the universe repo's enabled under Software Sources (System>Admin>Software Sources) then in a terminal type
```
sudo apt-get install avant-window-navigator
```If you are using Gusty then you will need to follow instructions [here]("http://ubuntuforums.org/showthread.php?t=385981") to get awn installed.


---

### Post by pdreger on 2008-04-15
AWN Navigator and the AWN management are both installed. It's the AWN-Extras that I can't find in the repository. I followed the directions on the AWN site - added the additional repositories, etc. But even then synaptic doesn't find a awn-extras package.

---

### Post by moonbeam on 2008-04-15
> **pdreger said:**
> AWN Navigator and the AWN management are both installed. It's the AWN-Extras that I can't find in the repository. I followed the directions on the AWN site - added the additional repositories, etc. But even then synaptic doesn't find a awn-extras package.

We're having some issues with awn-extras in the awn-testing ppa...  For the moment reacocard's repo appears to be working.  I'm hoping our PPA maintainer finds the time to get the issue resolved within the next couple days.

---

