---
title: "Snort on Ubuntu seems to be OK, but..."
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by cleopard on 2008-06-05
I just recently installed Snort on our Ubuntu Linux environment. Everything seems to have gone fine, except that I still don't think Snort is running:

root@craig-desktop:~# /etc/init.d/snort stop
* Stopping Network Intrusion Detection System snort [ OK ]
root@craig-desktop:~# /etc/init.d/snort start
* Starting Network Intrusion Detection System snort [ OK ]
root@craig-desktop:~# pgrep -l snort
root@craig-desktop:~#


Seems to start OK, but the process isn't listed. What things should I look for to see why it apparently isn't getting started as it says it is? Thank you.

---

