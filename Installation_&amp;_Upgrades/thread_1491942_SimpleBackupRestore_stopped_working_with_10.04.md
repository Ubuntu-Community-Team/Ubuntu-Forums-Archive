---
title: "SimpleBackupRestore stopped working with 10.04"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by Oldhacker on 2010-05-24
In my backup directory on a second HD, I notice that no backups have been made with SimpleBackupRestore since I upgraded from Ubuntu 9.04 to 10.04 

The parameters of where to backup from and to have not changed.
What else should I check?

Thanks

---

### Post by edyeeh on 2010-05-25
I noticed this also on my installation. I looked at the backup directory and saw that the Sbackup uses the computer's name in saving the backup files. And since I changed my computer name, SBackup no longer recognizes the old files. I think maybe that it has something to do with that. Did you do the same?

---

