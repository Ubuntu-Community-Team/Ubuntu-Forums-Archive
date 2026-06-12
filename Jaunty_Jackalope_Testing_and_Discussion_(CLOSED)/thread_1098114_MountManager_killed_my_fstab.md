---
title: "MountManager killed my fstab?"
date: 2009-03-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zerted on 2009-03-16
I just installed 9.04 alpha 5, updated, and installed a bunch of programs from Add/Remove (took at least 6 hours).  I was slowly going through all my options in the Control Center and played around a bit with MountManager.  I didn't accept any changes when I closed it.  I decided to manually look at my current mount options, but when I viewed /etc/fstab it was empty!  

I'm assuming 9.04 still uses fstab, so my only guess is that MountManager cleared it.  Is there any way I can regenerate it without reinstalling again?  

It might be important to point out that I have yet to restart this laptop since I booted it after the installation process finished.  The partition is formatted with ext3.

Edit: After a little more research, it appears the MountManager clears the contents of /etc/fstab on exit.  [SIZE="3"]**Backup your fstab before running MountManager.**[/SIZE]

---

### Post by knarf on 2009-03-16
```
cat /proc/mounts
``` should show you your currently mounted filesystems in a format not to dissimilar from /etc/fstab. From there you can regenerate /etc/fstab

---

### Post by zerted on 2009-03-16
Thanks a bunch, it worked.

---

