---
title: "Solving sqlite issues in hardy."
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by woodgdo1 on 2008-04-28
After reboot on my Gutsy to Hardy upgrade, I get a window with the following text:
Error during the connection to database
I eventually figured out that it was gnome-rdp causing this because of a different sqlite version.

Here is a quick and dirty way to upgrade or downgrade the sqlite DB. This should work with other applications also. 

(Dump a SQL backup of the DB)
```

cp .gnome-rdp.db .gnome-rdp2.db
sqlite3 .gnome-rdp.db
sqlite> .output dbdump
sqlite> .dump
sqlite> .quit

(Verify that there is data in the dump file)
cat dbdump

(Restore DB to other version of sqlite)
sqlite new.db
sqlite> .read dbdump
(To verify that the data made it in there correctly)
sqlite> .dump
sqlite> .quit
cp new.db .gnome-rdp.db
```


I hava also posted this fix in launchpad under these bugs: 
[https://bugs.launchpad.net/ubuntu/+source/gnome-rdp/+bug/174102](https://bugs.launchpad.net/ubuntu/+source/gnome-rdp/+bug/174102)
[https://bugs.launchpad.net/ubuntu/+source/gnome-rdp/+bug/149542](https://bugs.launchpad.net/ubuntu/+source/gnome-rdp/+bug/149542)

---

