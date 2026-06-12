---
title: "Postgreql 8.1 Dapper doesn't work"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by geokker on 2006-08-30
I'm trying to get the Pylons MVC framework working. Like all frameworks, it's weirdly difficult or I'm weirdly dumb. This time, I can't get PostgreSQL working.

When I start it, it seems fine. When I try to create a new user I get this:

createuser: could not connect to database template1: could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

Is this a port issue?

---

### Post by acoliver on 2006-09-07
I had this same problem when upgrading.  The install script seems to notice if you have older versions.  My first step was to sudo apt-get remove postgresql-7.4 postgresql-8.0 and manually remove their startup scripts from /etc/init.d.  Then modify /etc/postgresql/8.1/postgresql.conf and change the port from 5434 to 5432.  There is PROBABLY a way to get the psql client to look for other filenames for the unix domain socket, but psql -h didn't yield it for me and a quick google didn't.  Following making the config change do sudo /etc/init.d/postgresql stop; sudo /etc/init.d/postgresql start.  You MUST do stop then start and NOT restart.  Following this it should work.  Alternatively (untried) you could enable it to allow unauthenticated users via tcp/ip on localhost via the pg_hba.conf in the same directory (presently by default it says MD5 passwords) and launch psql with -h localhost -p 5424 (or whatever port is noted in your postgresql.conf) but I'm too lazy to deal with nondefault ports anyhow.  Hope that helps.

---

### Post by rshel on 2006-09-13
I give up.  I've spent two full days trying to get 8.1 to install cleanly or, when that happens, to allow connections.  Nothing doing.  I'll go back to windows on vmware until ubuntu/linux figures out how to make a somewhat user-friendly, easily configurable database & front end for non-techies.

---

