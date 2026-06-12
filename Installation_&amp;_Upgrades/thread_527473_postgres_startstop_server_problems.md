---
title: "postgres start/stop server problems"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by cgramona on 2007-08-16
I am running Feisty kubuntu and I have installed and uninstalled postgres 8.2 several times using both apt-get and adept package manager. 

The problem I am having is that with 8.2 I cant seen to start or stop the server using either the default main instance or the data instance I created using dbinit as user postgres.

Here are the error messages:
=================
postgres@ubuntu:~$ pg_ctl start -w -D /var/lib/postgresql/8.2/main -l logfile
pg_ctl: another server may be running; trying to start server anyway
pg_ctl: could not start server
Examine the log output.
postgres@ubuntu:~$ pg_ctl start -w -D /var/lib/postgresql/8.2/data -l logfile
waiting for server to start...............................................................could not start server
postgres@ubuntu:~$
=================

At one time I think I had a working installation maybe with an older version that even had an entry as a service - but it wouldn't start - that is why I removed it and am trying to get 8.2 to work. I even tried ps -ax to see if I could find a running instance but I an still a rookie as far as Linux goes.

Is the normal installation supposed create a service that gets started each time I login or is that an additional step?

Any referral or advice would be greatly appreciated.

Carl

---

### Post by luigi-br on 2007-09-27
you can look at /usr/local/pgsql/data for postmaster.pid . Delete that file and try again. I think that should help.

[]'s
Luigi

---

### Post by gritsul on 2008-04-04
Hello, you have to use postgres user.

Look here for the solution:
[http://rgritsulyak.blogspot.com/2008/04/how-to-stop-postgres-on-ubuntu-linux.html](http://rgritsulyak.blogspot.com/2008/04/how-to-stop-postgres-on-ubuntu-linux.html)

---

