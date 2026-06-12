---
title: "Postgresql Install Problem"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by rabideau on 2007-08-05
I have done everything I can think of to try and install Postgresql 8.2 including using synaptic, apt-get (install, autremove, autoclean, etc.)  Everytime the  software installs, no matter the method, I get the following error:

Setting up postgresql-8.2 (8.2.4-0ubuntu0.7.04) ...
 * Starting PostgreSQL 8.2 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2007-08-05 17:38:20 MDT FATAL:  unsafe permissions on private key file "server.key"
2007-08-05 17:38:20 MDT DETAIL:  File must be owned by the database user or root, must have no write permission for "group", and must have no permissions for "other".
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.2, action "start" failed.
dpkg: error processing postgresql-8.2 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postgresql-8.2
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can someone help me fix this?

Thanks!!!!

---

### Post by ifeldt on 2007-08-08
I would try navigating to something like /etc/postgres or something similar. Somewhere in this folder should be a file called server.key.

The error is telling you that the permissions on the file are wrong. Try a

```
sudo chmod 700 server.key
```

This should change the permissions of the file to what the postgres daemon expects.

If you can't find the file...

```
sudo updatedb
locate server.key
```

Perform the chmod on that file and you should be in business.

To see if the above worked, do a [HTML]sudo /etc/init.d/postgresql start[/HTML]

I'm not sure of the postgresql part, but if you type post and then hit tab a few times it should get you going.

---

