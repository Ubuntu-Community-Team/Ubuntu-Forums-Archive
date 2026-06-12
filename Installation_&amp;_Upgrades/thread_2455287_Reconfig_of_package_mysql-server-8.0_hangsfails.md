---
title: "Reconfig of package mysql-server-8.0 hangs/fails"
date: 2020-12-16
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2020-12-16
I'm running Ubuntu 20.04.1 LTS server and have problems during updates as the configuration of the mysql server fails.

I can reproduce the issue by trying to reconfigure the package
```
sudo dpkg --configure -a
```

The process starts (see attachment sc1), but never finishes.
/var/log/mysql/error.log (see attached sc1) shows warnings, but no errors; I have disabled the X plugin

See attachment sc3 for the related processes that are running. 

While I posted this, the process finished with the following result




Thanks```
llist@mail:~$ sudo dpkg --configure -a
Setting up mysql-server-8.0 (8.0.22-0ubuntu0.20.04.3) ...
mysqld will log errors to /var/log/mysql/error.log
mysqld is running as pid 3977
Job for mysql.service failed because a timeout was exceeded.
See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.
&#9679; mysql.service - MySQL Community Server
     Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
     Active: activating (auto-restart) (Result: timeout) since Thu 2020-12-17 12:19:37 AEDT; 10ms ago
    Process: 4120 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
    Process: 4154 ExecStart=/usr/sbin/mysqld (code=exited, status=0/SUCCESS)
   Main PID: 4154 (code=exited, status=0/SUCCESS)

Dec 17 12:19:38 mail systemd[1]: mysql.service: Scheduled restart job, restart counter is at 1.
Dec 17 12:19:38 mail systemd[1]: Stopped MySQL Community Server.
Dec 17 12:19:38 mail systemd[1]: Starting MySQL Community Server...
dpkg: error processing package mysql-server-8.0 (--configure):
 installed mysql-server-8.0 package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-8.0; however:
  Package mysql-server-8.0 is not configured yet.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-8.0
 mysql-server

```

---

### Post by Bashing-om on 2020-12-16
lister171254; Hey -

Hummm ...
SSL library ??

What results:
```

sudo apt update
sudo apt upgrade
sudo dpkg-reconfigure mysql-server-8.0

```

   - Get it hot for a heat seeking missile -

---

### Post by lister171254 on 2020-12-17
```

>> sudo apt update
Hit:1 http://mirror.intergrid.com.au/ubuntu focal InRelease
Get:2 http://mirror.intergrid.com.au/ubuntu focal-updates InRelease [114 kB]
Get:3 http://mirror.intergrid.com.au/ubuntu focal-backports InRelease [101 kB]
Get:4 http://security.ubuntu.com/ubuntu focal-security InRelease [109 kB]
Get:5 http://mirror.intergrid.com.au/ubuntu focal-updates/main amd64 Packages [699 kB]
Get:6 http://mirror.intergrid.com.au/ubuntu focal-updates/main i386 Packages [391 kB]
Get:7 http://mirror.intergrid.com.au/ubuntu focal-updates/universe amd64 Packages [705 kB]
Get:8 http://mirror.intergrid.com.au/ubuntu focal-updates/universe i386 Packages [523 kB]
Fetched 2,642 kB in 1s (2,088 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.
--------------------------
>> sudo apt upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  libargon2-0
Use 'sudo apt autoremove' to remove it.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.


>> sudo apt autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  libargon2-0
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
2 not fully installed or removed.
After this operation, 19.5 kB disk space will be freed.
Do you want to continue? [Y/n]
(Reading database ... 127062 files and directories currently installed.)
Removing libargon2-0 (0~20190702-0.1+ubuntu18.04.1+deb.sury.org+1) ...
Setting up mysql-server-8.0 (8.0.22-0ubuntu0.20.04.3) ...
mysqld will log errors to /var/log/mysql/error.log
mysqld is running as pid 25885
Job for mysql.service failed because a timeout was exceeded.
See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.
&#9679; mysql.service - MySQL Community Server
     Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
     Active: activating (auto-restart) (Result: timeout) since Fri 2020-12-18 08:56:28 AEDT; 8ms ago
    Process: 26008 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
    Process: 26033 ExecStart=/usr/sbin/mysqld (code=exited, status=0/SUCCESS)
   Main PID: 26033 (code=exited, status=0/SUCCESS)

Dec 18 08:56:28 mail systemd[1]: mysql.service: Scheduled restart job, restart counter is at 1.
Dec 18 08:56:28 mail systemd[1]: Stopped MySQL Community Server.
Dec 18 08:56:28 mail systemd[1]: Starting MySQL Community Server...
dpkg: error processing package mysql-server-8.0 (--configure):
 installed mysql-server-8.0 package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-8.0; however:
  Package mysql-server-8.0 is not configured yet.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 mysql-server-8.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
W: Operation was interrupted before it could finish
-------------------------------------------

sudo dpkg-reconfigure mysql-server-8.0
/usr/sbin/dpkg-reconfigure: mysql-server-8.0 is broken or not fully installed


```

---

### Post by Bashing-om on 2020-12-17
lister171254; Welp -

As we have the advisory:
> 
mysql-server-8.0 is broken or not fully installed


Let's take a look at what the package manager further thinks:
```

apt policy mysql-server-8.0
dpkg -l mysql-server-8.0

```

and give consideration to stopping and purging it - and then re-installing.

As this is a server - production ? - best tread here very lightly.

[INDENT]haste made slowly :)
[/INDENT]

---

### Post by lister171254 on 2020-12-20
```

>> sudo apt policy mysql-server-8.0
mysql-server-8.0:
  Installed: 8.0.22-0ubuntu0.20.04.3
  Candidate: 8.0.22-0ubuntu0.20.04.3
  Version table:
 *** 8.0.22-0ubuntu0.20.04.3 500
        500 http://mirror.intergrid.com.au/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     8.0.19-0ubuntu5 500
        500 http://mirror.intergrid.com.au/ubuntu focal/main amd64 Packages

>> sudo dpkg -l mysql-server-8.0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name             Version                 Architecture Description
+++-================-=======================-============-========================================================
iF  mysql-server-8.0 8.0.22-0ubuntu0.20.04.3 amd64        MySQL database server binaries and system database setup

```

Yes, this is a production servers.
Thanks

---

### Post by Bashing-om on 2020-12-20
lister171254; Well well - not

We know we are working with the repo release of mysql-server-8.0 with the latest version available from the repo.
dpkg tells us:
> 
[color=red]iF[/color]  mysql-server-8.0 8.0.22-0ubuntu0.20.04.3

it's broke, Jim

All I know to do at this point is try and re-install. Least invasive that I do know.
try:
```

sudo apt install --reinstall mysql-server-8.0

```

See then what the package manager relates.

[INDENT]do not force it - yet
[INDENT][INDENT][INDENT]a bigger hammer ?
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lister171254 on 2020-12-20
```

>> sudo apt install --reinstall mysql-server-8.0
[sudo] password for llist: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 1 to reinstall, 0 to remove and 0 not to upgrade.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for mysql-server-8.0:amd64

```

Also ran

```

>> sudo apt install --reinstall mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 1 to reinstall, 0 to remove and 0 not to upgrade.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for mysql-server:amd64

```

---

### Post by Bashing-om on 2020-12-20
lister171254; That stinks -

Why in the world would the package manager think "No file name for mysql-server-8.0:amd64" ?

Are all the PreDepends and depends met ?

Maybe check all are installed in accordance with
```

apt depends mysql-server-8.0

```

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by lister171254 on 2020-12-20
```

>> sudo apt depends mysql-server-8.0
mysql-server-8.0
  PreDepends: adduser (>= 3.40)
  PreDepends: debconf
  PreDepends: mysql-common (>= 5.5)
  Depends: lsb-base (>= 3.0-10)
  Depends: mysql-client-8.0 (>= 8.0.22-0ubuntu0.20.04.3)
  Depends: mysql-common (>= 5.8+1.0.4~)
  Depends: mysql-server-core-8.0 (= 8.0.22-0ubuntu0.20.04.3)
  Depends: passwd
    passwd:i386
  Depends: <perl:any> (>= 5.6)
    perl:i386
    perl
  Depends: psmisc
    psmisc:i386
 |Depends: debconf (>= 0.5)
  Depends: <debconf-2.0>
    cdebconf
    debconf
  Conflicts: <mariadb-server-10.1>
  Conflicts: mariadb-server-10.3
  Conflicts: mysql-server-5.7
  Conflicts: <virtual-mysql-server>
    mariadb-server-10.3
    mysql-server-5.7
  Recommends: libhtml-template-perl
  Recommends: mecab-ipadic-utf8
  Suggests: <mailx>
    bsd-mailx
    mailutils
  Suggests: tinyca

```

One other thing I found was 
```

>> sudo dpkg -V mysql-server-8.0
??5?????? c /etc/apparmor.d/usr.sbin.mysqld
??5?????? c /etc/mysql/mysql.conf.d/mysqld.cnf

```
Have not found any explanation on what this means yet.

---

### Post by Bashing-om on 2020-12-22
lister171254; Yukkie

On me too -

As I do not have mysql installed - I can not follow through. Perhaps others here can offer better insights.

[INDENT]a know it all I am not
[/INDENT]

---

### Post by ianb1469 on 2021-06-02
I had the same error messages, and eventually resolved it: I had once manually created a file /etc/systemd/system/mysql.service/override.conf containing some override options. They seemed to silently stop the server starting. Deleting this file resolved the issue.

Ian

---

