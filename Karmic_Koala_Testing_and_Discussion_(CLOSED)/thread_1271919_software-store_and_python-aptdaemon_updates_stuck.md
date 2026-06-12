---
title: "software-store and python-aptdaemon updates stuck"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cjcj on 2009-09-21
It has been some time now (about a week) that my system comes up with two errors when trying to update Karmic.

Could not find any other complaint of the same thing so started this thread.

The errors come up after trying to use update manager. The messages read

E: /var/cache/apt/archives/python-aptdaemon_0.10+bzr234-0ubuntu1_all.deb: subprocess new pre-removal script returned error exit status 1
E: /var/cache/apt/archives/software-store_0.3.7.1_all.deb: subprocess new pre-removal script returned error exit status 1

Clearly there is some reason why updates to software-store and python-aptdaemon fail to install. I have tried apt-get update and apt-get dist-update several times but they do not clear this problem. 

There were many other updates backing up but they would not instal while ever these two problem cases remained.

I therefore also tried apt-get -f install. This caused the other updates to take place but leaves the two rogue updates still ticked for update and still not working. 

Any ideas?  Do I just wait? Have other people had these updates work?

Thanks in advance

---

### Post by Lorag on 2009-09-21
Hi,

You can find the pre-removal (prem) scripts here:
/var/lib/dpkg/info

You can edit them and comment every command out or simply abort them by inserting "exit" somewhere at the beginning. I’m not sure what happens if you just delete them, so don’t do that or keep a copy.

After that you can try to remove the pakages and/or reinstall them. Or simply try an update. Good luck!

---

