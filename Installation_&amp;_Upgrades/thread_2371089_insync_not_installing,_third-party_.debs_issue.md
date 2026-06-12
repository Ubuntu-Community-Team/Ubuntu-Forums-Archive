---
title: "insync not installing, third-party .debs issue"
date: 2017-09-10
forum: Installation &amp; Upgrades
---

### Post by pagno2 on 2017-09-10
I have installed ubuntu 16.04.3.
I can't install insync. I download it but install does not move on.
I read it's a pretty common bug and the issue has to do with installing third-party .debs on Ubuntu 16.04.
[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573206](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573206)
Does anybody have found a solution?
GA

---

### Post by ajgreeny on 2017-09-10
Have you tried the gdebi workround that many have found works?
```
sudo apt install gdebi
```then open the insync package with gdebi. It will sort out any dependencies needed and install them.

---

### Post by pagno2 on 2017-09-11
Thank you ajgreeny
I did install gdebi. I can't use it. In 'applications' there is the 'GDebi package installer'. Clicking on it a window pops up, but nothing can be done with it.
GA

---

### Post by ajgreeny on 2017-09-11
Right click the insync.deb file and choose "Open with gdebi" if it does not do so automatically.

---

### Post by pagno2 on 2017-09-11
:)
that did work!
thanks, I did learned something!
I'll wait for the end of the process and have the post in the 'solved' status.
If everything is ok I'll also post this thread into the thread linked to above in this post. A lot of people appears to be affected by the issue.
GA

---

