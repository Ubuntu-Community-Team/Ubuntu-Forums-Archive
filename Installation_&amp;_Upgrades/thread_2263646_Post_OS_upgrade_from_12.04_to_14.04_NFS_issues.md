---
title: "Post OS upgrade from 12.04 to 14.04 NFS issues"
date: 2015-02-02
forum: Installation &amp; Upgrades
---

### Post by dbruce2 on 2015-02-02
After performing a server upgrade from Ubuntu 12.04 to 14.04, I noticed that one of my mounts from the toaster is behaving oddly:

FILERHOSTNAME:/PATHTODATA       /mysql_data                      nfs     rw,hard,intr,bg,rsize=8192,wsize=8192,vers=3,tcp,timeo=600
FILERHOSTNAME:/PATHTODATA  /rmounts/filer11/atlassian_data  nfs  rw,hard,intr,bg,rsize=8192,wsize=8192,vers=3,tcp,timeo=600

The first mount appears in a df and df -h, the second mount does not, I need to run df -ha in order to see it. Both appear when I run mount and mount -l.
I know the data is actually there and usable for the second mount, its just confusing for the admins.

Any ideas why these two are behaving differently ? They are mounted from the same network source and were created with the same options on our filer end.

---

