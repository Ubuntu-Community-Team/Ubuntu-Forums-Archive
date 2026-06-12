---
title: "Can't connect to MSSQL via odbc freetds X64 Ubuntu 12.04"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by cx19642 on 2013-08-22
I Can't connect to a MSSQL database via odbc and freetds on X64 Ubuntu 12.04.
With the database plugin of MonoDeevelop I can connect to the mssql database under Ubuntu 12.04 X64, so I know it must be possible tot connect to the database.

I installed:
odbcinst
tdsodbc
unixodbc

If a run "tsql -S mssl -U etl"  I get the message: 
Error 20012 (severity 2):
    Server name not found in configuration files.
locale is "en_US.UTF-8"
locale charset is "UTF-8"
using default charset "UTF-8"
Error 20013 (severity 2):
    Unknown host machine name.
There was a problem connecting to the server


If a run "isql -v mssql etl etl_01" I get the message:
[S1000][unixODBC][FreeTDS][SQL Server]Unable to connect to data source
[01000][unixODBC][FreeTDS][SQL Server]Unknown host machine name.
[ISQL]ERROR: Could not SQLConnect


With the database plugin of MonoDevelop the servername is 192.168.2.65\SQL2012_VB01.
Where \SQL2012_VB01 is the database instance name and 192.168.2.65 is the hostname of the database server.

What am I doning wrong?

---

### Post by Sukesh_Hoogan on 2013-09-03
Can you post the settings in FreeTDS.conf, ODBCINST.ini and ODBC.ini files.

---

