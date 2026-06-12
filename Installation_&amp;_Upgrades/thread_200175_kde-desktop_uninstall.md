---
title: "kde-desktop uninstall"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by kokimunchter on 2006-06-19
hi,

got a little problem uninstalling the kde-desktop, i used the aptitude command when i tried installing kde-desktop in ubuntu. supposedly, after i use the "sudo aptitude remove kubuntu-desktop", the kde should uninstall without a hitch, but then, i recieved the following error: 

The following packages will be REMOVED:
  kubuntu-desktop
0 packages upgraded, 0 newly installed, 156 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 378MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
**E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)**
**E: Couldn't lock list directory..are you root?**
root@ubuntu:~#

...at first i thought i should be root to uninstall it but after trying using my root account, the same error came out. i tried looking at the /var/lib/apt/lists/lock file but when i open it, it's blank

how do i go about with this?

---

### Post by pyromithrandir on 2006-06-20
You'll normally get that error when you have another package manager open. i.e. if you are running adept and you try to run aptitude, it won't let you.
So, check if you have something else like apt-get, aptitude, adept, synaptic, etc running, close whatever it is, and try again.

---

