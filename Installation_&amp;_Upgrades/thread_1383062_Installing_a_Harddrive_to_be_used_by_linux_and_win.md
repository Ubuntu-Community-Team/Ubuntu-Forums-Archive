---
title: "Installing a Harddrive to be used by linux and windows 7"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by Waffletaco on 2010-01-16
What File system and do i have to do anything special to use a storage HD.  Like i have Windows 7 and Ubuntu on an 80gig harddrive and a 500 gig harddrive as storage.  Anything special i have to do for me to be able to read the linux stuff in windows and vice versa?

---

### Post by Morbius1 on 2010-01-16
An NTFS formatted storage partition will be able to be read and written to by both Windows and Linux . You won't need to add anything to the linux install as the ntfs read / write driver is already contained in the kernel.

FAT32 is another option but it has file size limitations.

Some may argue that you can also do this with an ext3 / ext4 partition and install a linux filesystem driver in windows that will enable it to access linux partitions. But do you really want windows to have write access to your linux system files?

Anyway, that's my opinion

---

### Post by phillw on 2010-01-16
+1

Leave the 500GB drive as ntfs  (Never Twice the same File System - lol)

Ubuntu is dead kewl with ntfs. But, with a decent sized hard drive, such as you have - you could always allocate a partition of it to ext3/4 and do real quick backups from your other drive to it of your ubuntu installation (rsync can even do it automatically for you).

Regards,

Phill.

---

### Post by Waffletaco on 2010-01-16
Thanks guys =D

---

