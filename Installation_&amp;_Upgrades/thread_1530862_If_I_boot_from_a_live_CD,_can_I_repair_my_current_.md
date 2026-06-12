---
title: "If I boot from a live CD, can I repair my current 10.04 installation,  dual boot XP?"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by MatadorMac on 2010-07-14
I deleted more files than I should have apparently and cannot successfully boot into gmk.  This is such a shame as I had a really stable installation which did pretty much everything perfectly (sound aside).
 
I have tried quite a few fixes such as repairing packages, reinstalling fglrx (for Radeon HD 2600 XT card), etc.
 
Now in frustration I wonder if I can boot from an Ubuntu 10.04 CD and somehow repair my dual boot XP machine Ubuntu 10.04 installation?  If this is possible I need instruction as I am not strong in Linux/Ubuntu terminal and system command work.
 
Regards

---

### Post by joereith on 2010-07-14
I think that this is what you are looking for:

[http://ubuntuforums.org/showthread.php?t=1525239&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=1525239&highlight=dual+boot)

I had the same question and this is what I stumbled upon. I am not sure by the structure of your question as to what exactly needs to be done but it may help. I am working now and cannot try this fix. If it works let me know.

---

### Post by oldfred on 2010-07-14
You can chroot into you install from a boot of the liveCD. The chroot lets you run commands like you were in your system so usually you can repair it

kansasnoob converted the multiline entries into one line with & but you may have to edit the paritition:
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Once chrooted:
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# and/or anyother commands required to fix system

---

