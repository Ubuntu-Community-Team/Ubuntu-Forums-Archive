---
title: "Upgrade Advice"
date: 2012-08-18
forum: Installation &amp; Upgrades
---

### Post by wojnas on 2012-08-18
I have a system running 10.04.  It is an intel atom based system that has 32 gig compact flash that I have the OS files on it.  Then I have two, 2-terrabyte drives that I have in a Raid 1 configuration.  I would like to upgrade to 12 and I have done enough fiddling and thing a fresh install may be prudent.  Any advice I on how I can upgrade with a fresh install without impacting the existing Raid?

Thank you in advance for your help.

---

### Post by darkapec on 2012-08-18
I assume the raid is a software raid?

If that is the case it will be extremely simple. 

Backup your OS drive (if you need to) 

Then just as a precautionary disconnect your raid drives, install 12.04 as usual. DO NOT setup a raid during the ubuntu installation (it shouldnt let you because you disconnected the drives).

Once ubuntu is installed run the following 
```

sudo mdadm --assemble --scan

```
This will automatically detect your raid and set it back up exactly how it was for you.

DO NOT -BUILD OR -CREATE AS THAT WILL WIPE YOUR RAID!

this is a benefit to using a linux software raid, it is very easy to migrate to new hardware / reinstalls.

---

### Post by wojnas on 2012-08-18
Thank you very much.  Yes it is a software raid and I will give it a shot tomorrow.

---

### Post by darkapec on 2012-08-18
oops, forgot to mention you will have to plug the raid drives back in of course before you run that command.

---

