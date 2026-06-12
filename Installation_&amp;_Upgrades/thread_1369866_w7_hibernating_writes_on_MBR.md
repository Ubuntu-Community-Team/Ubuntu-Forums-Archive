---
title: "w7 hibernating writes on MBR"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by uffek on 2010-01-01
Hibernating windows 7 on dual-boot laptop (9.10 Ubuntu - W7) writes something on MBR which breaks GRUB2. GRUB2 does not load at all after hibernating W7 and the best solution is to reinstall GRUB with Ubuntu 9.10 cd, just follow the instructions at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
uffek

---

### Post by raymondh on 2010-01-01
> **uffek said:**
> Hibernating windows 7 on dual-boot laptop (9.10 Ubuntu - W7) writes something on MBR which breaks GRUB2. GRUB2 does not load at all after hibernating W7 and the best solution is to reinstall GRUB with Ubuntu 9.10 cd, just follow the instructions at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
uffek

after re-installing grub2 ... and then hibernating win7 again, will it continue to break grub2?

would you know which files are written by win7 to the mbr?

---

### Post by uffek on 2010-01-02
I guess W7 writes on MBR every time when hibernated, so it will break GRUB again if used. The files on MBR...I didn't save them it was the first time this happened.

---

### Post by yingwuzhao on 2010-01-02
this sounds ridiculous, I have dual boot of Win-7 and Ubuntu karmic koala. Such thing never happen to me. I really doubt that fact that any system will write anything on MBR when hibernate. 

I would suspect there is something else wrong if you have that problem.

---

### Post by uffek on 2010-01-02
There is plenty of post about W7/Karmic Koala dual boot machines and GRUB2 problems. Reinstalling GRUB solved it in my case. Possibly I will try to hibernate W7 again and find out what happened. W7 and Karmic Koala were "clean" installations about a week ago on a new Emachines laptop so I think what else could be wrong?
Of course there is a possibility of a fault component which may cause trouble.
uffek

---

