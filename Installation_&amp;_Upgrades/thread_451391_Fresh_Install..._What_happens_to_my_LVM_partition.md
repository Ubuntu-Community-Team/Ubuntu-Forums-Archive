---
title: "Fresh Install... What happens to my LVM partition?"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by Dorado on 2007-05-22
Good morning!

Its time for me to do a fresh install from scratch. Currently the the setup is such that my OS and other software is all located on a smaller 70GB hard drive. Aside from this I have several larger hard drives (2 x 500GB) under a LVM partition, which is used only as a repository for Samba.

I am worried about accidentally losing the LVM partition (and all my files) when reinstalling the OS. What happens when I do the fresh install? Are all the partition reformatted? Can I specify which partitions to keep as is and rollover to the new installation (the LVM) and which partitions to remove, recreate and reformat  (/, /home/ /swap etc...).

Thanks to anybody that can enlighten me.

Tim.

---

### Post by jspaces on 2007-06-02
> **Dorado said:**
> Good morning!

Its time for me to do a fresh install from scratch. Currently the the setup is such that my OS and other software is all located on a smaller 70GB hard drive. Aside from this I have several larger hard drives (2 x 500GB) under a LVM partition, which is used only as a repository for Samba.

I am worried about accidentally losing the LVM partition (and all my files) when reinstalling the OS. What happens when I do the fresh install? Are all the partition reformatted? Can I specify which partitions to keep as is and rollover to the new installation (the LVM) and which partitions to remove, recreate and reformat  (/, /home/ /swap etc...).

Thanks to anybody that can enlighten me.

Tim.

Hi Tim, once the LVM volume group is activated and is accepted the partitioner restarts. In the list you will find each of your LVM volumes un-configured. Select each one then enter the correct mount point and label. On the ones that you what to keep make sure that FORMAT is deselected. The partitioner will now just mount the volumes without formatting the partition and thus preventing file deletion. The root, usr, boot partitions should be formatted if not newly created to clean house otherwise some leftover configurations and files may cause issues.
The file ownerships and permissions may need to be repaired by root if the original user is just a local one and not in a LDAP or other database on another server which did not get wiped. 
Hope this helps.
Jeff

---

