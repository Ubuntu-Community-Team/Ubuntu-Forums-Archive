---
title: "what to backup"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by Jesus-Ninja on 2008-07-05
I want to get as full a backup of the ubuntu system as possible, but am still no expert in Linux. I'm using sbackup, and have used the following exclude and includes.

```
[dirconfig]
/BACKUP1 = 0
/bin = 1
/boot = 0
/dev = 0
/etc = 1
/home = 1
/initrd = 0
/lib = 1
/lost+found = 0
/media = 0
/mnt = 0
/n3200 = 0
/opt = 1
/proc = 0
/root = 0
/sbin = 1
/sys = 0
/tmp = 0
/usr = 1
/var = 1

```

Am I missing anything, or is it over kill?

Thanks!

---

### Post by Sam Lars on 2008-07-05
I think for the most part it all looks good.  Just a few things I might suggest:
/bin = 1 - This is where basic programs are installed.  You can always reinstall them rather than back them up.
/etc = 1 - This is where all configuration is placed.  You can back up only the configurations you have changed, the rest will be reinstalled with the programs.
/lib = 1 - This is where all libraries are installed.  You can always reinstall them rather than back them up.
/opt = 1 - This is where you can install programs manually.  If you didn't install anything there, it's probably empty.
/sbin = 1 - Root-specific programs are installed here.  You can always reinstall them rather than back them up.
/usr = 1 - This is where most programs are installed.  You can always reinstall them rather than back them up.
/var = 1 - This is where mostly logs are installed, also local mail.  In the event that you would need to restore things, I wouldn't consider it that important.

---

### Post by Jesus-Ninja on 2008-07-15
Thanks Sam!

---

