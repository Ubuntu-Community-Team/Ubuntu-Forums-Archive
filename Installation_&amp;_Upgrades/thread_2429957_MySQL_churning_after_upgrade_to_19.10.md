---
title: "MySQL churning after upgrade to 19.10"
date: 2019-10-25
forum: Installation &amp; Upgrades
---

### Post by dcroxton on 2019-10-25
There were some issues with the upgrade to 19.10 complaining about MySQL.  It looks like it's trying to upgrade my old databases to version 8, but it just keeps running forever (days at a time with no sign of stopping).  Any idea how I can either get the upgrade to work, or else go back to MySQL 5.7?

---

### Post by SeijiSensei on 2019-10-25
Do you use mysqldump regularly to create text-based backups of your databases?  If so, you could move /var/lib/mysql to /var/lib/mysql.old and reinstall MySQL. Then rebuild the databases from the backup.

If you're not backing up your databases regularly, now would be a good time to start.

---

### Post by dcroxton on 2019-10-25
Let's say for a moment I don't make text backups regularly...(I do have file backups.)  I can't start mysql to do anything because it is busy doing the upgrade.  That is, mysqld is in the process list, but I can't log in because it's just upgrading and not serving requests.  I don't think it would be a complete disaster if I lost the data I have, but is there an alternative?

---

### Post by SeijiSensei on 2019-10-26
Something is clearly wrong since upgrading should not take that long unless perhaps you have databases with millions of records.

If you're willing to abandon your current data, I'd kill the running MySQL process, uninstall MySQL,  move the old databases in /var/lib/mysql out of the way, and reinstall.

Beyond that I'd suggest asking in the MySQL support forums.

---

