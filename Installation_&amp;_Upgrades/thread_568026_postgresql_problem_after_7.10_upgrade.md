---
title: "postgresql problem after 7.10 upgrade"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by koukos on 2007-10-05
I have postgresql 7.4. When i upgraded my ubuntu to version 7.10 i get this problem when i start postgres:
 * Starting PostgreSQL 7.4 database server                                       * /usr/lib/postgresql/7.4/bin/pg_ctl: 75: cannot create /dev/null: Permission denied
/usr/lib/postgresql/7.4/bin/pg_ctl: 96: cannot create /dev/null: Permission denied
/usr/lib/postgresql/7.4/bin/pg_ctl: 1: Can't open /dev/null
/usr/lib/postgresql/7.4/bin/pg_ctl: 1: cannot create /dev/null: Permission denied
The PostgreSQL server failed to start. Please check the log output:

Then i take a look at /var/log/postgresql/postgresql-7.4-main.log
2007-10-05 16:20:10 LOG:  statement: select a.oid,a.relname,a.relnamespace,a.relpages,a.relisshared,a.reltuples,b.schemaname,b.n_tup_ins,b.n_tup_upd,b.n_tup_del from pg_class a, pg_stat_all_tables b where a.oid=b.relid and a.relkind = 'r' and schemaname not like 'pg_temp_%'
2007-10-05 16:22:08 LOG:  incomplete startup packet
2007-10-05 16:22:08 LOG:  received fast shutdown request
2007-10-05 16:22:08 LOG:  shutting down
2007-10-05 16:22:10 LOG:  database system is shut down

Any idea what is the problem ?

---

