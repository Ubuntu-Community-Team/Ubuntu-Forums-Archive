---
title: "upgrade from 12.04.5 LTS to 14.04 LTS"
date: 2014-10-31
forum: Installation &amp; Upgrades
---

### Post by marchello_lippi2 on 2014-10-31
Hi all, 

I'd like to upgrade to 14.04 LTS.

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise

$ sudo do-release-upgrade -d
Checking new version of Ubuntu
New version not found

$ sudo apt-get dist-upgrade
Reading packages list... Done
Building tree of dependencies
Reading information about current state... Done
Update calculating... Done
updated 0, installed 0 new packages, marked to delete 0 packages and 0 packages not updated.

Sorry, it was my personal translation. 
But the result is wrong. I just can't upgrade. Any suggestions?

---

### Post by ajgreeny on 2014-10-31
It does not really answer your question, but my suggestion, (no, it's a recommendation) would be to clean install, not upgrade. Just make sure everything is backed up before doing so.

---

### Post by plucky on 2014-10-31
> $ sudo do-release-upgrade -d
Checking new version of Ubuntu
New version not found

Try without the -d as that is looking for a development version.

```
sudo apt-get update
sudo do-release-upgrade
```

Also post output from a terminal for ```
cat /etc/update-manager/release-upgrades
```

Good Luck

---

### Post by crazybear on 2014-11-01
> **ajgreeny said:**
> It does not really answer your question, but my suggestion, (no, it's a recommendation) would be to clean install, not upgrade. Just make sure everything is backed up before doing so.

While for those who are fairly adept with Ubuntu and Linux this seems like a logical, good and even simple option, I've been totally thwarted for MONTHS trying to install packages from 12.04 into 14.04 and can't find help that helps on all the many threads about 'it' on the internet. I have a 'clean install' that will NOT accept any form [I've tried several] of package lists from 12.04. The problem is dependencies and it screaming about held and broken packages...but I don't know how to move forward. I thought I had a list of programs only [minus dependencies], but it screams in terminal and in synaptic, both. It is all well and good to suggest a 'clean install'...but for me who is not a novice...but not an expert either, it is a hollow recommendation without clear instructions and help on getting it done from a clean install to all being reinstalled that I want and most of what I had - I realize some will not work with 14.04 now or perhaps ever. I even tried Aptik - but am afraid to try it, as I don't know how it will handle dependencies and programs that shouldn't be in 14.04 from 12.04. Help would be appreciated. I have many, many programs and a complex set up...installing the all one by one would take many weeks and make work on the computer impossible during that time. Thanks

---

### Post by Bucky Ball on 2014-11-01
Open Software Updater>Settings>Updates tab>make sure 'Notify me of' is set to 'Long-term releases'>close the window.

Open Software Updater. At the top of the windows you should be notified there is a OS upgrade available to 14.04 LTS.

---

### Post by marchello_lippi2 on 2014-11-01
I've installed 14.04 LTS from .iso 

Thanks to all.

---

### Post by Bucky Ball on 2014-11-01
So everything's working? If so, good news, and please follow the second thread in my signature to mark the thread as solved. Enjoy. ;)

---

