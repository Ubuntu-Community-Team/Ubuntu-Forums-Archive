---
title: "Couldn't install mysql-server   E: Sub-process /usr/bin/dpkg returned an error code ("
date: 2016-02-20
forum: Installation &amp; Upgrades
---

### Post by aeth3r on 2016-02-20
```
root@xxx:~# apt-get install mysql-server -y
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  mysql-server-5.5
Suggested packages:
  tinyca mailx
The following NEW packages will be installed:
  mysql-server mysql-server-5.5
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1760 kB of archives.
After this operation, 32.8 MB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main mysql-server-5.5 amd64 5.5.47-0ubuntu0.14.04.1 [1748 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main mysql-server all 5.5.47-0ubuntu0.14.04.1 [11.8 kB]
Fetched 1760 kB in 2s (669 kB/s)
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76, <> line 2.)
debconf: falling back to frontend: Readline
Preconfiguring packages ...
(Reading database ... 15862 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
Aborting downgrade from (at least) 10.1 to 5.5.
If are sure you want to downgrade to 5.5, remove the file
/var/lib/mysql/debian-*.flag and try installing again.
dpkg: error processing archive /var/cache/apt/archives/mysql-server-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
Selecting previously unselected package mysql-server.
Preparing to unpack .../mysql-server_5.5.47-0ubuntu0.14.04.1_all.deb ...
Unpacking mysql-server (5.5.47-0ubuntu0.14.04.1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I've tried "sudo apt-get clean" and "sudo apt-get install -f" yet it still shows the above message.


Runnning "sudo dpkg --configure -a" gives me the below message.
```
root@xxx:~# dpkg --configure -a
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not installed.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server
```

Any help would be greatly appreciated. Thanks!!

---

### Post by potato5 on 2016-02-20
Try:
```
sudo aptitude -f install
```
or/and
```
sudo aptitude install mysql-server
```

---

### Post by Bashing-om on 2016-02-20
aeth3r; Hey ...

Let's see if we can find out the why:
> 
mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not installed.

What results when we attempt to install the requested package ?
```

sudo apt install mysql-server-5.5

```

It all stats with a 1st step;
[INDENT][INDENT]looks like a good place to me
[/INDENT][/INDENT]

---

### Post by aeth3r on 2016-02-20
Hi guys, thanks for helping!:D

Running apt-get install mysql-server-5.5 gives me the below error message.
```

root@xxx:~# apt-get install mysql-server-5.5
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  tinyca mailx
The following NEW packages will be installed:
  mysql-server-5.5
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1748 kB of archives.
After this operation, 32.7 MB of additional disk space will be used.
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76, <> line 1.)
debconf: falling back to frontend: Readline
Preconfiguring packages ...
(Reading database ... 15866 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
Aborting downgrade from (at least) 10.1 to 5.5.
If are sure you want to downgrade to 5.5, remove the file
/var/lib/mysql/debian-*.flag and try installing again.
dpkg: error processing archive /var/cache/apt/archives/mysql-server-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
[B]Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

```

Here's what i get after running apt-get -f install, same as before.
```
root@xxx:~# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  mysql-server-5.5
Suggested packages:
  tinyca mailx
The following NEW packages will be installed:
  mysql-server-5.5
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1748 kB of archives.
After this operation, 32.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76, <> line 1.)
debconf: falling back to frontend: Readline
Preconfiguring packages ...
(Reading database ... 15866 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
Aborting downgrade from (at least) 10.1 to 5.5.
If are sure you want to downgrade to 5.5, remove the file
/var/lib/mysql/debian-*.flag and try installing again.
dpkg: error processing archive /var/cache/apt/archives/mysql-server-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
[B]Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

```

---

### Post by MAFoElffen on 2016-02-21
Look at the error.. 
```

debconf: ([COLOR=#ff0000]No usable dialog-like program is installed[/COLOR], so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/[COLOR=#ff0000]Dialog[/COLOR].pm line 76.)

```
reading your error... That script line checks for and cannot find [COLOR=#ff0000]dialog[/COLOR], so try this:
```

sudo apt-get install dialog
sudo apt-get install -f

```

---

### Post by aeth3r on 2016-02-21
Hi MAFoElffen,
Here's what i get after running install dialog and -f install.

```
root@xxx:~# apt-get install dialog
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 mysql-server : Depends: mysql-server-5.5 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@xxx:~# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  mysql-server-5.5
Suggested packages:
  tinyca mailx
The following NEW packages will be installed:
  mysql-server-5.5
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1748 kB of archives.
After this operation, 32.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76, <> line 1.)
debconf: falling back to frontend: Readline
Preconfiguring packages ...
(Reading database ... 15866 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
Aborting downgrade from (at least) 10.1 to 5.5.
If are sure you want to downgrade to 5.5, remove the file
/var/lib/mysql/debian-*.flag and try installing again.
dpkg: error processing archive /var/cache/apt/archives/mysql-server-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@xxx:~#

```

---

### Post by steeldriver on 2016-02-21
I think the significant error is
```

Aborting downgrade from (at least) 10.1 to 5.5.
If are sure you want to downgrade to 5.5, remove the file
/var/lib/mysql/debian-*.flag and try installing again.

```

Did you previously install mariadb by any chance?

---

### Post by aeth3r on 2016-02-21
> **steeldriver said:**
> I think the significant error is
```

Aborting downgrade from (at least) 10.1 to 5.5.
If are sure you want to downgrade to 5.5, remove the file
/var/lib/mysql/debian-*.flag and try installing again.

```

Did you previously install mariadb by any chance?

Hi steeldriver,
I don't remember having it installed.
And this is what i get after removing the said file, trying to reconfigure it, changing password and starting it.
```
root@xxx:~# apt-cache show mysql-server | grep Version
Version: 5.5.47-0ubuntu0.14.04.1
Version: 5.5.35+dfsg-1ubuntu1

```

```

[B]root@xxx:/var/lib/mysql# cp debian-10.1.flag debian-10.1.flag.backup
root@xxx:/var/lib/mysql# rm debian-10.1.flag
root@xxx:/var/lib/mysql# apt-get install mysql-server-5.5[/B]
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  tinyca mailx
The following NEW packages will be installed:
  mysql-server-5.5
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1748 kB of archives.
After this operation, 32.7 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ trusty-updates/main mysql-server-5.5 amd64 5.5.47-0ubuntu0.14.04.1 [1748 kB]
Fetched 1748 kB in 3s (445 kB/s)
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76, <> line 1.)
debconf: falling back to frontend: Readline
Preconfiguring packages ...
(Reading database ... 15866 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
 * Stopping MariaDB database server mysqld                               [ OK ]
Unpacking mysql-server-5.5 (5.5.47-0ubuntu0.14.04.1) ...
Setting up mysql-server-5.5 (5.5.47-0ubuntu0.14.04.1) ...
Installing new version of config file /etc/logrotate.d/mysql-server ...
Installing new version of config file /etc/mysql/conf.d/mysqld_safe_syslog.cnf ...
Installing new version of config file /etc/mysql/debian-start ...

Configuration file '/etc/init.d/mysql'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** mysql (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/init.d/mysql ...
Installing new version of config file /etc/apparmor.d/usr.sbin.mysqld ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
160221 10:08:02 [Note] /usr/sbin/mysqld (mysqld 5.5.47-0ubuntu0.14.04.1-log) starting as process 18342 ...
160221 10:08:02 [Warning] Using unique option prefix myisam_recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
160221 10:08:02 [Note] Plugin 'FEDERATED' is disabled.
160221 10:08:02 InnoDB: The InnoDB memory heap is disabled
160221 10:08:02 InnoDB: Mutexes and rw_locks use GCC atomic builtins
160221 10:08:02 InnoDB: Compressed tables use zlib 1.2.8
160221 10:08:02 InnoDB: Using Linux native AIO
160221 10:08:02 InnoDB: Initializing buffer pool, size = 256.0M
160221 10:08:02 InnoDB: Completed initialization of buffer pool
160221 10:08:02 InnoDB: highest supported file format is Barracuda.
160221 10:08:02  InnoDB: Waiting for the background threads to start
160221 10:08:03 InnoDB: 5.5.47 started; log sequence number 1617932
160221 10:08:03 [ERROR] /usr/sbin/mysqld: unknown variable 'log_slow_verbosity=query_plan'
160221 10:08:03 [ERROR] Aborting

160221 10:08:03  InnoDB: Starting shutdown...
160221 10:08:04  InnoDB: Shutdown completed; log sequence number 1617932
160221 10:08:04 [Note] /usr/sbin/mysqld: Shutdown complete

Configuring mysql-server-5.5
----------------------------

Unable to set password for the MySQL "root" user

An error occurred while setting the password for the MySQL administrative user.
This may have happened because the account already has a password, or because of
a communication problem with the MySQL server.

You should check the account's password after the package installation.

Please read the /usr/share/doc/mysql-server-5.5/README.Debian file for more
information.

start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing package mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

**root@xxx:/var/lib/mysql# dpkg-reconfigure mysql-server-5.5**
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
/usr/sbin/dpkg-reconfigure: mysql-server-5.5 is broken or not fully installed

**root@xxx:/var/lib/mysql# mysqladmin -u root password XXXXXXXXXX**
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

**root@xxx:/var/lib/mysql# /etc/init.d/mysql start**
 * Starting MySQL database server mysqld                                 [fail]

```

UPDATE:
```

**root@xxx:/etc/network# dpkg --get-selections | grep mysql**
libdbd-mysql-perl                               install
libmysqlclient18                                install
mysql-client-5.5                                install
mysql-client-core-5.5                           install
mysql-common                                    install
mysql-server-5.5                                deinstall
mysql-server-core-5.5                           install
php5-mysql                                      install
**root@xxx:/etc/network# apt-get install mysql-server-5.5**
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  tinyca mailx
The following NEW packages will be installed:
  mysql-server-5.5
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1748 kB of archives.
After this operation, 32.7 MB of additional disk space will be used.
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76, <> line 1.)
debconf: falling back to frontend: Readline
Preconfiguring packages ...
Configuring mysql-server-5.5
----------------------------

While not mandatory, it is highly recommended that you set a password for the
MySQL administrative "root" user.

If this field is left blank, the password will not be changed.

[COLOR=#ff0000]New password for the MySQL "root" user:[/COLOR]



[COLOR=#ff0000]Repeat password for the MySQL "root" user:[/COLOR]


Selecting previously unselected package mysql-server-5.5.
(Reading database ... 15862 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
Unpacking mysql-server-5.5 (5.5.47-0ubuntu0.14.04.1) ...
Setting up mysql-server-5.5 (5.5.47-0ubuntu0.14.04.1) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
160221 10:38:57 [Note] /usr/sbin/mysqld (mysqld 5.5.47-0ubuntu0.14.04.1-log) starting as process 21687 ...
160221 10:38:57 [Warning] Using unique option prefix myisam_recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
160221 10:38:57 [Note] Plugin 'FEDERATED' is disabled.
160221 10:38:57 InnoDB: The InnoDB memory heap is disabled
160221 10:38:57 InnoDB: Mutexes and rw_locks use GCC atomic builtins
160221 10:38:57 InnoDB: Compressed tables use zlib 1.2.8
160221 10:38:57 InnoDB: Using Linux native AIO
160221 10:38:57 InnoDB: Initializing buffer pool, size = 256.0M
160221 10:38:57 InnoDB: Completed initialization of buffer pool
160221 10:38:57 InnoDB: highest supported file format is Barracuda.
160221 10:38:57  InnoDB: Waiting for the background threads to start
160221 10:38:58 InnoDB: 5.5.47 started; log sequence number 1617932
160221 10:38:58 [ERROR] /usr/sbin/mysqld: unknown variable 'log_slow_verbosity=query_plan'
160221 10:38:58 [ERROR] Aborting

160221 10:38:58  InnoDB: Starting shutdown...
160221 10:38:59  InnoDB: Shutdown completed; log sequence number 1617932
160221 10:38:59 [Note] /usr/sbin/mysqld: Shutdown complete

Configuring mysql-server-5.5
----------------------------

Unable to set password for the MySQL "root" user

An error occurred while setting the password for the MySQL administrative user.
This may have happened because the account already has a password, or because of
a communication problem with the MySQL server.

You should check the account's password after the package installation.

Please read the /usr/share/doc/mysql-server-5.5/README.Debian file for more
information.

start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing package mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.5
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by MAFoElffen on 2016-02-21
It is a catch-22 type of thing.

Whe you ran the install for the package dialog, apt was in a broken state ... because MySQL was not installed because dialog was not installed. 

Before you can install My-SQL, you need to fix the original error, which is to install the pre-install scripts dependency "dialog". dialog will not install with a broken apt state, so tries to continue installing my-sql... So, try to back-ff the installation before fixing the foundation.
```

sudo apt-get --force-yes remove my-sql
sudo dpkg -r my-sql

```
Do either of those back off the installation?

If so, (and only then,) then continue with 
```

sudo apt-get install dialog

```

---

### Post by Bashing-om on 2016-02-21
aeth3r; Hey ...

Upfront, I now have my learning cap on .

EDIT: @ MAFoElffen; 
Mike :) , I failed to see there was an update on the thread prior to me hitting the send button. Great to me to see my theory confirmed !
-----------------------
I am with steeldriver, in that we have a version conflict with mysql-server-5.5 , somewhere - still even after removing " /var/lib/mysql/debian-* " .
-OR- also maybe that the package " dialog " is not fully installed ?? <-----

Confirm that the system thinks this is trusty:
```

lsb_release -a

```
as I show the current supported version:
> 
sysop@1404mini:~$ apt-cache show mysql-server-5.5
<snip>
Version: 5.5.47-0ubuntu0.14.04.1
Filename: pool/main/m/mysql-5.5/mysql-server-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb
<snip>

That we are attempting to get to properly install and we have now:
> 
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76, <> line 1.)
debconf: falling back to frontend: Readline
Preconfiguring packages ...


Which makes us want to look at that file .. is it corrupted ?
```

cat /usr/share/perl5/Debconf/FrontEnd/Dialog.pm

```

BUT !! I presently do not get the gist of this, as my system, line 76 :
> 
}
	else {
		die gettext("No usable dialog-like program is installed, so the dialog based frontend cannot be used.");



Is line 1 corrupted ?
Mine:
> 
#!/usr/bin/perl -w


Does line 53 : mine:
> 
elsif (Debconf::Path::find("dialog") &&

Apply ??
Are we now looking that " dialog " is not fully installed ?
What returns :
```

dpkg -l dialog
apt-cache policy dialog

```

Getting the package manager in a happy state.
[INDENT][INDENT]give it what it wants and
[INDENT][INDENT][INDENT][INDENT]it will go away
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aeth3r on 2016-02-22
Hey MAFoElffen & Bashing-om,

Thanks for helping, really appreciate it! Issue has been resolved by installing MariaDB. Would you guys like to continue to put on your learning cap and continue troubleshooting?  
This forum is definitely the most **USERS**-friendly forum..... :D

---

### Post by Bashing-om on 2016-02-22
aeth3r; Hey Hey ...

It is good that you provided what it took to obtain resolution.

Yeah, I am always open to a learning experience, a new situation open a new thread - and we all have at it .

As the current condition is resolved:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all of 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aeth3r on 2016-02-23
> **Bashing-om said:**
> aeth3r; Hey Hey ...

It is good that you provided what it took to obtain resolution.

Yeah, I am always open to a learning experience, a new situation open a new thread - and we all have at it .

As the current condition is resolved:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
[INDENT][INDENT]'buntu[INDENT][INDENT][INDENT]all of 1 and one for all
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


:popcorn:

---

