---
title: "create backup of laptop recovery partition"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by marshall31415 on 2010-03-16
I'm about to install Ubuntu Netbook Remix and my Acer machine has a recovery partition at the beginning of the drive. I've created the eRecovery discs but those will only restore XP - not the actual recovery partition (which I'd like to have in case I sell the laptop later etc).

How can I backup the actual recovery partition, and keep its boot file intact. Then how can I restore this partition at a later time?

Thanks.

---

### Post by sikander3786 on 2010-03-16
Clonezilla is the software that might help you.

[http://clonezilla.org/](http://clonezilla.org/)

It is a disk clone, disk backup and disaster recovery software.

Sikander.

---

### Post by Mark Phelps on 2010-03-16
If you want a free MS Windows app for doing this, try EASUS Partition Master.  Has much the same features as the old Partition Magic app but it's free.

---

### Post by heatblazer on 2010-03-18
Clonezilla or... 
boot live ubuntu CD, connect to the network
sudo apt-get install partimage
follow the options of partimage.

---

