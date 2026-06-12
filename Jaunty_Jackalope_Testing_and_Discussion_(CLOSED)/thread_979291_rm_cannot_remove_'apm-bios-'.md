---
title: "rm: cannot remove 'apm-bios-'"
date: 2008-11-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-11-11
Hi all, 
I dunno if some of you got this or not [lpbug]294269[/lpbug] . Basically some newer files unable to write 

```

Setting up powermgmt-base (1.30+nmu1) ...
udev active, devices will be created in /dev/.static/dev/
create apm_bios    c 10 134 root:root 0660
rm: cannot remove `apm_bios-': Read-only file system
mknod: `apm_bios-': Read-only file system
makedev apm_bios c 10 134 root root 0660: failed
rm: cannot remove `apm_bios-': Read-only file system

```

Comments, suggestions etc. welcome here or at the bug-report.

---

### Post by MacUntu on 2008-11-12
.

---

### Post by Kevbert on 2008-11-12
This is a bug. See bug #[[COLOR="Red"]294269[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/powermgmt-base/+bug/294269"). Please add a comment or click on this bug affects me at the top of the bug report.

---

### Post by ShirishAg75 on 2008-11-12
Kevbert, I know its a bug, please re-read my first post. I just wanted to share so that people wouldn't go on making multiple bugs for this one.

---

### Post by Kevbert on 2008-11-13
> **ShirishAg75 said:**
> Kevbert, I know its a bug, please re-read my first post. I just wanted to share so that people wouldn't go on making multiple bugs for this one.

Sorry about that... Thanks for the bug comment.

---

