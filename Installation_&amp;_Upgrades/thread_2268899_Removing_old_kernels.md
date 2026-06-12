---
title: "Removing old kernels"
date: 2015-03-12
forum: Installation &amp; Upgrades
---

### Post by zkab on 2015-03-12
I used a script from a Linux article to remove old Linux kernels from my systems.

dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge

But I get an error - E: Can not write log (Is stdout a terminal?) - tcgetattr (25: Inappropriate ioctl for device)
Also the directory with the old modules is not removed -  /lib/modules/3.19.0-7-generic not empty 

How can that be fixed - I am not so familiar with 'sed'

---

### Post by dino99 on 2015-03-12
why dont you use a simple cron job doing 'sudo apt-get autoremove' ?
or if you only wants the oldest been removed, but the more recent still been installed, then 'sudo apt-get purge 'linux-image-3.xx' where you set the xx to the real numbers to remove, and do the same for 'linux-image-extra-...' and the related 'headers'

---

### Post by zkab on 2015-03-12
I want some script that automatically removes all kernel packages (except the current one) and deletes all related files on disk.

---

### Post by slickymaster on 2015-03-12
> **zkab said:**
> I want some script that automatically removes all kernel packages (except the current one) and deletes all related files on disk.
See this thread: [http://ubuntuforums.org/showthread.php?t=1961409](http://ubuntuforums.org/showthread.php?t=1961409)

---

### Post by zkab on 2015-03-12
OK - so if I want to keep the current kernel & one kernel before I should run:```
sudo apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1) --assume-yes
```
acording to  [http://ubuntuforums.org/showthread.php?t=1961409](http://ubuntuforums.org/showthread.php?t=1961409) or ...

---

### Post by slickymaster on 2015-03-12
Yes.

---

### Post by zkab on 2015-03-12
Thanks

---

