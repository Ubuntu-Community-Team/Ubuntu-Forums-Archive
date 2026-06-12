---
title: "Unable to find pg_ctl after upgrade to 15.04"
date: 2015-05-03
forum: Installation &amp; Upgrades
---

### Post by MickG01 on 2015-05-03
I upgraded my Ubuntu server first from 14.04 to 14.10 and all went fine.

Then I upgraded it to 15.04 and on boot it now gives the error:

start-stop-daemon: unable to stat /usr/bin/pg_ctl (no such file or directory)

Searching for the file pg_ctl I have 2 of them

./usr/lib/postgresql/9.3/bin/pg_ctl
./home/mick/TimeTrex/postgresql/bin/pg_ctl

So somewhere I have to change a path for the boot to use the correct one.

Timetrex is the only user currently of the postgresql database though I have plans to develop some other stuff.

Can someone explain what I need to modify for the boot to look in the correct place for pg_ctl?

I found that by running the command: 'sudo pg_ctlcluster 9.3 main start' I was able to start the database and the timetrex application worked.

---

### Post by dino99 on 2015-05-03
Looks like the now used /usr/bin/ have lost the link to /bin/
either find the postgresql's conf file and adapt it, or create a symlink redirection (dirty solution)
[http://ubuntuhak.blogspot.in/2013/04/symbolic-links-in-ubuntu.html](http://ubuntuhak.blogspot.in/2013/04/symbolic-links-in-ubuntu.html)

---

### Post by SeijiSensei on 2015-05-04
```

cd /usr/bin
sudo ln -s /usr/lib/postgresql/9.3/bin/pg_ctl

```

I'd get rid of the implementation of Postgres in /home/mick/TimeTrex entirely.  Apparently the application came with own instance of Postgres?

---

### Post by MickG01 on 2015-05-04
Ppreciated but first I think I should check which instance of Postgresql contains 3 1/2 years worth of Payroll records.

I'll try adding the link and hopefully that will solve my problem.

---

### Post by MickG01 on 2015-05-04
OK I tried creating the symbolic link pointing to each pg_ctl and rebooting to see what happened. In both cases the boot log showed this on 'tail'

 * Starting OpenSSH server
 * Stopping thermal daemon
 * Starting network connection manager
 * Starting SMB/CIFS File and Active Directory Server
 * Starting MySQL Server
 * 
start-stop-daemon: unable to stat /usr/bin/pg_ctl (No such file or directory)
 * Starting PostgreSQL 9.3 database server 
 * Stopping System V runlevel compatibility

Then I still got an error saying the server wasn't started 

again running  'sudo pg_ctlcluster 9.3 main start' and I could connect to the Timetrex app?

---

### Post by SeijiSensei on 2015-05-05
The implementation you have for PostgreSQL is not the Ubuntu default.  There is no reference to "start-stop daemon" in any of the startup files like /etc/init.d/postgresql or /usr/share/postgresql-common/init.d-functions.  You seem to be somewhere between 14.04 and 15.04.

Now I would never use 15.04 or any non-LTS version on a production server.  And if I did, I wouldn't upgrade.  I'd start with a brand-new 15.04 instance, migrate the database with pg_dump, and start afresh.

You can try this as a kludge:

1) Edit the file /etc/postgresql/9.3/main/start.conf and replace "auto" with "manual".

2) Stop PostgreSQL with "sudo service postgresql stop".

3) Edit the file /etc/rc.local and add the line
```
/usr/bin/pg_ctlcluster 9.3 main start
```
above the "exit 0" line.

4) Reboot.
This will use the pg_ctlcluster command to start PG at boot rather than the usual startup scripts.

---

### Post by MickG01 on 2015-05-05
That did it.

Going into why I chose to upgrade s not for this discussion but I agree with you.
A fresh install would have involved backing up and restoring a great deal more than just a database on a very (hardware flakey) Machine.
Thanks for your help that got me around this issue. Now I can prepare for when 16.04 comes out.

---

### Post by MickG01 on 2015-05-05
Double Mouse click - Sorry

---

