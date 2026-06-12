---
title: "Old kernel not properly removed prevents installs"
date: 2017-02-13
forum: Installation &amp; Upgrades
---

### Post by Raphael_Poli on 2017-02-13
Hello I updated my kernel and since then, I get errors mentioning a previous kernel, as if there would remain traces of previous installs.
The problem is that all install or uninstall is blocked by this problem, preventing me from doing anything.
Can someone help?
regards,
Raphael

---

### Post by ubfan1 on 2017-02-13
What were the exact error messages?  Do you have any free space for the new kernel (check with the terminal command df)?  Did you manually delete any old kernels, and get complaints about them?  The package manager just gives up when trying to remove a package whose parts are missing, but it tells you what file is missing, and you can just create an empty one to satisfy it.

---

### Post by oldfred on 2017-02-13
What version of Ubuntu?
LVM or encrypted install?

 /boot full or Not enough disk space on updates
[http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808](http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808)
[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)
Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
-s is simulate so you can see what it will do
sudo apt-get -s autoremove

---

