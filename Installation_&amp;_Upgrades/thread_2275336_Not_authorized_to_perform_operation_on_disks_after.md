---
title: "Not authorized to perform operation on disks after upgrade"
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by Mattias on 2015-04-25
Hello
After upgrading from 14.10 to 15.04 extra disks have stopped auto-mounting , when I click on a disk in the sidebar of the file manager the error message "Unable to access “DISKNAME” Not authorized to perform operation, the same thing happens for USB disks. I guess it is a permissions problem but i have no idea where to start. Anyone have an idea ?
/M

---

### Post by sgian on 2015-04-26
Does this error happen in a standard or administrator account?  I've had this problem accessing extra drives from a standard account but not from an administrative account, so that I had to give permission from the administrator account to allow the standard accounts to access extra drives.

---

### Post by Mattias on 2015-04-26
It is an admistrator account. Something must be wrong with the settings for that though. In the user accounts in setting the unlock button is greyed out and adding a user is not possible. Does anyone have a good guide for user administration from the CLI ? Maybe if i cold create a new adminstrator user in the CLI and then set the same permissions for my current user ?

---

