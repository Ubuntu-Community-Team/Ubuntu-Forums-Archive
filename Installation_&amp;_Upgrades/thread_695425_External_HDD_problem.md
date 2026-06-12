---
title: "External HDD problem"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by jeromevaliente on 2008-02-13
I am using UBUNTU 6.10, I have a problem with my external USB Hard Disk Drive. Everytime I attach the external HDD it wont save a file. The message is "you dont have permission to write this folder". Any idea to fix this problem? Thanks and God bless.

---

### Post by tact on 2008-02-13
Seems you dont have write permissions to the folder you are trying to write to.  Is it just that folder?  Or the whole drive?
(Assuming the drive shows up on your desktop as an icon ... right click on it>properties>permissions tab...  )

Assuming you created the partition, or formatted, the external drive yourself - using gparted or sudo in a terminal....  then the partition (or whole drive) is owned by "root".  You would need to change ownerto yourself  and/or give yourself and/or "others"  permissions to read and/or write to the drive or folder etc.

More specific guidance will require you telling more about how you created/partitioned/formatted the external drive.

---

