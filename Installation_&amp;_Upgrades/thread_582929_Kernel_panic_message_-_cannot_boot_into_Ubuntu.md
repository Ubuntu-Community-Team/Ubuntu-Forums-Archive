---
title: "Kernel panic message - cannot boot into Ubuntu"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by weedwacker on 2007-10-20
:confused:Used the Update Manager to run update from Feisty to Gutsy and all seemed to go well except for a number of messages that said it could not install or configure certain files.

Finally I got a message that it was aborting.  I then did a restart/reboot and got the following mesage:
**Starting up... [20.316858] Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)**

My Ubuntu resides on one of my two hard drives.  Windows on the other. From Windows I can see my files on the Ubuntu hard drive.  I can see a number of new files that were installed as part of the update along side the older versions.

Is there any help here?  Suggestions on how to boot into this drive?  Or will I somehow have to reformat the drive and reinstall?  Which brings up the question:  How would I reformat this drive if it doesn't boot at all?  Any help? :confused:

---

### Post by Stemp on 2007-10-20
Using grub can you boot in an older version of the kernel ?

---

### Post by weedwacker on 2007-10-20
Hello---

yes, I hit "esc" at boot and it takes me to a list of kernels.

I try to boot with the three kernels listed. No luck.

I try the recovery modes of the three kernels.  In two of the kernels I eventually get to this:

root@stanz-desktop:~#

However, I don't know what to do next.

Any help?

Thanks.

---

### Post by Stemp on 2007-10-20
If you are connected to internet, try to restart an upgrade.

```
aptitude update
aptitude full-upgrade
```

---

### Post by weedwacker on 2007-10-20
Hi----

Thanks for your kind posts.

I have decided that my Feisty system was badly corrupted by my trying to upgrade to Gutsy so I cleared out my partition and reinstalled Feisty.  I have noticed that I am not alone with this problem.  It seems that there are many others experiencing this problem.

Thanks again.

---

