---
title: "Synaptics Package Manager - lost History entry"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by mcook2 on 2007-06-09
While working as described in [http://ubuntuforums.org/showthread.php?p=2812526#post2812526](http://ubuntuforums.org/showthread.php?p=2812526#post2812526) ....

I noticed Synaptics Package Manager (SPM) does not have a History entry for at least one set of changes I made while I was trying to get the Flash player working on my AMD X 64 box.  

At one point I left SPM running an Apply while attempting to  "sudo apt-get install sleuthkit" from a Terminal in parallel. I got the message "E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?" . 

I killed the sleuthkit install and ran the other changes to completion while  "Apply changes in Terminal window" was set, but I have no SPM History for that one set of changes.   

Can setting "Apply changes in Terminal window" cause this?

---

### Post by bapoumba on 2007-06-11
synaptic logs its own history, and apt-get relies on dpkg's log. Aptitude also has its own log file (much more exhaustive). And they do not quite talk to each other :)

---

### Post by mcook2 on 2007-06-13
Thanks - I found a record of what got installed in my /var/log.dpkg.log - I guess I installed these outside of SPM .

I didn't find a log file for Aptitude, but then I hadn't used it before  - /root/.aptitude appeared only after I ran it to take a look.

Thanks again,

---

### Post by bapoumba on 2007-06-14
You're welcome..
aptitude lists auto-installed packages in /var/lib/aptitude/pkgstates and logs history in /var/log/aptitude.

---

