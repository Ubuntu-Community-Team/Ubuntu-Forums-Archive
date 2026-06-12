---
title: "Copying remaining packages to hard drive failed"
date: 2006-03-03
forum: Installation &amp; Upgrades
---

### Post by elbj510 on 2006-03-03
I am trying to install Ubuntu off a cd I burned from the downloaded iso image.  It works fine until it gets to the stage where it copies the remaining files to the hard drive.  The error message says there may not be enough diskspace in target /var, and to check /var/log/syslog or virtual console 4.  I have no idea how to do that.  I am trying to use this as the sole os on the computer so I know there is plenty of space on the disk.

Any advice would be greatly appreciated.

---

### Post by swamytk on 2006-03-03
Go to console 4 by pressing Alt+4. Issue "df -h" command. Check for the entry like /var partition. If you have done auto partition, Ubuntu might have allocated less space for /var partition. If it is so, do manual partition with / (root), /home and swap only leaving more space for root partition.

---

