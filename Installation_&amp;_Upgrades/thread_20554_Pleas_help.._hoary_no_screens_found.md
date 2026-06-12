---
title: "Pleas help.. hoary: no screens found"
date: 2005-03-17
forum: Installation &amp; Upgrades
---

### Post by kuleali on 2005-03-17
I updated my warty to hoary , and when i rebooted my comyter the x would not start so i did sudo dpkg-reconfigure xserver-xorg.

But when i startx i get the folowing erreor:

Parse erreor line 37 (which is the Modules section) of section files in file /etc/X11/xorg.conf

"Section" is not a valid known in the section.

(EE) problem parsing config file

Fatal server error 

No screens found




I have a nvidia on board graphic driver geforce 4MX.

Pleas help.

---

### Post by dusu on 2005-03-17
There have been some troubles today (I also had the same problem this morning).
They seem to have fixed it. I simply did an apt-get update and apt-get upgrade once more, and everything worked fine.
Can you give this a try ?

---

### Post by kuleali on 2005-03-17
DAo
well, i downloaded and innstalled the hoary privew cd.
Worked fine now.

---

