---
title: "Errors on pg_upgrade from 8.4 to 9.1"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by p3k on 2011-11-20
Hi

During (a successful) upgrade from Ubuntu 11.04 to 11.10 I got the message to manually upgrade PostgreSQL from 8.4 to 9.1.

I followed the advice in the message and did this:

# su postgres
# pg_dropcluster --stop 9.1 main
# pg_upgradecluster 8.4 main

The last command results in an error and the upgrade is aborted / rolled back:

Stopping old cluster...
Disabling connections to the old cluster during upgrade...
Restarting old cluster with restricted connections...
Creating new cluster (configuration: /etc/postgresql/9.1/main, data: /var/lib/postgresql/9.1/main)...
Moving configuration file /var/lib/postgresql/9.1/main/postgresql.conf to /etc/postgresql/9.1/main...
Moving configuration file /var/lib/postgresql/9.1/main/pg_hba.conf to /etc/postgresql/9.1/main...
Moving configuration file /var/lib/postgresql/9.1/main/pg_ident.conf to /etc/postgresql/9.1/main...
Configuring postgresql.conf to use port 5433...
Disabling connections to the new cluster during upgrade...
psql: FATAL:  no pg_hba.conf entry for host "[local]", user "root", database "antville", SSL off
Use of uninitialized value $buffer in string ne at /usr/bin/pg_upgradecluster line 322.
Error: automatic upgrade of tablespaces is not supported
Re-enabling connections to the old cluster...
Re-enabling connections to the new cluster...
Error during cluster dumping, removing new cluster

To me it looks like there are two problems:

1. Something is wrong in the file pg_hba.conf – unfortunately, I do not have a clue what that could be. The file essentially looks like this:

local   all         postgres                          ident
local   all         postgres                          ident map=root-as-pg
local   all         all                               trust
host    all         all         127.0.0.1/32          md5
host    all         all         ::1/128               md5

Connecting to the server with psql works flawlessly.

2. Something is wrong in the file /usr/bin/pg_upgradecluster

Although I found a thread about this I do not understand what I could change to make the error go away.

Could anyone here please give me exact and detailed instructions what I need to do to make the upgrade work?

Cheers,
tobi

---

