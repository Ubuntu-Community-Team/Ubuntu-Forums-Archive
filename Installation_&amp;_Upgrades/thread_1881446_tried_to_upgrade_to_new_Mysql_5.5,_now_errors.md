---
title: "tried to upgrade to new Mysql 5.5, now errors"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by LPLawson on 2011-11-15
Hi. I tried to install mysql 5.5 on Ubuntu 11.10 on a dedicated linux machine (amd64 if that matters). I removed everything (using apt-get remove and purge and also deleting all files with mysql in their name) from 5.1 for a fresh install ( I wasn't using it before, but need it now), then sudo apt-get install mysql-server. (the must have just updated to 5.5)

It didn't seem to work correctly (no mysql in the bin or anything) even though it let me do the password step, so I uninstalled it and tried reinstalling. I got to enter the password again, but then it said that I couldn't enter the password because it either already had a password or wasn't configured correctly. But it told me to fix that later, so I thought it was ok.

Then I got this error after a bunch of InnoDB lines:

ERROR: 1146  Table 'mysql.user' doesn't exist
111115 13:34:52 [ERROR] Aborting

111115 13:34:52  InnoDB: Starting shutdown...
111115 13:34:53  InnoDB: Shutdown completed; log sequence number 1595675
111115 13:34:53 [Note] /usr/sbin/mysqld: Shutdown complete

start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


If anyone has any ideas, I would greatly greatly appreciate them. I need this to work, and I'm getting really depressed. :(

Thanks so much!
-Lucinda

---

### Post by raja.genupula on 2011-11-15
[http://mysql-tools.com/articles/mysql/48-table-mysqlproc-doesnt-exist.html](http://mysql-tools.com/articles/mysql/48-table-mysqlproc-doesnt-exist.html)

---

### Post by LPLawson on 2011-11-15
Yeah, I tried mysql_upgrade, but it says that that command can be found in 5.1... it didn't run.

---

### Post by raja.genupula on 2011-11-15
[http://www.topwebhosts.org/bbs/board.php?bo_table=database&wr_id=29](http://www.topwebhosts.org/bbs/board.php?bo_table=database&wr_id=29)

---

### Post by LPLawson on 2011-11-16
Thanks Raja, but that won't work either. Since this isn't just an upgrade (My title is a bit misleading, sorry. I got rid of 5.1 and related files before getting 5.5) and the new commands (e.g., mysql_upgrade) didn't make it through on this install (which is why it keeps saying that the commands are available in 5.1 when I try to execute them).

Any other ideas?

-Lucinda

---

### Post by LPLawson on 2011-11-16
an update.

So I tried uninstalling 5.5 and downgrading back to 5.1. Same errors. Then I told it to upgrade to 5.5 again. I think I made some progress (though it's still broken).

It seems like the client-5.5 isn't installing correctly. The first error message said that client wasn't installing, then the server doesn't install because the client is missing. 

You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 mysql-server-5.5 : Depends: mysql-client-5.5 (>= 5.5.17-1~ppa1~oneiric) but it is not going to be installed


it suggested that I try sudo apt-get -f install

so then I get this:

The following extra packages will be installed:
  mysql-client-5.5
Suggested packages:
  libterm-readkey-perl
The following NEW packages will be installed:
  mysql-client-5.5
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/9,726 kB of archives.
After this operation, 35.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 158281 files and directories currently installed.)
Unpacking mysql-client-5.5 (from .../mysql-client-5.5_5.5.17-1~ppa1~oneiric_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/mysql-client-5.5_5.5.17-1~ppa1~oneiric_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/mysqlcheck', which is also in package mysql-client-core-5.1 5.1.58-1ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-client-5.5_5.5.17-1~ppa1~oneiric_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried renaming mysqlcheck to mysqlcheck2 and doing it again (in case it couldn't overwrite for some reason, even though I already tried chmod to 777 of that file just to be sure). Same error...

It shot me to the software center, which said that it would try to fix the problem. However, it doesn't seem able to repair it. The error message from software center says:

Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now? I click repair, it tries, then it fails. giving this message (essentially the same as before)

Reading database ... 158281 files and directories currently installed.) 
Unpacking mysql-client-5.5 (from .../mysql-client-5.5_5.5.17-1~ppa1~oneiric_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/mysql-client-5.5_5.5.17-1~ppa1~oneiric_amd64.deb (--unpack): 
 trying to overwrite '/usr/bin/mysqlcheck', which is also in package mysql-client-core-5.1 5.1.58-1ubuntu1 
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/mysql-client-5.5_5.5.17-1~ppa1~oneiric_amd64.deb 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
dpkg: dependency problems prevent configuration of mysql-server-5.5: 
 mysql-server-5.5 depends on mysql-client-5.5 (>= 5.5.17-1~ppa1~oneiric); however: 
  Package mysql-client-5.5 is not installed. 
dpkg: error processing mysql-server-5.5 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of mysql-server: 
 mysql-server depends on mysql-server-5.5; however: 
  Package mysql-server-5.5 is not configured yet. 
dpkg: error processing mysql-server (--configure): 
 dependency problems - leaving unconfigured 

does this make sense to anyone?

---

### Post by raja.genupula on 2011-11-16
hey man just do this 

sudo apt-get install -f 

and then try to do again.

---

### Post by LPLawson on 2011-11-16
I did that. See above. it cannot fix it.

---

### Post by ramkumarant on 2012-04-02
Please try the following.

1. **dpkg --list**

2. You can see packages starts with mysql as given below.
	ii  **mysql-client**                    5.1.62-2                        MySQL - Client
	ii  **mysql-common **                   5.1.61-0ubuntu0.11.10.1         MySQL database common files, e.g. /etc/mysql/my.cnf
	ii  **mysql-devel**                     5.5.22-2                        MySQL - Development header files and libraries
	ii  **mysql-embedded **                 5.5.22-2                        MySQL - Embedded library
	ii  **mysql-server-core-5.1**           5.1.61-0ubuntu0.11.10.1         MySQL database server binaries
	ii  **mysql-shared**                    5.5.22-2                        MySQL - Shared libraries
	ii ** mysql-test**                      5.5.22-2                        MySQL - Test suite

3. Issue the following commands
	[B]dpkg -r mysql-client
	dpkg -r mysql-common
	dpkg -r mysql-devel
	dpkg -r mysql-embedded
	dpkg -r mysql-server-core-5.1
	dpkg -r mysql-shared
	dpkg -r mysql-test
	dpkg -r mysql-workbench-gpl[/B]

4. **apt-get -f install**

5. **apt-get autoremove**

---

