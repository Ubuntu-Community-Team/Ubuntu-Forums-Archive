---
title: "Mythtv-database configuration problem"
date: 2013-09-15
forum: Installation &amp; Upgrades
---

### Post by acsidental on 2013-09-15
Hi,

After rather foolishly deciding to upgrade my two mythbuntu boxes to 12.04 (then to 13.10 as I had no end of issue's) I still have an issue with my slave machine.

When running "sudo dpkg-reconfigure mythtv-database" I get the folling error.

ERROR 1062 (23000) at line 1148: Duplicate entry 'TV Frontend-CYCLEAUDIOCHAN-mythbuntu' for key 'PRIMARY'

I can run the backend setup and install cards, tune them and see them on the frontend but they are unavailable due to error's. Also the slave drives do not show as available on the frontend (frontend is running on the master backend machine).

Any help appreciated.

Thanks

---

### Post by acsidental on 2013-09-17
Can anybody please tell me where the file is keep with this info so I can investigate what is happening?

Thanks

---

### Post by p2k on 2013-09-18
Hi,

same issue here. Seems to come from /usr/share/mythtv/sql/mythtv_0.27.0.sql containing duplicate entries.

Edit post installation script to make it verbose :
```

sudo vi /var/lib/dpkg/info/mythtv-database.postinst

```

Add "set -x" on the second line :
```

#!/bin/sh -e
set -x

```

Re-run installation :
```

patrick@myhostname:~/workspace$ sudo aptitude install mythtv-database 
The following partially installed packages will be configured:
  mythtv-database 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up mythtv-database (2:0.27.0+fixes.20130918.033883b-0ubuntu0mythbuntu3) ...
+ MYSQL=/usr/share/mythtv/sql/mythtv*.sql
+ MYSQLCONFIG=/etc/mysql/conf.d/mythtv.cnf
+ FSTAB=/etc/fstab
+ NEWIP=127.0.0.1
+ cat /etc/hostname
+ LOCALHOSTNAME=myhostname
+ . /usr/share/debconf/confmodule
+ [ !  ]
+ PERL_DL_NONLAZY=1
+ export PERL_DL_NONLAZY
+ [  ]
+ exec /usr/share/debconf/frontend /var/lib/dpkg/info/mythtv-database.postinst configure 
+ MYSQL=/usr/share/mythtv/sql/mythtv*.sql
+ MYSQLCONFIG=/etc/mysql/conf.d/mythtv.cnf
+ FSTAB=/etc/fstab
+ NEWIP=127.0.0.1
+ cat /etc/hostname
+ LOCALHOSTNAME=myhostname
+ . /usr/share/debconf/confmodule
+ [ ! 1 ]
+ [ -z  ]
+ exec
+ [  ]
+ exec
+ DEBCONF_REDIR=1
+ export DEBCONF_REDIR
+ db_get mythtv/mysql_mythtv_dbname
+ _db_cmd GET mythtv/mysql_mythtv_dbname
+ _db_internal_IFS= 

+ IFS= 
+ printf %s\n GET mythtv/mysql_mythtv_dbname
+ IFS=  

+ IFS=
 read -r _db_internal_line
+ RET=mythconverg
+ return 0
+ database=mythconverg
+ db_get mythtv/mysql_mythtv_user
+ _db_cmd GET mythtv/mysql_mythtv_user
+ _db_internal_IFS= 

+ IFS= 
+ printf %s\n GET mythtv/mysql_mythtv_user
+ IFS=  

+ IFS=
 read -r _db_internal_line
+ RET=mythtv
+ return 0
+ mythtv_username=mythtv
+ db_get mythtv/mysql_mythtv_password
+ _db_cmd GET mythtv/mysql_mythtv_password
+ _db_internal_IFS= 

+ IFS= 
+ printf %s\n GET mythtv/mysql_mythtv_password
+ IFS=  

+ IFS=
 read -r _db_internal_line
+ RET=LY2MUGYh
+ return 0
+ mythtv_password=LY2MUGYh
+ db_get mythtv/mysql_admin_user
+ _db_cmd GET mythtv/mysql_admin_user
+ _db_internal_IFS= 

+ IFS= 
+ printf %s\n GET mythtv/mysql_admin_user
+ IFS=  

+ IFS=
 read -r _db_internal_line
+ RET=debian-sys-maint
+ return 0
+ admin_username=debian-sys-maint
+ [ debian-sys-maint = debian-sys-maint ]
+ SECURITY_INFO=--defaults-file=/etc/mysql/debian.cnf
+ [  = localhost ]
+ [ -f /etc/mysql/conf.d/mythtv.cnf ]
+ db_get mythtv/public_bind
+ _db_cmd GET mythtv/public_bind
+ _db_internal_IFS= 

+ IFS= 
+ printf %s\n GET mythtv/public_bind
+ IFS=  

+ IFS=
 read -r _db_internal_line
+ RET=false
+ return 0
+ [ -n false ]
+ [ false = true ]
+ sed -i -e s/^bind/#bind/ /etc/mysql/conf.d/mythtv.cnf
+ mysql --defaults-file=/etc/mysql/debian.cnf mythconverg
+ echo SELECT NULL;
+ mysql --defaults-file=/etc/mysql/debian.cnf mythconverg
+ echo SELECT value FROM settings LIMIT 1, 1;
+ prepare_database
+ mysql --defaults-file=/etc/mysql/debian.cnf mythconverg
+ sed -e s/Terra/Mythbuntu/g; s/OLDHOSTNAME/myhostname/g; s/127.0.0.1/127.0.0.1/g; s/blueosd/BlackCurves-OSD/g
+ cat /usr/share/mythtv/sql/mythtv_0.27.0.sql
ERROR 1062 (23000) at line 1148: Duplicate entry 'TV Frontend-CYCLEAUDIOCHAN-myhostname' for key 'PRIMARY'
dpkg: error processing mythtv-database (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 mythtv-database
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mythtv-database (2:0.27.0+fixes.20130918.033883b-0ubuntu0mythbuntu3) ...
+ MYSQL=/usr/share/mythtv/sql/mythtv*.sql
+ MYSQLCONFIG=/etc/mysql/conf.d/mythtv.cnf
+ FSTAB=/etc/fstab
+ NEWIP=127.0.0.1
+ cat /etc/hostname
+ LOCALHOSTNAME=myhostname
+ . /usr/share/debconf/confmodule
+ [ !  ]
+ PERL_DL_NONLAZY=1
+ export PERL_DL_NONLAZY
+ [  ]
+ exec /usr/share/debconf/frontend /var/lib/dpkg/info/mythtv-database.postinst configure 
+ MYSQL=/usr/share/mythtv/sql/mythtv*.sql
+ MYSQLCONFIG=/etc/mysql/conf.d/mythtv.cnf
+ FSTAB=/etc/fstab
+ NEWIP=127.0.0.1
+ cat /etc/hostname
+ LOCALHOSTNAME=myhostname
+ . /usr/share/debconf/confmodule
+ [ ! 1 ]
+ [ -z  ]
+ exec
+ [  ]
+ exec
+ DEBCONF_REDIR=1
+ export DEBCONF_REDIR
+ db_get mythtv/mysql_mythtv_dbname
+ _db_cmd GET mythtv/mysql_mythtv_dbname
+ _db_internal_IFS= 

+ IFS= 
+ printf %s\n GET mythtv/mysql_mythtv_dbname
+ IFS=  

+ IFS=
 read -r _db_internal_line
+ RET=mythconverg
+ return 0
+ database=mythconverg
+ db_get mythtv/mysql_mythtv_user
+ _db_cmd GET mythtv/mysql_mythtv_user
+ _db_internal_IFS= 

+ IFS= 
+ printf %s\n GET mythtv/mysql_mythtv_user
+ IFS=  

+ IFS=
 read -r _db_internal_line
+ RET=mythtv
+ return 0
+ mythtv_username=mythtv
+ db_get mythtv/mysql_mythtv_password
+ _db_cmd GET mythtv/mysql_mythtv_password
+ _db_internal_IFS= 

+ IFS= 
+ printf %s\n GET mythtv/mysql_mythtv_password
+ IFS=  

+ IFS=
 read -r _db_internal_line
+ RET=LY2MUGYh
+ return 0
+ mythtv_password=LY2MUGYh
+ db_get mythtv/mysql_admin_user
+ _db_cmd GET mythtv/mysql_admin_user
+ _db_internal_IFS= 

+ IFS= 
+ printf %s\n GET mythtv/mysql_admin_user
+ IFS=  

+ IFS=
 read -r _db_internal_line
+ RET=debian-sys-maint
+ return 0
+ admin_username=debian-sys-maint
+ [ debian-sys-maint = debian-sys-maint ]
+ SECURITY_INFO=--defaults-file=/etc/mysql/debian.cnf
+ [  = localhost ]
+ [ -f /etc/mysql/conf.d/mythtv.cnf ]
+ db_get mythtv/public_bind
+ _db_cmd GET mythtv/public_bind
+ _db_internal_IFS= 

+ IFS= 
+ printf %s\n GET mythtv/public_bind
+ IFS=  

+ IFS=
 read -r _db_internal_line
+ RET=false
+ return 0
+ [ -n false ]
+ [ false = true ]
+ sed -i -e s/^bind/#bind/ /etc/mysql/conf.d/mythtv.cnf
+ mysql --defaults-file=/etc/mysql/debian.cnf mythconverg
+ echo SELECT NULL;
+ mysql --defaults-file=/etc/mysql/debian.cnf mythconverg
+ echo SELECT value FROM settings LIMIT 1, 1;
+ prepare_database
+ mysql --defaults-file=/etc/mysql/debian.cnf mythconverg
+ sed -e s/Terra/Mythbuntu/g; s/OLDHOSTNAME/myhostname/g; s/127.0.0.1/127.0.0.1/g; s/blueosd/BlackCurves-OSD/g
+ cat /usr/share/mythtv/sql/mythtv_0.27.0.sql
ERROR 1062 (23000) at line 1148: Duplicate entry 'TV Frontend-CYCLEAUDIOCHAN-myhostname' for key 'PRIMARY'
dpkg: error processing mythtv-database (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mythtv-database

```

Indeed, this script tries to insert the same entries twice :
patrick@myhostname:~/workspace$ grep CYCLEAUDIOCHAN /usr/share/mythtv/sql/mythtv_0.27.0.sql | sed 's/),(/),\n(/g' | grep CYCLEAUDIOCHAN
```

('TV Frontend','CYCLEAUDIOCHAN','Cycle audio channels','','OLDHOSTNAME'),
('TV Playback','CYCLEAUDIOCHAN','Cycle audio channels','','OLDHOSTNAME'),
('TV Frontend','CYCLEAUDIOCHAN','Cycle audio channels','','OLDHOSTNAME'),
('TV Playback','CYCLEAUDIOCHAN','Cycle audio channels','','OLDHOSTNAME'),

```

---

### Post by p2k on 2013-09-18
The issue is visible here : [https://github.com/MythTV/packaging/blob/master/deb/debian/mythtv_0.27.0.sql](https://github.com/MythTV/packaging/blob/master/deb/debian/mythtv_0.27.0.sql)

---

### Post by p2k on 2013-09-18
Affected entries are :
```

$ grep CYCLEAUDIOCHAN /usr/share/mythtv/sql/mythtv_0.27.0.sql | sed 's/)[,;](/)\n(/g' | tail -n +2 | awk ' { a[$0]++} ; END { for (i in a) print a[i] "\t" i } ' | sort | grep ^2
2       ('TV Frontend','CYCLEAUDIOCHAN','Cycle audio channels','','OLDHOSTNAME')
2       ('TV Playback','BACK','Exit or return to DVD menu','','OLDHOSTNAME')
2       ('TV Playback','CYCLEAUDIOCHAN','Cycle audio channels','','OLDHOSTNAME')
2       ('TV Playback','NEXTRAWTEXT','Next Text track','','OLDHOSTNAME')
2       ('TV Playback','PREVRAWTEXT','Previous Text track','','OLDHOSTNAME')
2       ('TV Playback','SELECTRAWTEXT_0','Display Text Subtitle 1','','OLDHOSTNAME')
2       ('TV Playback','TOGGLERAWTEXT','Toggle Text Subtitles','','OLDHOSTNAME')
2       ('TV Playback','TOGGLETEXT','Toggle External Subtitles','','OLDHOSTNAME')

```

---

### Post by p2k on 2013-09-18
Here's a fix for this issue:
```

patrick@myhostname:~/workspace/mythtv/packaging/deb/debian$ git diff
diff --git a/deb/debian/mythtv_0.27.0.sql b/deb/debian/mythtv_0.27.0.sql
index 79d7a35..b4ba7ab 100644
--- a/deb/debian/mythtv_0.27.0.sql
+++ b/deb/debian/mythtv_0.27.0.sql
@@ -1145,7 +1145,7 @@ CREATE TABLE `keybindings` (
 
 LOCK TABLES `keybindings` WRITE;
 /*!40000 ALTER TABLE `keybindings` DISABLE KEYS */;
-INSERT INTO `keybindings` VALUES ('Global','UP','Up Arrow','Up','OLDHOSTNAME'),('Global','DOWN','Down Arrow','Down','OLDHOSTNAME'),('Global','LEFT','Left Arrow','Left','OLDHOSTNAME'),('Global','RIGHT','Right Arrow','Right','OLDHOSTNAME'),('Global','SELECT','Select','Return,Enter,Space','OLDHOSTNAME'),('Global','ESCA
+INSERT INTO `keybindings` VALUES ('Global','UP','Up Arrow','Up','OLDHOSTNAME'),('Global','DOWN','Down Arrow','Down','OLDHOSTNAME'),('Global','LEFT','Left Arrow','Left','OLDHOSTNAME'),('Global','RIGHT','Right Arrow','Right','OLDHOSTNAME'),('Global','SELECT','Select','Return,Enter,Space','OLDHOSTNAME'),('Global','ESCA
 /*!40000 ALTER TABLE `keybindings` ENABLE KEYS */;
 UNLOCK TABLES;
 

```

Next one I get is:
```

+ cat /usr/share/mythtv/sql/mythtv_0.27.0.sql
ERROR 1062 (23000) at line 1148: Duplicate entry 'TV Editing-SAVEMAP-myhostname' for key 'PRIMARY'
dpkg: error processing mythtv-database (--configure):

```

To be continued...

---

### Post by p2k on 2013-09-18
This commit is the culprit : [https://github.com/MythTV/packaging/commit/efe0e0c02018b5db6ac77e969372e821f68ffa61](https://github.com/MythTV/packaging/commit/efe0e0c02018b5db6ac77e969372e821f68ffa61)
It creates duplicate entries by replacing test-virtualbox with OLDHOSTNAME...

The quick fix is to get the previous version of the file :
```

$ sudo wget "https://github.com/MythTV/packaging/raw/223a44cf9df0c85c38f5dbda874d900e74d1727a/deb/debian/mythtv_0.27.0.sql" -O /usr/share/mythtv/sql/mythtv_0.27.0.sql
--2013-09-18 09:52:43--  https://github.com/MythTV/packaging/raw/223a44cf9df0c85c38f5dbda874d900e74d1727a/deb/debian/mythtv_0.27.0.sql
Resolving github.com (github.com)... 192.30.252.129
Connecting to github.com (github.com)|192.30.252.129|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.github.com/MythTV/packaging/223a44cf9df0c85c38f5dbda874d900e74d1727a/deb/debian/mythtv_0.27.0.sql [following]
--2013-09-18 09:52:44--  https://raw.github.com/MythTV/packaging/223a44cf9df0c85c38f5dbda874d900e74d1727a/deb/debian/mythtv_0.27.0.sql
Resolving raw.github.com (raw.github.com)... 185.31.19.133
Connecting to raw.github.com (raw.github.com)|185.31.19.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 229366 (224K) [text/plain]
Saving to: &#8216;/usr/share/mythtv/sql/mythtv_0.27.0.sql&#8217;

100%[====================================================================================================================================================================================================================================================================================>] 229,366      507KB/s   in 0.4s   

2013-09-18 09:52:45 (507 KB/s) - &#8216;/usr/share/mythtv/sql/mythtv_0.27.0.sql&#8217; saved [229366/229366]

```

And re-run installation:
```

$ sudo aptitude install mythtv-database
The following partially installed packages will be configured:
  mythtv-database
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up mythtv-database (2:0.27.0+fixes.20130918.033883b-0ubuntu0mythbuntu3) ...
+ MYSQL=/usr/share/mythtv/sql/mythtv*.sql
+ MYSQLCONFIG=/etc/mysql/conf.d/mythtv.cnf
+ FSTAB=/etc/fstab
+ NEWIP=127.0.0.1
+ cat /etc/hostname
+ LOCALHOSTNAME=myhostname
+ . /usr/share/debconf/confmodule
+ [ !  ]
+ PERL_DL_NONLAZY=1
+ export PERL_DL_NONLAZY
+ [  ]
+ exec /usr/share/debconf/frontend /var/lib/dpkg/info/mythtv-database.postinst configure 
+ MYSQL=/usr/share/mythtv/sql/mythtv*.sql
+ MYSQLCONFIG=/etc/mysql/conf.d/mythtv.cnf
+ FSTAB=/etc/fstab
+ NEWIP=127.0.0.1
+ cat /etc/hostname
+ LOCALHOSTNAME=myhostname
+ . /usr/share/debconf/confmodule
+ [ ! 1 ]
+ [ -z  ]
+ exec
+ [  ]
+ exec
+ DEBCONF_REDIR=1
+ export DEBCONF_REDIR
+ return 0
+ database=mythconverg
+ db_get mythtv/mysql_mythtv_user
+ _db_cmd GET mythtv/mysql_mythtv_user
+ _db_internal_IFS=

+ IFS=
+ printf %s\n GET mythtv/mysql_mythtv_user
+ IFS=

+ IFS=
 read -r _db_internal_line
+ RET=mythtv
+ return 0
+ mythtv_username=mythtv
+ db_get mythtv/mysql_mythtv_password
+ _db_cmd GET mythtv/mysql_mythtv_password
+ _db_internal_IFS=

+ IFS=
+ printf %s\n GET mythtv/mysql_mythtv_password
+ IFS=

+ IFS=
 read -r _db_internal_line
+ RET=LY2MUGYh
+ return 0
+ mythtv_password=LY2MUGYh
+ db_get mythtv/mysql_admin_user
+ _db_cmd GET mythtv/mysql_admin_user
+ _db_internal_IFS=

+ IFS=
+ printf %s\n GET mythtv/mysql_admin_user
+ IFS=

+ IFS=
 read -r _db_internal_line
+ RET=debian-sys-maint
+ return 0
+ admin_username=debian-sys-maint
+ [ debian-sys-maint = debian-sys-maint ]
+ SECURITY_INFO=--defaults-file=/etc/mysql/debian.cnf
+ [  = localhost ]
+ [ -f /etc/mysql/conf.d/mythtv.cnf ]
+ db_get mythtv/public_bind
+ _db_cmd GET mythtv/public_bind
+ _db_internal_IFS=

+ IFS=
+ printf %s\n GET mythtv/public_bind
+ IFS=

+ IFS=
 read -r _db_internal_line
+ RET=false
+ return 0
+ [ -n false ]
+ [ false = true ]
+ sed -i -e s/^bind/#bind/ /etc/mysql/conf.d/mythtv.cnf
+ mysql --defaults-file=/etc/mysql/debian.cnf mythconverg
+ echo SELECT NULL;
+ mysql --defaults-file=/etc/mysql/debian.cnf mythconverg
+ echo SELECT value FROM settings LIMIT 1, 1;
+ prepare_database
+ mysql --defaults-file=/etc/mysql/debian.cnf mythconverg
+ sed -e s/Terra/Mythbuntu/g; s/OLDHOSTNAME/myhostname/g; s/127.0.0.1/127.0.0.1/g; s/blueosd/BlackCurves-OSD/g
+ cat /usr/share/mythtv/sql/mythtv_0.27.0.sql
+ mysql --defaults-file=/etc/mysql/debian.cnf mythconverg
+ echo UPDATE settings SET data = '127.0.0.1' WHERE settings.value = 'BackendServerIP' AND settings.hostname = 'myhostname';
+ mysql --defaults-file=/etc/mysql/debian.cnf mythconverg
+ echo UPDATE settings SET data = '127.0.0.1' WHERE settings.value = 'MasterServerIP';
+ update_database
+ mysql --defaults-file=/etc/mysql/debian.cnf mythconverg
+ echo GRANT ALL PRIVILEGES ON mythconverg.* TO mythtv@localhost IDENTIFIED BY 'LY2MUGYh';
+ mysql --defaults-file=/etc/mysql/debian.cnf mythconverg
+ echo GRANT ALL PRIVILEGES ON mythconverg.* TO mythtv@'%' IDENTIFIED BY 'LY2MUGYh';
+ mysql --defaults-file=/etc/mysql/debian.cnf mysql
+ mysql_tzinfo_to_sql /usr/share/zoneinfo/
+ db_set mythtv/mysql_admin_password 
+ _db_cmd SET mythtv/mysql_admin_password 
+ _db_internal_IFS= 

+ IFS= 
+ printf %s\n SET mythtv/mysql_admin_password 
+ IFS=  

+ IFS=
 read -r _db_internal_line
+ RET=value set
+ return 0
+ db_set mythtv/mysql_mythtv_password 
+ _db_cmd SET mythtv/mysql_mythtv_password 
+ _db_internal_IFS= 

+ IFS= 
+ printf %s\n SET mythtv/mysql_mythtv_password 
+ IFS=  

+ IFS=
 read -r _db_internal_line
+ RET=value set
+ return 0
+ exit 0

```

The proper fix is to remove test-virtualbox entries.
I'll submit a pull request...

---

### Post by p2k on 2013-09-18
Pull request submitted: [https://github.com/MythTV/packaging/pull/34](https://github.com/MythTV/packaging/pull/34)

---

