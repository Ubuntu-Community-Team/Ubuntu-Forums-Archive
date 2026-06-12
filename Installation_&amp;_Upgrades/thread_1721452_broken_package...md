---
title: "broken package.."
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by saurov on 2011-04-04
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 359060 files and directories currently installed.) 
Preparing to replace postgresql-client-8.4 8.4.4-2 (using .../postgresql-client-8.4_8.4.7-0ubuntu0.10.10_i386.deb) ... 
Unpacking replacement postgresql-client-8.4 ... 
Setting up postgresql-common (111) ... 
/bin/df: `/opt/OpenbravoERP-2.50/postgresql': No such file or directory 
/bin/df: no file systems processed 
 * Starting PostgreSQL 8.4 database server         * Insecure directory in $ENV{PATH} while running with -T switch at /usr/bin/pg_ctlcluster line 63. 
 [fail] 
invoke-rc.d: initscript postgresql, action "start" failed. 
dpkg: error processing postgresql-common (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up rubygems1.8 (1.3.7-2) ... 
No apport report written because MaxReports is reached already
update-alternatives: error: alternative link /usr/bin/gem is already managed by ruby. 
dpkg: error processing rubygems1.8 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up postgresql-client-8.4 (8.4.7-0ubuntu0.10.10) ... 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 postgresql-common 
 rubygems1.8 
Setting up rubygems1.8 (1.3.7-2) ... 
update-alternatives: error: alternative link /usr/bin/gem is already managed by ruby. 
dpkg: error processing rubygems1.8 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up postgresql-common (111) ... 
/bin/df: `/opt/OpenbravoERP-2.50/postgresql': No such file or directory 
/bin/df: no file systems processed 
 * Starting PostgreSQL 8.4 database server         * Insecure directory in $ENV{PATH} while running with -T switch at /usr/bin/pg_ctlcluster line 63. 
 [fail] 
invoke-rc.d: initscript postgresql, action "start" failed. 
dpkg: error processing postgresql-common (--configure): 
 subprocess installed post-installation script returned error exit status 1 


help me ...

---

### Post by zvacet on 2011-04-05
```
sudo dpkg --configure -a
```

---

### Post by saurov on 2011-04-06
after doing that.. result-

saurov@saurov-G31M-ES2C:~$ sudo dpkg --configure -a
[sudo] password for saurov: 
Setting up rubygems1.8 (1.3.7-2) ...
update-alternatives: error: alternative link /usr/bin/gem is already managed by ruby.
dpkg: error processing rubygems1.8 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up postgresql-common (111) ...
/bin/df: `/opt/OpenbravoERP-2.50/postgresql': No such file or directory
/bin/df: no file systems processed
 * Starting PostgreSQL 8.4 database server                                       * Insecure directory in $ENV{PATH} while running with -T switch at /usr/bin/pg_ctlcluster line 63.
                                                                         [fail]
invoke-rc.d: initscript postgresql, action "start" failed.
dpkg: error processing postgresql-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql-contrib-8.4:
 postgresql-contrib-8.4 depends on postgresql-common (>= 109~); however:
  Package postgresql-common is not configured yet.
dpkg: error processing postgresql-contrib-8.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-contrib:
 postgresql-contrib depends on postgresql-contrib-8.4; however:
  Package postgresql-contrib-8.4 is not configured yet.
dpkg: error processing postgresql-contrib (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rubygems1.8
 postgresql-common
 postgresql-contrib-8.4
 postgresql-contrib
.............................................................................................................................

may be this problem is related with OpenBravo ERP .. plz give me suggestion..:(

---

