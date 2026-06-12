---
title: "Is upgrade from 5.04 -&gt; 5.10 automatic?"
date: 2005-10-28
forum: Installation &amp; Upgrades
---

### Post by iSAWaUFO on 2005-10-28
If I was running Ubuntu 5.04 and just do the normal internet package updates, does that automatically get me to 5.10 or do I need to install from CD? How do I tell the difference? uname -a reports
Linux ubuntu 2.6.10-5-386 #1 Mon Oct 10 11:15:41 UTC 2005 i686 GNU/Linux
My CPU is a VIA Ezra

---

### Post by aysiu on 2005-10-28
You need to change your sources.list (do a find/replace on the word *hoary* for the word *breezy*), then type this in a terminal ```
sudo apt-get update
sudo apt-get dist-upgrade
``` For the most up-to-date Breezy repositories, follow the instructions [here](http://www.psychocats.net/sources.html)

---

