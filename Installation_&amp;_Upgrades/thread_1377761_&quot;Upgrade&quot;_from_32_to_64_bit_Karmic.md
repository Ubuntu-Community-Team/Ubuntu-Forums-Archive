---
title: "&quot;Upgrade&quot; from 32 to 64 bit Karmic"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by hfdragon on 2010-01-10
I've searched and read a few things about "upgrading" to 64 bits, and it seems that the only solution is to make a clean install.

I have /home on a different partition, so it's ok for my personal files.

Which other parts of my systems should I backup in order not to loose any data ? I've seen that apache and sql have some data in /var, so I think I should backup this one... and of course /etc too...

And anyway... once I have installed the "new" 64 bit system, will the files from the "old" /etc and /var be compatibles with the 64 bit system ?

---

### Post by leehach on 2010-01-11
Don't know what sql you have, but for PostgreSQL the database cluster is not compatible between 64-bit and 32-bit installs.

So for Postgres at least you would have to backup the database using Postgres' own tools (pg_dump or pg_dumpall), upgrade Ubuntu to 64 bit, install 64 bit Postgres, then restore the database (pg_restore).

---

### Post by hfdragon on 2010-01-11
No it's not postgress... only mysql-server-5.1
Are the databases 32/64 bit compatibles ?

---

### Post by Sef on 2010-01-11
> I've searched and read a few things about "upgrading" to 64 bits, and it seems that the only solution is to make a clean install.

That is correct.  A clean install is the only way to "upgrade" to 64-bit from 32-bit.

---

### Post by hfdragon on 2010-01-14
I found the answer about the sql database compatibility here :

[http://dev.mysql.com/doc/refman/5.0/en/copying-databases.html]("http://dev.mysql.com/doc/refman/5.0/en/copying-databases.html")

It says :

> You can copy the .frm, .MYI, and .MYD files for MyISAM tables between different architectures that support the same floating-point format. (MySQL takes care of any byte-swapping issues.)

So i did my "upgrade" : install of the 64 bit version on a new partition, then copy the different files I needed from the "old" partition to the new installation (sql, ssh, apache config, etc..).

And everything seems OK :) Great !

---

