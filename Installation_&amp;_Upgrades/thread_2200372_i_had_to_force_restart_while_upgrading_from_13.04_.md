---
title: "i had to force restart while upgrading from 13.04 to 13.10"
date: 2014-01-18
forum: Installation &amp; Upgrades
---

### Post by Edward_Franklin on 2014-01-18
I went to upgrade to 13.10 from 13.04 and i had rythembox playing while i was waiting for the upgrade to finish and towards the end of downloading the packages for the upgrade to 13.10 from 13.04, The music started to skip violently and then the computer froze and i couldn't stop the music so i forced it to power off and i restarted it and when i try to boot ubuntu normally it tells me it has trouble with the graphics card. What do i do?

---

### Post by deadflowr on 2014-01-18
See if running some commands will help.
First run
```
sudo apt-get update
```
to make sure the repos were updated.
Then try a
```
sudo apt-get -f install
```
which should fix any broken packages.
then try
```
sudo apt-get upgrade
```
and if all goes well without errors, we'll see what next.
Post errors if any come up.
Use code tags(the #symbol in the new reply box)

---

### Post by unixpcguy on 2014-01-18
If you have another PC you can download 13.10 and install it via CD/DVD. If it crashed then you should reformat and clean install. Sometimes an ugrade will completely ruin a setup alltogether.

---

