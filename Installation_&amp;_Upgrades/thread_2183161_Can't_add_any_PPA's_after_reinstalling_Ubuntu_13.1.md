---
title: "Can't add any PPA's after reinstalling Ubuntu 13.10"
date: 2013-10-23
forum: Installation &amp; Upgrades
---

### Post by mtclare on 2013-10-23
I can't add any PPA's at all after reinstalling Ubuntu 13.10.
  Here is what it says:



  michael@MikesKomputer:~$ sudo add-apt-repository ppa:atareao/atareao
Cannot add PPA: 'ppa:atareao/atareao'.
Please check that the PPA name or format is correct.
  


This repository is working as far as I know. The problem is that I  can't add any new repositories. Even if I can use the Software Center, I  can't have my system with the add-apt-repository command broken

---

### Post by mtclare on 2013-10-23
Long story but this bug was the result of trying to dual boot Windows 7 and Ubuntu 13.10.

I re-ran the installer and formatted partitions and now it works again.

---

