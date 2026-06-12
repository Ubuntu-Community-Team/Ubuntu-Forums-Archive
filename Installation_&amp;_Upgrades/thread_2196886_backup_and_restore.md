---
title: "backup and restore"
date: 2014-01-01
forum: Installation &amp; Upgrades
---

### Post by deanie44 on 2014-01-01
Hi everyone.  Happy New Year!  I am trying to backup the database in Mythtv without success.  I have read several articles and posts, but what I am doing is not working.  Here is the output of the terminal:

salliemae@salliemae:~$ mythconverg_backup.pl --verbose


Configuring environment:
  -    username: salliemae
  -        HOME: /home/salliemae
  - MYTHCONFDIR: /home/salliemae/.mythtv


Parsing configuration files:
  - checking: /home/salliemae/.mythtv/config.xml
     parsing: /home/salliemae/.mythtv/config.xml
  - checking: /home/salliemae/.mythtv/backuprc
     parsing: /home/salliemae/.mythtv/backuprc


Applying command-line arguments.


Checking configuration.


Database Information:
         DBHostName: localhost
             DBPort: 3306
         DBUserName: mythtv
         DBPassword: XXX
             DBName: mythconverg
        DBSchemaVer: 
  DBBackupDirectory: /home/mythtv
   DBBackupFilename: 


Executables:
          mysqldump: mysqldump
           compress: gzip


ERROR: DBBackupDirectory is not a directory or is not writable. Please specify
       a directory in your database information file using DBBackupDirectory.
       If not using a database information file, please specify the 
        --directory command-line option.


Invalid backup directory, stopped at /usr/local/bin/mythconverg_backup.pl line 870.
salliemae@salliemae:~$ 

I do not understand what I am doing wrong.  Can someone please help me.  Any suggestions will be appreciated.  sister5091

---

