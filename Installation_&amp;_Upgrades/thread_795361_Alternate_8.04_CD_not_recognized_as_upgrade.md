---
title: "Alternate 8.04 CD not recognized as upgrade"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by bsmith1051 on 2008-05-15
I'm trying to upgrade my existing 7.10 system to 8.04 by using the Alternate CD.  When I first inserted the CD it prompted that it contained updates and I clicked OK.  It then popped-up Update Manager but it only said that there were 484 packages to update -- it did **NOT** say that there was an "Upgrade available."  I didn't want to end-up with a frankenstein OS so I cancelled.

I've done this process several times before and always in the past it's prompted "There is a new Ubuntu **upgrade** available."  So is there something wrong with the 8.04 Alternate, that it's not recognized as such?
__________

Here are a couple of reasons (possible bugs?) why it might not have worked properly:

[LIST=1]
[*]I eventually learned that there were 3 new updates available and 'they' always tell you to make sure that all available updates have been installed before attempting a version upgrade.
[*]After canceling the first attempt, I checked the Repositories in Synaptic. My previous upgrade from 7.04 to 7.10 had also been via CD and the 7.10 CD was still enabled as an "Ubuntu" source in Synaptic.  The new 8.04 Alternate CD was listed as a "3rd Party" source?
[*]I disabled the 7.10 CD and deleted the 8.04 Alternate CD from 3rd-Party, then remounted it.  This time nothing happened (beyond opening the CD file-list).  
[*]I tried running the 'cdromupgrade' script on the CD but, again, the CD ended-up in the 3rd-Party list.
[*]I edited the sources.lst file and removed the entire reference to the 7.10 CD but this had no effect either.
[/LIST]

So, for whatever reason, my system refuses to recognize the 8.04 Alternate CD as an Ubuntu upgrade.  And, I don't know how to make it re-run the original script that caused the pop-up (running the 'cdromupgrade' script doesn't work).  Any suggestions?
__________

UPDATE: I found the following 'cdromupgrade' bug which is fixed... in HARDY!  Fat lot of good that does us now, though...
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/155833](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/155833)

UPDATE #2: I'm about to try the following steps to manually remount the Alternate CD and launch the upgrade,
[http://ubuntuforums.org/showthread.php?t=580338](http://ubuntuforums.org/showthread.php?t=580338)
```
> sudo umount "/media/Ubuntu 8.04 i386"
> sudo mount /dev/cdrom2 /media/cdrom
> gksu "sh /cdrom/cdromupgrade" 
```
(Note: I had to look in my /dev folder to identify the current device name, cdrom2.)

---

### Post by bsmith1051 on 2008-05-15
**SOLUTION!**
The problem really was as simple as the drive mapping/name.  Recreating it as 'cdrom' (as expected by the Update Manager) solved my problem.

---

