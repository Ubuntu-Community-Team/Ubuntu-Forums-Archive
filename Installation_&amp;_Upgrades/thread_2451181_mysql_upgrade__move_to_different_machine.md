---
title: "mysql upgrade / move to different machine"
date: 2020-09-28
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2020-09-28
I have a large database (data.idb is 24 GB).
On this machine, I still use 18.04

I want to prepare to setup a new machine with 20.04.
At the same time I want to upgrade to MySQL 8.0

The system is collecting constantly data. If I use a mysqldump it would take some time and I would miss data when I start the database on the new machine.
What is the best way to move the data? I am thinking of something like use mysqldump for the first xxxx records and delete these records, to keep the database small on the day of moving. Then I start collecting on the new machine and import the data I exported via mysqldump and deleted it. Then I want to add the data I have now collected on the old and new machine but would discard the duplicates when inserting. Is that a way I should look closer or is there another better way?

---

### Post by ELMIT on 2020-10-10
Where can I get answer to this question?

---

### Post by norobro on 2020-10-10
Maybe I misunderstand your situation, but why not start collecting data on your new machine, do a mysqldump of the database on the old machine after it is off line and then restore the data to your new machine.

---

### Post by Tadaen_Sylvermane on 2020-10-10
Set up duplication? Then switch masters once it's caught up? I'm no sql admin but sounds like what it's made for almost? Downtime shouldn't be much more a few minutes when restarting services to load new configs.

Apologies...

Replication. Not duplication.

---

