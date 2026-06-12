---
title: "rtpproxy fails to install"
date: 2008-07-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by caryb on 2008-07-30
I have tried to install rtpproxy but it has partially installed & wont uninstall. I have a bug report in launchpad [https://bugs.launchpad.net/ubuntu/+source/rtpproxy/+bug/252804]("https://bugs.launchpad.net/ubuntu/+source/rtpproxy/+bug/252804")Can anyone tell me the file that houses the list of applications installed? I have tried apt-get remove & dpkg to remove to no avail. I guess the only thing to do is a brute force removal & take the entry out of the ??? file. 

Can someone point me in the right direction to get rid of this?


TIA Cary

BTW I have tried apt-get -f install

---

### Post by caryb on 2008-07-30
I found a dodgy fix I removed all references from /var/lib/dpkg/status file.

All good now:lolflag:


Cary

---

