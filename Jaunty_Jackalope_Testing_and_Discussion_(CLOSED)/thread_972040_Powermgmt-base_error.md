---
title: "Powermgmt-base error"
date: 2008-11-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2008-11-05
Just downloaded the latest updates for Jaunty and got the following error in terminal:
```
Setting up powermgmt-base (1.30+nmu1) ...
udev active, devices will be created in /dev/.static/dev/
create apm_bios	c 10 134 root:root 0660
rm: cannot remove `apm_bios-': Read-only file system
mknod: `apm_bios-': Read-only file system
makedev apm_bios c 10 134 root root 0660: failed
rm: cannot remove `apm_bios-': Read-only file system
```
I've raised this as a bug on Launchpad...
Any comments ?

---

