---
title: "system program problem detected - can't get rid of"
date: 2015-10-09
forum: Installation &amp; Upgrades
---

### Post by alek5a on 2015-10-09
not good in understanding what happened after last update

---

### Post by ajgreeny on 2015-10-09
Please do not add large images inline as some users have expensive limited downloads and images like that can cause problems for them.

In future please use thumbnails as I have done by clicking on the paperclip icon in the toolbar when you use the "reply to thread" button.

---

### Post by steve3332 on 2015-10-09
Those screens look very much like what I experienced here:

[http://ubuntuforums.org/showthread.php?t=2298070](http://ubuntuforums.org/showthread.php?t=2298070)

---

### Post by grahammechanical on 2015-10-09
Is it stopping you using the OS? If not then you have 2 options as far as I can see.

1) Cancel the crash report every time it appears and continue using the OS and wait for another update to fix the problem.
2) At the Grub boot menu select Advanced Options for Ubuntu and then select an earlier kernel. Does it have the same problem.

A third option would be to submit the crash report as a bug report. You may find that it has already been reported and is been looked into. As for what all that information means, I cannot say as I have no idea.

It is my understanding that Ubuntu now has something called Phased Updates. Instead of pushing out an important update such as a kernel update to all users with the possiblity that all users experience the same bug, only a certain percentage of users get the update. If they do not squeal then another percentage of users get the update and os on until all users receive the update. If the first & second group of users start reporting a bug then the update is held back until the bug is fixed.

[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

Regards

---

### Post by ajgreeny on 2015-10-09
Yes, it looks as if this may be a result of the phased updates system, or perhaps you have the proposed repositories enabled in software sources.

If the latter, just disable those repos and update again, then remove the 3.13.0-66.107 kernel that gives you the "oops" and reboot.

The proposed repos are now showing an even newer version of the kernel than you have, ie 3.13.0-66.108. so maybe your problem will be solved if you update again without disabling the proposed repos.

---

### Post by ubfan1 on 2015-10-09
Looks like you should take a look at bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503655](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503655) , and add yourself to the list.

---

### Post by alek5a on 2015-10-11
so much to learn from these moments, thank you all for promptness, tips & tricks

great to feel comunity
_______""""

It went away "system program problem detected" by itself, genius

---

