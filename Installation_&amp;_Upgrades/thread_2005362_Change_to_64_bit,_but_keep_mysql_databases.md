---
title: "Change to 64 bit, but keep mysql databases"
date: 2012-06-17
forum: Installation &amp; Upgrades
---

### Post by niks88 on 2012-06-17
Hi guys!

I would like your advice!

I have several huge MySQL databases (all together 500 Gb) and I am using Ubuntu in 32 bit. I would like to be able to use all my RAM and therefore upgrade to 64 bit.

Is it possible to reinstall Ubuntu but keep those databases intact?

Cheers,
Nik

---

### Post by SeijiSensei on 2012-06-17
You'll first need to dump the databases to plain-text SQL with the [mysqldump]("http://dev.mysql.com/doc/refman/5.5/en/mysqldump.html") command.  Then install the 64-bit version and restore the databases from the dump file.

---

### Post by niks88 on 2012-06-17
Thanks, SeijiSensei.

That's what I thought at first. But is there some way to avoid dumping and restoring, since it will takes days with my database sizes?

---

### Post by SeijiSensei on 2012-06-17
To be honest I don't know, but I suspect that the 64-bit binaries of MySQL might balk at the 32-bit data found in /var/lib/mysql.  If this is a production machine, I'd do some experimenting by first building a 32-bit version of Ubuntu in a virtual machine (using, say, VirtualBox) and creating a small test database.  Copy the contents of /var/lib/mysql to an external device like a pendrive.  Now install 64-bit Ubuntu into a VM and copy over the saved 32-bit data store.  See if it works.

I've found in the past that I could install a newer version of MySQL then replace the contents of /var/lib/mysql with the data stored in the prior version and have everything work correctly.  However I didn't change the machine's architecture, just replaced the data store.  Switching from 32-bit to 64-bit might be a more profound change than migrating from one version of MySQL to another on the same architecture.

You must have some hefty indexes and highly optimized queries to manage an SQL server of that size!

---

### Post by niks88 on 2012-06-18
Thank you! I dumped it all, installed the 64 bit version, and now restoring. Hopefully everything will be fine and in the next two days the databases will run again.

Yeah, these databases are for research in network analysis, so all tables are full of indeces and it takes a bit of time to come up with efficient queries.

---

