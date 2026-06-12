---
title: "fuse: permissions incorrect after upgrade to edgy"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by heldal on 2006-11-12
Members of the "fuse" group are denied access to /dev/fuse after upgrade to edgy. The problem is due to an error in /etc/udev/rules.d/40-fuse.rules. The file reads:

```
KERNEL="fuse", NAME="%k", MODE="0666"
```

Udev has changed syntax for equality-tests to use "==". For backwards compatilbility, using group permissions, change the content to:

```
KERNEL=="fuse", NAME="%k", MODE="0660", OWNER="root", GROUP="fuse"
```

Permissions will then be as before when the fuse module has been reloaded (manually or reboot).

---

### Post by StarsAndBars14 on 2006-11-21
I think this solved my problem, but all I'm getting when I run ntfsmount is "volume is dirty, run chkdsk and try again or use the --force option"

I guess I'll be spending a few hours tonight on chkdsk.  Damn Microsoft for making it so time-intensive compared to fsck.

---

