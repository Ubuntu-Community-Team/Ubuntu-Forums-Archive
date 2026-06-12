---
title: "compiling SQLite3 with parametr"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by svecpetr on 2011-12-13
I need recompile SQLite3 with parameter

SQLITE_ENABLE_UPDATE_DELETE_LIMIT

as is written on [http://stackoverflow.com/questions/1824490/how-do-you-enable-limit-for-delete-in-sqlite](http://stackoverflow.com/questions/1824490/how-do-you-enable-limit-for-delete-in-sqlite)

tar xzf sqlite-3.6.20.tar.gz
cd sqlite-3.6.20
export CFLAGS='-DSQLITE_ENABLE_UPDATE_DELETE_LIMIT=1'
./configure
make

compilation were done with no error

but PHP5 still ends with

Warning: SQLite3::query() [sqlite3.query]: near "LIMIT": syntax error in /var/www/xxx.php on line 987

---

