---
title: "Ubuntu 12.04 damaged my window 7 bootup."
date: 2013-10-05
forum: Installation &amp; Upgrades
---

### Post by k-vel-kutralam on 2013-10-05
HIGHLY DISAPPOINTED WITH UBUNTU 12.04.

Previously i used ubuntu 9 it is very fine the install also very simply and can install inside win7 as application BUT UBUNTU 12.04 INSTALL IS DIFFERENT AND CRASHED WIN 7.

After installing ubuntu 12.04 along inside windows i can't able to boot my windows 7.
So i have formated windowns 7 installed partition and tried to reinstall windows 7 but not able to reinstall Win 7.
Now my system don't have any OS and i lost all my data in Win 7..


I like  UBUNTU 9 installing method that is install ubuntu 9 inside the windows option and install method.
UBUNTU 12.04 install is hightly disappointed..

---

### Post by Bucky Ball on 2013-10-05
You are talking about a Wubi install, not a dual-boot install where the two OSs are on separate partitions, by the sounds of it. Wubi is being phased out and was never considered a permanent solution, more to try out Ubuntu. As this can be done from the install disk there is not much point in it.

Do you actually want help with this (if so, please tell us in detail with what) or just sharing your thoughts? If this is not a support request I will move the post to somewhere more appropriate. Thanks.

---

### Post by xSCCMx on 2013-10-05
As Ubuntu becomes more of a seperate OS than just an application, it needs more than just being installed as Wubi.

Try a partiton or installing it in a VM.

---

### Post by hakuna_matata on 2013-10-05
> BUT UBUNTU 12.04 INSTALL IS DIFFERENT AND CRASHED WIN 7.
If you run wubi.exe from 12.04 desktop CD, the option "Install inside Windows" is missing. [Here]("https://lists.ubuntu.com/archives/ubuntu-devel/2012-March/034970.html") is the reason. There is an easy solution. Copy file wubi.exe to hard disk and run wubi.exe from hard disk.

---

### Post by Mark Phelps on 2013-10-06
> So i have formated windowns 7 installed partition and tried to reinstall windows 7 but not able to reinstall Win 7.
Now my system don't have any OS and i lost all my data in Win 7..

When you reformatted the Win7 partition, that erased all the data inside it.  How did you expect that reinstalling Win7 was going to retain your data?

Or ... did you try to install Ubuntu (using Wubi) to a different Windows partition -- and merely reformatted that partition?

And, how do you know that Win7 is actually gone?

---

