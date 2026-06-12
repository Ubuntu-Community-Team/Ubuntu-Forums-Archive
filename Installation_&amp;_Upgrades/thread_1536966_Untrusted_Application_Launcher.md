---
title: "Untrusted Application Launcher"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by dangnv.ict on 2010-07-22
Hi all,
I installed LDOCE5 on Unbuntu 10.04, but when run file ldoce5.desktop then there a message:

               **Untrusted Application Launcher**
The application launcher "ldoce5.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe.

Pro help me!!!

---

### Post by btedm on 2010-07-25
I had a similar problem with a launcher which I had previously used in version 9.10 and which would not work in 10.04.  In my case, version 10.04 required the launcher to be marked as an executable.  I did this by:
-- open the Nautilus file browser (Places ->  Home Folder)
-- browse to find the launch file 
-- right click on the file and select Properties
-- select the tab Permissions
-- in execute, put a check on the box "Allow executing file as program"

One can find more information in bug reports found by searching in Ubuntu Search "untrusted application".  For example, there is a bug report [https://bugs.launchpad.net/ubuntu/+bug/572918](https://bugs.launchpad.net/ubuntu/+bug/572918)

---

### Post by midcommander on 2010-08-18
right click the shortcut, select properties, select tab permissions, in the bottom are mark the execute (allow executing file as program). then close.

---

### Post by gemme on 2010-12-05
> **midcommander said:**
> right click the shortcut, select properties, select tab permissions, in the bottom are mark the execute (allow executing file as program). then close.

But how can I change permissions if the file is on NTFS drive or a read-only (cd-rom) media? Is there any other way to launch these files (besides copying them...)

---

