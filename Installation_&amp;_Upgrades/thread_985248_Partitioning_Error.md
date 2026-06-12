---
title: "Partitioning Error"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by littlered on 2008-11-17
When trying to install Ubuntu, it errors out when resizing the partitions to make room for Ubuntu, but I know this isn't a problem specific to Ubuntu. I also get errors when trying trying to make a new partition manually with Partition Magic to install Ubuntu on, I'm not really sure where to go from here. Any help would be appreciated. :) Thanks.

---

### Post by psusi on 2008-11-17
Never use partition magic, it trashes hard drives.  Boot windows and force it to chkdsk the ntfs partition:

```

chkdsk /f c:

```

Say yes to the question about scheduling it during the next boot, and reboot.

If you still have trouble with gparted, post the output of sudo fdisk -l.

---

### Post by littlered on 2008-11-17
When I recently tried to install 8.10 and it failed, when I booted into Windows directly after that it ran a disk check, will this do anything that Windows do by itself that time? :)

Thanks for your help!

---

### Post by psusi on 2008-11-17
Huh?  A likely cause for failing to resize during install is that the filesystem has some minor problems that a chkdsk will fix.  Another is that the disk is too full and/or has files close to the end.  So force a chkdsk, and run a defrag before trying to install.

---

