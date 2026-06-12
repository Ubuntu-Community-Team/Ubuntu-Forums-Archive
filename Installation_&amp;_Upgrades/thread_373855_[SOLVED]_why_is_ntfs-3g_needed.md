---
title: "[SOLVED] why is ntfs-3g needed?"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by zamolxis on 2007-03-01
Upon installing edgy, my ntfs drives were all recognized and mounted. I am able to access the files with no problem.

1. Why is everybody insisting on ntfs-3g? Why is that better than the default?
2. How can I rename them to something other than sda, etc?

Thanx.

---

### Post by raja on 2007-03-01
The ability to mount and read NTFS drives in linux is not new. However, you will not be able to write anything in the NTFS partition. That is where ntfs-3g comes in. Install it if you want write access to your NTFS drives.

---

### Post by zamolxis on 2007-08-21
thanx raja
i think i tried writing to ntfs before but that introduced errors so i haven't tried in a long time. hopefully, this time chkdsk won't be restarting my comp multiple times

---

