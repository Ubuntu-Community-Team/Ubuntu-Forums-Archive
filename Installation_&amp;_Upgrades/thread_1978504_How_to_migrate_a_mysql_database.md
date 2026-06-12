---
title: "How to migrate a mysql database?"
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2012-05-11
I "managed" to backup my /var/lib/mysql directory, just before the hard disk gone to heaven on a Ubuntu 11.10 system

How can I migrate the databases into a newly installed Ubuntu 12.04?

E.g., I got one database /var/lib/mysql/bible
ls -l bible/
total 20016
-rw-rw---- 1 mysql mysql    8676 Sep  6  2011 apoc.frm
-rw-rw---- 1 mysql mysql  863724 Sep  6  2011 apoc.MYD
-rw-rw---- 1 mysql mysql  940032 Sep  6  2011 apoc.MYI
-rw-rw---- 1 mysql mysql    8676 Sep  6  2011 bible_basic.frm
-rw-rw---- 1 mysql mysql 4700860 Sep  6  2011 bible_basic.MYD
-rw-rw---- 1 mysql mysql 4500480 Sep  6  2011 bible_basic.MYI
-rw-rw---- 1 mysql mysql    8676 Sep  6  2011 bible.frm
-rw-rw---- 1 mysql mysql 4660668 Sep  6  2011 bible.MYD
-rw-rw---- 1 mysql mysql 4759552 Sep  6  2011 bible.MYI
-rw-rw---- 1 mysql mysql    8686 Sep  6  2011 books.frm
-rw-rw---- 1 mysql mysql    3280 Sep  6  2011 books.MYD
-rw-rw---- 1 mysql mysql    6144 Sep  6  2011 books.MYI
-rw-rw---- 1 mysql mysql      61 Sep  6  2011 db.opt

Thanks a million!

bye

Ronald

---

### Post by agillator on 2012-05-11
This is not the usual way of backing up or restoring mysql. The best thing to do is to check the mysql documentation for migrating databases and the like. The problem is that information on the database is also in the mysql database, so simply restoring the files probably won't accomplish anything. There may be an answer in the documentation. If not, try manually recreating the database until the same files exist in the new as the old database. Then move the old files over, replacing the new ones. That might (I emphasize might) work. This all assumes you cannot access the old database on the old drive. If you can, forget all the above. Dump the database to a file (see the mysql documentation) and then restore from that file (again, see the documentation).

---

### Post by jadtech on 2012-05-11
i know  there is a far easyer way someone will come along with though the files can be copied and pasted so long as they go back in the right place in the right order , this could take a good long time if its a huge data base though ..

---

