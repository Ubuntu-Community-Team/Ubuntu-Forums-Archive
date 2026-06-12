---
title: "Resize error, missing cluster gparted"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2011-04-20
[B][SIZE=2]I have a netbook that has a dead windows partition.  I've installed ubuntu and have never tried to recover the dead windows installation.  However, I now need that space in the main partition.  I ran the liveUSB of ubuntu and ran gparted.  I have an error on that partition.

Accounting clusters...
cluster accounting failed at 66892 (0x1054c): Missing cluster in $bitmap
Cluster accounting failed at 489569 (0x77861): extra cluster in...

I think I may have attempted to resize this and I got this error.  Originally I didn't care, but now I would like to fix this.

I can not get into windows to fix anything, so I can't run scan disk or fix disk etc....  I'm not sure if I can get a command prompt.  I don't have a CD drive.

Can I reinstall linux and use the entire hard drive?  Will it do this, or will the cluster errors prevent this?  Can I fix this so to resize the windows partition?  

Any ideas?

Thanks,

Dennis
[/SIZE][/B]

---

### Post by Quackers on 2011-04-20
Will gparted allow you to delete the Windows partition?

---

### Post by claven123 on 2011-04-21
That partition has boot? So I cant delete it.... wish I could.


D

---

