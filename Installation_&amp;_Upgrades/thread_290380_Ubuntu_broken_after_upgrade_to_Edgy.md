---
title: "Ubuntu broken after upgrade to Edgy"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by Max_Might on 2006-11-01
Hi. Yesterday I upgraded my Ubuntu from Dapper to Edgy. The updater downloaded all the files and instaled and then it prompted to restart the computer. And now after the restart i cant boot. The startup process dies with the following message:

```
*Activating swap ...
*Checking root file system...
fsch 1.39 (29-May-2006)
/dev/hdb3: clean, 118272/1856832 files, 897648/3713023 blocks (check in 2 mounts)

*Checking file systems ...
fsch 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'UUID=080B-8034'
fsck died with exit status 8

*File system check failed.
A log is being saved in /var/log/fsck/checkfs
Please repair the file system manually.
```

How can i repair my Ubuntu withhout reinstalling the whole thing ?

---

### Post by IanVaughan on 2006-11-01
A couple of ideas, 1. Can you not select the Recovery mode from the GRUB menu?, if not 2. Boot from a Ubuntu live CD and fix it from there.

I say "fix it from there" as I don't know what problem you are having, but you could have a look at the partition table?

---

### Post by Max_Might on 2006-11-01
> **IanVaughan said:**
> A couple of ideas, 1. Can you not select the Recovery mode from the GRUB menu?, if not 2. Boot from a Ubuntu live CD and fix it from there.

I say "fix it from there" as I don't know what problem you are having, but you could have a look at the partition table?


well, the system automatically logs me as root when that happens so  i think i dont have to boot in recovery mode...but still i dont know what is the problem and how to fix it ](*,)

---

