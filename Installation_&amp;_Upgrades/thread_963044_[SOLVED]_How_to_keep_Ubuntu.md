---
title: "[SOLVED] How to keep Ubuntu?"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by ujodarko on 2008-10-29
OK :), I have 2 partitions on HDD. First has XP, second Ubuntu 8.04 installed under XP. So that means: Ubuntu is listed as one of the programs in XP Add/Remove programs list...

Now, problem is in fact that XP has crushed and I can't make it working! It always reboot after few second of starting steps...

I would like to repair it but I am scared what is going to happen to Ubuntu? Is there possibility to reinstall XP and then to maybe copy some files back to C:/ and bring back Ubuntu alive?

Thanks a lot!!!

---

### Post by cyfur01 on 2008-10-29
I'm not sure about repairing, but if you reinstall Windows, it's possible to reconfigure grub to boot them both.

First, be careful not to delete your Linux partition when re-installing Windows! Just reuse the old NTFS partition.

Second, after installing Windows, follow [this article]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm") to fix grub.

Note: I assume that you can try the repair option and then reconfigure grub, but I'm not completely sure what the repair does...

---

### Post by ad_267 on 2008-10-29
I don't really think that will work. It's probably best to boot into Ubuntu if you can and back up all of your stuff you need to an external drive or to the second partition if Ubuntu isn't taking it all up.

Then when you reinstall, install Ubuntu on its own partition as a dual boot so you don't have to worry about that happening again. :)

Cyfur01: Ujodarko installed with wubi, so I don't think that will work.

---

### Post by cyfur01 on 2008-10-29
> 
Cyfur01: Ujodarko installed with wubi, so I don't think that will work.

I've never touched Wubi, so I'm rather ignorant regarding it, and how it actually installs Ubuntu.

---

### Post by ad_267 on 2008-10-29
> **cyfur01 said:**
> I've never touched Wubi, so I'm rather ignorant regarding it, and how it actually installs Ubuntu.

Yeah me either to be honest, but from what I've heard it's installed as a Windows application and the Ubuntu file system is actually in a file on the Windows file system. Unless there are tools for extracting data from this I don't think the Ubuntu installation can be recovered if Windows is reinstalled.

---

### Post by Phil112 on 2008-10-29
> **ad_267 said:**
> Yeah me either to be honest, but from what I've heard it's installed as a Windows application and the Ubuntu file system is actually in a file on the Windows file system. Unless there are tools for extracting data from this I don't think the Ubuntu installation can be recovered if Windows is reinstalled.

It's the normal Linux file system just put at "C:/Ubuntu/".

I don't think there is a way to restore it though.
The only option would be to use a live cd and back up important files.
Then reinstall XP, then Wubi, then copy the files back over.

---

### Post by ujodarko on 2008-10-30
Thank you all for your thoughts,sugestions... You know, I supposed that Ubuntu has its independence from XP while installed on 2nd partition. 

WUBI makes things this way: after XP boot screen and choosing Ubuntu, GRUB is opening its screen for choosing type of Ubuntu or XP. That is what makes me think how Ubuntu has from that point absolute independence over XP.

I tried few things:

1. I've copied wubildr & wubildr.mbr files originally from C: to D: in the same (root) position and then made change in boot.ini where I putted D:\wubildr.mbr instead C:\wubildr.mbr

  - after choosing that line, system responds with: file hal.dll is missing or corrupted in windows root directory /sistem32/

2. Then I made experiment (just like some silly lab scientist would do in crazy comedy) and put this line: D:\wubildr instead D:\wubildr.mbr
 
  - after that, Ubuntu is trying to find GRLDR file on every single one partition including inserted memory stick and says: Cannot find GRLDR file, press Ctrl+Alt+Delete to restart.

***

So, should I copy some more files or reconfigure some other file?!

Or, :rolleyes: forget all about this and reinstall OS, but this time Ubuntu standing alone (without XP). 
Honestly, I am much closer to that opinion-although it is so funny and exciting to mess around with boooot files, reconfigurations and of course loosing valuable data possibilities :-\". Noooo, don't worry I have made backup =D>

---

### Post by meindian523 on 2008-10-30
If all your data is backed up,it's better to just let everything go and install Ubuntu on a partition,whether you want to dual boot or use only Ubuntu is left to you.

---

### Post by ujodarko on 2008-10-30
> **meindian523 said:**
> If all your data is backed up,it's better to just let everything go and install Ubuntu on a partition,whether you want to dual boot or use only Ubuntu is left to you.

Well, I've decided to make one partition of those two and to install only Ubuntu. Thanks a lot!

---

### Post by Sigshane on 2008-10-30
I bet if he were to reboot with his XP cd, he could perform a repair (not from the initial option page, but from the install options page later) and fix it.

I believe that the repair only replaces essential files for the Windows install, and does not affect the other partitions.  He should have just been able to do that.

But it appears to not matter, if he's gonna slick and de-MS his system.

Good on him, and good luck TO him.

Shane

---

### Post by ujodarko on 2008-11-03
Yes!

Only 8.10 is instaled on my machine - this thread is now pointless ;-)

---

### Post by meindian523 on 2008-11-05
Please Mark the thread solved.

---

