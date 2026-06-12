---
title: "dictd configure database_virtual"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by TennTux on 2008-03-15
I have installed dictd and a number of dict databases for use offline. There are times when I want to use a subset of all the databases I have installed. For example when I want to lookup a word for translation I don't want the thesaurus or word definisions.

After reading the man page for dictd I see the configuration file entry for database_virtual.

> database_virtual string { virtual database specification }

Virtual Database Specification
    The virtual database specification describes the virtual database:

    database_list string
        Specifies a list of databases which are included into the virtual database.  Database names are in  the  string  and  are  separated  by comma.


Given this information I tried the following statement in the /var/lib/dictd/db.list file which is included in the /etc/dictd/dictd.conf.

```
database_virtual e-trans
 { 
  database_list fd-eng-fra, fd-eng-deu, fd-eng-spa 
}
```

However, when I try to start dictd it complains about the comma after fd-eng-fra. I have tried several variations including removing the spaces and using only spaces as separators.

Has anybody been able to use the database_virtual option, know the correct way to use it or a better way of doing what I want. I don't really want to use several -d options each time I run dict or gnome-dictionary? I don't want to submit a bug if it's just me missing the obvious.

dictd Version Info:
dictd 1.10.2/rf on Linux 2.6.22-14-generic

Ubuntu Version: 7.10 Gutsy

---

