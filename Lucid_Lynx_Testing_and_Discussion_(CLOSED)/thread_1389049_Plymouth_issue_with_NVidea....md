---
title: "Plymouth issue with NVidea..."
date: 2010-01-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by exploder on 2010-01-23
I checked out the bug report on the issue with Plymouth not displaying for NVidea users and found the report marked as "Fix Committed" and 3 users effected. I have NVidea graphics and the issue is not resolved. There are more than 3 users effected too, I know this from the thread in this forum.

Has the fix just not made it into the repos? If you have NVidea graphics and no Plymouth displaying please add to the bug report. This bug is marked as "High" in priority so the developers certainly want this feature working for everyone. 

I did a fresh install yesterday with the daily build and Plymouth is not displaying. I Did have to update ubiquity in a live session to get yesterday's daily build to install but the install went fine after that and other than Plymouth most everything else is working nicely.

I am not complaining, I just want the developers to know that Plymouth is still not working for those of us using NVidea graphics.

Edit: Here is the bug report for this.

[https://bugs.launchpad.net/ubuntu/lucid/+source/plymouth/+bug/506717](https://bugs.launchpad.net/ubuntu/lucid/+source/plymouth/+bug/506717)

---

### Post by infoseeker on 2010-01-24
Grub2 to KDE for me.  Nothing in-between except blank screen and 2 lines of text (something to do with fsck).  Nvidia 9600GT card. Alpha2 and uptodate.

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

```

---

### Post by philinux on 2010-01-24
> **exploder said:**
> I checked out the bug report on the issue with Plymouth not displaying for NVidea users and found the report marked as "Fix Committed" and 3 users effected. I have NVidea graphics and the issue is not resolved. There are more than 3 users effected too, I know this from the thread in this forum.

Has the fix just not made it into the repos? If you have NVidea graphics and no Plymouth displaying please add to the bug report. This bug is marked as "High" in priority so the developers certainly want this feature working for everyone. 

I did a fresh install yesterday with the daily build and Plymouth is not displaying. I Did have to update ubiquity in a live session to get yesterday's daily build to install but the install went fine after that and other than Plymouth most everything else is working nicely.

I am not complaining, I just want the developers to know that Plymouth is still not working for those of us using NVidea graphics.

Edit: Here is the bug report for this.

[https://bugs.launchpad.net/ubuntu/lucid/+source/plymouth/+bug/506717](https://bugs.launchpad.net/ubuntu/lucid/+source/plymouth/+bug/506717)

Please check launchpad status's. Fix committed is the one before fix released.

---

### Post by exploder on 2010-01-24
> 
Please check launchpad status's. Fix committed is the one before fix released.

Thanks philinux! Your post definitely got me smiling this morning! That was a dumb mistake on my part.:o

Edit: I apologised for my mistake in the bug report and will pay more attention to the status in the future to avoid embarrassing myself... I appreciate being set strait on the status.

---

