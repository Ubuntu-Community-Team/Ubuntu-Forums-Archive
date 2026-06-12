---
title: "delete extended partition"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by thebozenator on 2008-10-03
I am trying to delete Ubuntu off a hard drive (don't worry I'll still be using Ubuntu) but i cant seem to delete the extended partition with Gparted. Can anyone help me delete it?

---

### Post by Pumalite on 2008-10-03
Post a screenshot of Gparted

---

### Post by thebozenator on 2008-10-03
sorry for the misunderstanding but the problem is not with Gparted. I just don't know how to delete the extended partition.

---

### Post by Pumalite on 2008-10-03
What are you using to delete it? Post:
sudo fdisk -lu

---

### Post by thebozenator on 2008-10-03
i just went to Gparted and right clicked on the partition "resize/move"  and "delete". Also sorry but i am away from the problem computer right now so i cant use that command. However here is the one from the computer i am on right now. They both have the same setup because i formated them at the same time. The one i am trying to delete is /dev/sdb5:

 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1       145388250   295210439    74911095   83  Linux
/dev/sdb2   *          63   145388249    72694093+   7  HPFS/NTFS
/dev/sdb5       369013176   378571724     4779274+  82  Linux swap / Solaris

The only difference is that i already deleted the NTFS partition on the other computer.

---

### Post by Pumalite on 2008-10-03
Try using Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
It works with unmounted drives/partitions

---

### Post by thebozenator on 2008-10-03
I did use my Ububtu LiveCD.

---

### Post by Pumalite on 2008-10-03
It's different. I said Gparted Live CD. Many times the problem with Gparted in the Ubuntu Live CD can be obviated with Gparted Live CD.

---

### Post by thebozenator on 2008-10-03
oops sorry about that. Ill try that next time. Thanks

---

### Post by thebozenator on 2008-10-05
it worked!!!

---

