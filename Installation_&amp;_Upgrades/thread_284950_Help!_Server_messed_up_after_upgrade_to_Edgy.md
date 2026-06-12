---
title: "Help! Server messed up after upgrade to Edgy"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by eldaria on 2006-10-26
I have been running Ubuntu Server 64 bit for a while now, everything has been running fine.
I upgraded my Kubuntu Desktops, and they all upgraded without a hitch.
So I decided to upgrade my Ubuntu server.

Upgrade went fine, it only came with one message telling me I would have to upgrade courier-authlib-userdb manually with the version of Authentication I'm running.

When it was done it came with an error message about courier depending on the above packages.
I was unable to install it as it tells me it depends on it self.
ok well that is a minor problem right now, so I figured maybe it needed a reboot.
Now this was a big mistake.
After reboot I have no network anymore, my sql server is not running and I get all kinds of Errors:

I guess the most critical is the fact that I have no network anymore, so I can't downgrade again, (Is this possible?)

These are the errors I get:

> 
* Loading hardware drivers...
/etc/rcS.D/S10udev: line 64: /sbin/udevplug: No such file or directory [COLOR="Red"][fail][/COLOR]


> * Setting up per-VC fonts...
* /dev/tty2
* /dev/tty3
* /dev/tty4
* /dev/tty5
* /dev/tty6
               [ ok ]
locale: Cannot set LC_ALL to default locale: no such file or directory
* INIT: Entering runlevel: 2


> 
* Starting Courier authdaemon...
/usr/lib/courier/authlib/authdaemond: line 31: /usr/sbin/courierlogger: No such file or directory
/usr/lib/courier/authlib/authdaemond: line31: exec: /usr/sbin/courierlogger: cannot execute: No such file or directory
              [COLOR="Red"][fail][/COLOR]


> 
Starting MySQL database server: mysqld.
.
.
.
.
.
.
.
.
.
.
.
.
.
...failed or took more than 6s.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!


> 
Starting ISPConfig sustem...
/root/ispconfig/httpd/bin/apachectl startssl: httpd started
Could not connect to MySQL server!ISPConfig sustem is now up and running!



Please help me either get it up and running with Edgy, or at least network so that I can roll back to a working setup of Dapper if this is possible.


Regards.
Brian.

---

### Post by martinoc on 2006-10-26
I had this issue today

do this 

cd /var/cache/apt/archive

dpkg -i courier-base_0.53.2-3ubuntu1_i386.deb

this will complain about dependancies - so note them and then do

dpkg --ignore-depends=comma,seperated,list,of,depends -i courier-base_0.53.2-3ubuntu1_i386.deb

next do 

dpkg -i courier-authdaemon_0.58-4ubuntu1_i386.deb

note the dependancies here and do

dpkg --ignore-depends=comma,seperated,list -i courier-authdaemon_0.58-4ubuntu1_i386.deb

then do 

apt-get -f install

Let me know if this helps.

---

### Post by eldaria on 2006-10-26
Thank you for responding,
First one listed a whole bunch of dependencies, but it still installed.
Second part however did not list any dependencies but rather a whole bunch of errors.
So did it when I tried to continue to step the apt-get -f install

Results of dpkg -i courier-authdaemon_0.58-4ubuntu1_amd64.deb

> 
(Reading database ... 39436 files and directories currently installed.)
Preparing to replace courier-authdaemon 0.47-13ubuntu5.1 (using courier-authdaemon_0.58-4ubuntu1_amd64.deb) ...
 * Stopping Courier authdaemon...        [80G /usr/lib/courier/authlib/authdaemond: line 31: /usr/sbin/courierlogger: No such file or directory
/usr/lib/courier/authlib/authdaemond: line 31: exec: /usr/sbin/courierlogger: cannot execute: No such file or directory

 [COLOR="Red"][fail][/COLOR]
invoke-rc.d: initscript courier-authdaemon, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
 * Stopping Courier authdaemon...        [80G /usr/lib/courier/authlib/authdaemond: line 31: /usr/sbin/courierlogger: No such file or directory
/usr/lib/courier/authlib/authdaemond: line 31: exec: /usr/sbin/courierlogger: cannot execute: No such file or directory

 [COLOR="Red"][fail][/COLOR]
invoke-rc.d: initscript courier-authdaemon, action "stop" failed.
dpkg: error processing courier-authdaemon_0.58-4ubuntu1_amd64.deb (--install):
 subprocess new pre-removal script returned error exit status 1
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_NL:en",
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
 * Starting Courier authdaemon...        [80G /usr/lib/courier/authlib/authdaemond: line 31: /usr/sbin/courierlogger: No such file or directory
/usr/lib/courier/authlib/authdaemond: line 31: exec: /usr/sbin/courierlogger: cannot execute: No such file or directory

 [COLOR="Red"][fail][/COLOR]
invoke-rc.d: initscript courier-authdaemon, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 courier-authdaemon_0.58-4ubuntu1_amd64.deb



And last part: apt-get -f install
> 
Reading package lists...
Building dependency tree...
Correcting dependencies... Done
The following extra packages will be installed:
  courier-authdaemon courier-authlib
The following NEW packages will be installed:
  courier-authlib
The following packages will be upgraded:
  courier-authdaemon
1 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
369 not fully installed or removed.
Need to get 0B/90.3kB of archives.
After unpacking 176kB of additional disk space will be used.
Do you want to continue [Y/n]? perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_NL:en",
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: courier-authdaemon: dependency problems, but removing anyway as you request:
 courier-base depends on courier-authdaemon; however:
  Package courier-authdaemon is to be removed.
dpkg: error processing courier-authdaemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Errors were encountered while processing:
 courier-authdaemon


Another thing which is very important to me is the SQL server, this because I have lots of data in there that I need.
Also the fact that my network card is no longer working is not a good thing.

Stupid me not taking a backup before starting an upgrade.

---

### Post by martinoc on 2006-10-26
Sorry, I left out  some packages :-# 

cd /var/cache/apt/archive

dpkg -i locales_2.3.22_all.deb

dpkg --ignore-depends=blah,blah -i locales_2.3.22_all.deb  
(if needed)

dpkg -i courier-authlib_0.58-4ubuntu1_i386.deb

dpkg --ignore-depends=comma,seperated,list -i courier-authlib_0.58-4ubuntu1_i386.deb

then try installing authdaemon as per above followed by

apt-get -f install

Tell me how this goes.

---

### Post by martinoc on 2006-10-26
The reason why your network and mysql is not working is because the new packages from the upgrade have not been configured yet

once you get your package manager fixed as above, everything will work.

---

### Post by eldaria on 2006-10-26
ok can not get past first step.

> 
dpkg -i courier-authlib_0.58-4ubuntu1_amd64.deb
dpkg: regarding courier-authlib_0.58-4ubuntu1_amd64.deb containing courier-authlib:
 courier-authlib conflicts with courier-authdaemon (<< 0.58)
  courier-authdaemon (version 0.47-13ubuntu5.1) is broken due to postinst failure.
dpkg: error processing courier-authlib_0.58-4ubuntu1_amd64.deb (--install): conflicting packages - not installing courier-authlib
Errors were encountered while processing:
 courier-authlib_0.58-4ubuntu1_amd64.deb


---

### Post by martinoc on 2006-10-26
I edited since the first post.

as far as I can remember, you need to do locales first

then try doing authlib

then authdaemon

then apt-get -f install

---

### Post by martinoc on 2006-10-26
Try it in this order:

cd /var/cache/apt/archive

dpkg -i locales_2.3.22_all.deb

dpkg --ignore-depends=blah,blah -i locales_2.3.22_all.deb
(if needed)

dpkg -i courier-authlib_0.58-4ubuntu1_i386.deb

dpkg --ignore-depends=comma,seperated,list -i courier-authlib_0.58-4ubuntu1_i386.deb

then try installing authdaemon as per above followed by

apt-get -f install

Tell me how this goes.

---

### Post by eldaria on 2006-10-26
Great, you saved me.

I needed to modify the command a bit.

dpkg --force-conflicts -i courier-authlib_0.58-4ubuntu1_amd64.deb

That worked.
Now my network works again, however MySQL still won't start.
Not after reboot either.

In syslog I get the follwoing when trying to "/etc/init.d/mysql start"

> 
Oct 26 13:38:59 lnx1 mysqld_safe[4022]: started
Oct 26 13:38:59 lnx1 mysqld[4025]: mysqld got signal 4;
Oct 26 13:38:59 lnx1 mysqld[4025]: This could be because you hit a bug. It is also possible that this binary
Oct 26 13:38:59 lnx1 mysqld[4025]: or one of the libraries it was linked against is corrupt, improperly built,
Oct 26 13:38:59 lnx1 mysqld[4025]: or misconfigured. This error can also be caused by malfunctioning hardware.
Oct 26 13:38:59 lnx1 mysqld[4025]: We will try our best to scrape up some info that will hopefully help diagnose
Oct 26 13:38:59 lnx1 mysqld[4025]: the problem, but since we have already crashed, something is definitely wrong
Oct 26 13:38:59 lnx1 mysqld[4025]: and this may fail.
Oct 26 13:38:59 lnx1 mysqld[4025]: 
Oct 26 13:38:59 lnx1 mysqld[4025]: key_buffer_size=0
Oct 26 13:38:59 lnx1 mysqld[4025]: read_buffer_size=131072
Oct 26 13:38:59 lnx1 mysqld[4025]: max_used_connections=0
Oct 26 13:38:59 lnx1 mysqld[4025]: max_connections=100
Oct 26 13:38:59 lnx1 mysqld[4025]: threads_connected=0
Oct 26 13:38:59 lnx1 mysqld[4025]: It is possible that mysqld could use up to 
Oct 26 13:38:59 lnx1 mysqld[4025]: key_buffer_size + (read_buffer_size + sort_buffer_size)*max_connections = 217599 K
Oct 26 13:38:59 lnx1 mysqld[4025]: bytes of memory
Oct 26 13:38:59 lnx1 mysqld[4025]: Hope that's ok; if not, decrease some variables in the equation.
Oct 26 13:38:59 lnx1 mysqld[4025]: 
Oct 26 13:38:59 lnx1 mysqld_safe[4031]: ended
Oct 26 13:39:13 lnx1 /etc/init.d/mysql[4188]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Oct 26 13:39:13 lnx1 /etc/init.d/mysql[4188]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Oct 26 13:39:13 lnx1 /etc/init.d/mysql[4188]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Oct 26 13:39:13 lnx1 /etc/init.d/mysql[4188]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Oct 26 13:39:13 lnx1 /etc/init.d/mysql[4188]:


---

### Post by martinoc on 2006-10-26
you still need to do  

apt-get -f install 

to finish configuring edgy packages

then reboot

if all services are running then do 

apt-get dist-upgrade

again to install the new init manager

---

### Post by eldaria on 2006-10-26
Ok did the apt-get -f install

This is the output:

> 
Reading package lists...
Building dependency tree...
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.24a-9) ...
 * Stopping MySQL database server mysqld        [ ok ]
 * Starting MySQL database server mysqld        [COLOR="Red"][fail][/COLOR]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Setting up sasl2-bin (2.1.19.dfsg1-0.2ubuntu3) ...
Starting SASL Authentication Daemon: (failed).
invoke-rc.d: initscript saslauthd, action "start" failed.
dpkg: error processing sasl2-bin (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
 sasl2-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by martinoc on 2006-10-26
go to the /var/cache/apt/archive

manually do dpkg -i <mysql5>.deb

see what dependancies are unmet

try dpkg -i on each one

try force config for any that need to be shoehorned in

let me know what you did

---

### Post by eldaria on 2006-10-26
Ok I have couple of differnet files with mysql.
This is a list:

> 
mysql-client_5.0.22-0ubuntu6.06.2_all.deb
mysql-client_5.0.22-0ubuntu6.06_all.deb
mysql-client_5.0.24a-9_all.deb
mysql-client-5.0_5.0.22-0ubuntu6.06.2_amd64.deb
mysql-client-5.0_5.0.22-0ubuntu6.06_amd64.deb
mysql-client-5.0_5.0.24a-9_amd64.deb
mysql-common_5.0.22-0ubuntu6.06.2_all.deb
mysql-common_5.0.22-0ubuntu6.06_all.deb
mysql-common_5.0.24a-9_all.deb
mysql-server_5.0.22-0ubuntu6.06.2_all.deb
mysql-server_5.0.22-0ubuntu6.06_all.deb
mysql-server_5.0.24a-9_all.deb
mysql-server-5.0_5.0.22-0ubuntu6.06.2_amd64.deb
mysql-server-5.0_5.0.22-0ubuntu6.06_amd64.deb
mysql-server-5.0_5.0.24a-9_amd64.deb


My guess is that it is one of these:

> 
dpkg -i mysql-server-5.0_5.0.24a-9_amd64.deb

(Reading database ... 39508 files and directories currently installed.)
Preparing to replace mysql-server-5.0 5.0.24a-9 (using mysql-server-5.0_5.0.24a-9_amd64.deb) ...
 * Stopping MySQL database server mysqld        [ ok ]
 * Stopping MySQL database server mysqld        [ ok ]
Unpacking replacement mysql-server-5.0 ...
Setting up mysql-server-5.0 (5.0.24a-9) ...
 * Stopping MySQL database server mysqld        [ ok ]
 * Starting MySQL database server mysqld        [COLOR="Red"][fail][/COLOR]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0



> 
dpkg -i 
mysql-server_5.0.24a-9_all.deb
(Reading database ... 39508 files and directories currently installed.)
Preparing to replace mysql-server 5.0.24a-9 (using mysql-server_5.0.24a-9_all.deb) ...
Unpacking replacement mysql-server ...
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server


---

### Post by martinoc on 2006-10-26
try starting mysqld manually or read the logs to see why init cannot start mysqld

---

### Post by eldaria on 2006-10-26
Same as earlier.

from /var/log/syslog

> 
Oct 26 23:06:05 lnx1 mysqld_safe[12665]: started
Oct 26 23:06:05 lnx1 mysqld[12668]: mysqld got signal 4;
Oct 26 23:06:05 lnx1 mysqld[12668]: This could be because you hit a bug. It is also possible that this binary
Oct 26 23:06:05 lnx1 mysqld[12668]: or one of the libraries it was linked against is corrupt, improperly built,
Oct 26 23:06:05 lnx1 mysqld[12668]: or misconfigured. This error can also be caused by malfunctioning hardware.
Oct 26 23:06:05 lnx1 mysqld[12668]: We will try our best to scrape up some info that will hopefully help diagnose
Oct 26 23:06:05 lnx1 mysqld[12668]: the problem, but since we have already crashed, something is definitely wrong
Oct 26 23:06:05 lnx1 mysqld[12668]: and this may fail.
Oct 26 23:06:05 lnx1 mysqld[12668]: 
Oct 26 23:06:05 lnx1 mysqld[12668]: key_buffer_size=0
Oct 26 23:06:05 lnx1 mysqld[12668]: read_buffer_size=131072
Oct 26 23:06:05 lnx1 mysqld[12668]: max_used_connections=0
Oct 26 23:06:05 lnx1 mysqld[12668]: max_connections=100
Oct 26 23:06:05 lnx1 mysqld[12668]: threads_connected=0
Oct 26 23:06:05 lnx1 mysqld[12668]: It is possible that mysqld could use up to 
Oct 26 23:06:05 lnx1 mysqld[12668]: key_buffer_size + (read_buffer_size + sort_buffer_size)*max_connections = 217599 K
Oct 26 23:06:05 lnx1 mysqld[12668]: bytes of memory
Oct 26 23:06:05 lnx1 mysqld[12668]: Hope that's ok; if not, decrease some variables in the equation.
Oct 26 23:06:05 lnx1 mysqld[12668]: 
Oct 26 23:06:05 lnx1 mysqld_safe[12674]: ended
Oct 26 23:06:19 lnx1 /etc/init.d/mysql[12813]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Oct 26 23:06:19 lnx1 /etc/init.d/mysql[12813]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Oct 26 23:06:19 lnx1 /etc/init.d/mysql[12813]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Oct 26 23:06:19 lnx1 /etc/init.d/mysql[12813]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Oct 26 23:06:19 lnx1 /etc/init.d/mysql[12813]: 


Looks like something is corrupted, Perhaps I should reinstall MySQL, can I do that without loosing the databases?
And if so, how do I tell apt to reinstall?

---

### Post by martinoc on 2006-10-26
you will have to use dpkg -r to remove mysql - all packages

as long as you dont purge (which is default) you wont lose any databases

once you have removed mysql  do

apt-get -f install

---

### Post by eldaria on 2006-10-26
> **martinoc said:**
> 
as long as you dont purge (which is default) you wont lose any databases


Does that mean that by default it purges or by default it does not? ;-)

---

### Post by eldaria on 2006-10-26
I have tried following.
apt-get remove mysql-common

This removed:
libmysqlclient15off, libdbd-mysql-perl, mysql-common, mysql-server-5.0, mysql-client-5.0

Then I:
apt-get install mysql-server

That installs all of the packages above.

But I still get same message in syslog.

Ok, it is getting late I have to go to bed.

---

### Post by codelad on 2006-10-27
I have exactly the same problem with mysql. 

I did manage to get mysql running, after purging all mysql-related packages. However, when I try to restart (or stop-start), it fails again. 

```

# sudo apt-get --purge remove mysql-common

```

removes the following packages:
  libdbd-mysql-perl* libmysqlclient15off* mysql-client* mysql-client-5.0*
  mysql-common* mysql-server* mysql-server-5.0*

```

# sudo apt-get install mysql-server mysql-client
.
.
.

Setting up mysql-server-5.0 (5.0.24a-9) ...
 * Stopping MySQL database server mysqld                                 [ ok ] 
 * Starting MySQL database server mysqld                                 [ ok ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

Setting up mysql-server (5.0.24a-9) ...

```

As of now, the server is up and running, and I'm able to access the default tables (I backed up all my tables, and removed them during the purge).

Now, when I try to restart (or stop/start), it always fails :(

```

# sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                 [ ok ] 
 * Starting MySQL database server mysqld                                 [fail] 

```

VJ

---

### Post by eldaria on 2006-10-27
Ok it seems as if something is no good with the new packages for SQL server.

This is how I got it working again.

apt-get remove mysql-common

This will remove:
libmysqlclient15off, libdbd-mysql-perl, mysql-common, mysql-server-5.0, mysql-client-5.0

Now i went to the /var/cache/apt/archives directory (Thanks to martinoc)

I installed the old version in the follwing order:

dpkg -i mysql-common_5.0.22-0ubuntu6.06.2_all.deb

dpkg -i libmysqlclient15off_5.0.22-0ubuntu6.06.2_amd64.deb

dpkg -i libdbd-mysql-perl_3.0002-2build1_amd64.deb

dpkg -i mysql-client-5.0_5.0.22-ubuntu6.06.2_amd64.deb

dpkg -i mysql-client_5.0_5.0.22-0ubuntu6.06.2_amd64.deb

dpkg -i mysql-server-5.0_5.0.22-0ubuntu6.06.2_amd64.deb

dpkg -i mysql-server_5.0.22-0ubuntu6.06.2_all.deb


and last I did a restart to verify:
 /etc/init.d/mysql restart

I verified it by logging into the database with:

> 
mysql -p
Enter password:
Welcome to the MySQL monitor. Commands end with æ or \g.
Your MySQL connection id is 14 to the server version: 5.0.22-Debian_0ubuntu6.06.2-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show databases;




This listed my databases.

However now I'm afraid of doing an apt-get update, since it might upgrade my mysql again.

---

### Post by martinoc on 2006-10-27
Unfortunatly, you need to finish apt-get -f install and apt-get dist-upgrade to finish the upgrade or your system will be in an inconsistent state.

first do an apt-get update to make sure you are using the latest packages

Try this and let us know how it goes.

---

### Post by martinoc on 2006-10-27
I have mysql 5 installed and working ok on one of my servers.

---

### Post by eldaria on 2006-10-27
Hmm, ok I tried it, in 2 ways.

First I did a upgrade telling it not to overwrite my my.cnf
After upgrade, mysql server no longer starting.

ok so I removed it again installed the old version 5.22 instead of 5.24a-9 that it upgrades to.

Then again I tried to do an dist-upgrade this time telling it to use the package maintained my.cnf, but again same thing happends.

This is the output of the dist-upgrade, and syslog.

```

Reading package lists...
Building dependency tree...
Reading state information...
The following packages have been kept back:
  proftpd python-soappy python-twisted-conch python-twisted-core
  python-twisted-mail python-twisted-names python-twisted-news
  python-twisted-runner python-twisted-web python-twisted-words
The following packages will be upgraded:
  libdbd-mysql-perl libmysqlclient15off mysql-client mysql-client-5.0
  mysql-common mysql-server mysql-server-5.0
7 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B/35.2MB of archives.
After unpacking 20.9MB of additional disk space will be used.
Do you want to continue [Y/n]? Preconfiguring packages ...
(Reading database ... 37760 files and directories currently installed.)
Preparing to replace mysql-common 5.0.22-0ubuntu6.06.2 (using .../mysql-common_5.0.24a-9_all.deb) ...
Unpacking replacement mysql-common ...
Preparing to replace libmysqlclient15off 5.0.22-0ubuntu6.06.2 (using .../libmysqlclient15off_5.0.24a-9_amd64.deb) ...
Unpacking replacement libmysqlclient15off ...
Preparing to replace libdbd-mysql-perl 3.0002-2build1 (using .../libdbd-mysql-perl_3.0006-1_amd64.deb) ...
Unpacking replacement libdbd-mysql-perl ...
Preparing to replace mysql-client 5.0.22-0ubuntu6.06.2 (using .../mysql-client_5.0.24a-9_all.deb) ...
Unpacking replacement mysql-client ...
Preparing to replace mysql-client-5.0 5.0.22-0ubuntu6.06.2 (using .../mysql-client-5.0_5.0.24a-9_amd64.deb) ...
Unpacking replacement mysql-client-5.0 ...
Preparing to replace mysql-server 5.0.22-0ubuntu6.06.2 (using .../mysql-server_5.0.24a-9_all.deb) ...
Unpacking replacement mysql-server ...
Preparing to replace mysql-server-5.0 5.0.22-0ubuntu6.06.2 (using .../mysql-server-5.0_5.0.24a-9_amd64.deb) ...
Stopping MySQL database server: mysqld.
Stopping MySQL database server: mysqld.
Unpacking replacement mysql-server-5.0 ...
Setting up mysql-common (5.0.24a-9) ...
Installing new version of config file /etc/mysql/my.cnf ...
Setting up libmysqlclient15off (5.0.24a-9) ...

Setting up libdbd-mysql-perl (3.0006-1) ...
Setting up mysql-client-5.0 (5.0.24a-9) ...
Setting up mysql-client (5.0.24a-9) ...
Setting up mysql-server-5.0 (5.0.24a-9) ...
Installing new version of config file /etc/init.d/mysql-ndb-mgm ...
Installing new version of config file /etc/init.d/mysql ...
Installing new version of config file /etc/init.d/mysql-ndb ...
Installing new version of config file /etc/mysql/debian-start ...
Installing new version of config file /etc/logcheck/ignore.d.workstation/mysql-server-5_0 ...
Installing new version of config file /etc/logcheck/ignore.d.server/mysql-server-5_0 ...
Installing new version of config file /etc/logcheck/ignore.d.paranoid/mysql-server-5_0 ...
 * Stopping MySQL database server mysqld        [ ok ]
 * Starting MySQL database server mysqld        [COLOR="Red"][fail][/COLOR]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

Oct 27 12:31:12 lnx1 mysqld[3615]: 061027 12:31:12 [Note] /usr/sbin/mysqld: Normal shutdown
Oct 27 12:31:12 lnx1 mysqld[3615]:
Oct 27 12:31:12 lnx1 mysqld[3615]: 061027 12:31:12  InnoDB: Starting shutdown...
Oct 27 12:31:14 lnx1 mysqld[3615]: 061027 12:31:14  InnoDB: Shutdown completed; log sequence number 0 43665
Oct 27 12:31:14 lnx1 mysqld[3615]: 061027 12:31:14 [Note] /usr/sbin/mysqld: Shutdown complete
Oct 27 12:31:14 lnx1 mysqld[3615]:
Oct 27 12:31:14 lnx1 mysqld_safe[3761]: ended
Oct 27 12:31:15 lnx1 mysqld_safe[3851]: started
Oct 27 12:31:15 lnx1 mysqld[3854]: 061027 12:31:15  InnoDB: Started; log sequence number 0 43665
Oct 27 12:31:15 lnx1 mysqld[3854]: 061027 12:31:15 [Note] /usr/sbin/mysqld: ready for connections.
Oct 27 12:31:15 lnx1 mysqld[3854]: Version: '5.0.22-Debian_0ubuntu6.06.2-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian Etch distribution
Oct 27 12:31:16 lnx1 /etc/mysql/debian-start[3889]: Running MySQL upgrade script in the background...
Oct 27 12:31:16 lnx1 /etc/mysql/debian-start[3893]: This script updates all the mysql privilege tables to be usable by
Oct 27 12:31:16 lnx1 /etc/mysql/debian-start[3893]: MySQL 4.0 and above.
Oct 27 12:31:16 lnx1 /etc/mysql/debian-start[3893]:
Oct 27 12:31:16 lnx1 /etc/mysql/debian-start[3893]: This is needed if you want to use the new GRANT functions,
Oct 27 12:31:16 lnx1 /etc/mysql/debian-start[3893]: CREATE AGGREGATE FUNCTION, stored procedures, or
Oct 27 12:31:16 lnx1 /etc/mysql/debian-start[3893]: more secure passwords in 4.1
Oct 27 12:31:16 lnx1 /etc/mysql/debian-start[3893]:
Oct 27 12:31:16 lnx1 /etc/mysql/debian-start[3893]: done
Oct 27 12:31:16 lnx1 /etc/mysql/debian-start[3920]: Checking for crashed MySQL tables in the background.
Oct 27 12:32:28 lnx1 postfix/anvil[1730]: statistics: max connection rate 1/60s for (smtp:67.30.130.180) at Oct 27 12:24:07
Oct 27 12:32:28 lnx1 postfix/anvil[1730]: statistics: max connection count 1 for (smtp:67.30.130.180) at Oct 27 12:24:07
Oct 27 12:32:28 lnx1 postfix/anvil[1730]: statistics: max cache size 2 at Oct 27 12:24:39
Oct 27 12:32:50 lnx1 mysqld[3854]: 061027 12:32:50 [Note] /usr/sbin/mysqld: Normal shutdown
Oct 27 12:32:50 lnx1 mysqld[3854]:
Oct 27 12:32:50 lnx1 mysqld[3854]: 061027 12:32:50  InnoDB: Starting shutdown...
Oct 27 12:32:53 lnx1 mysqld[3854]: 061027 12:32:53  InnoDB: Shutdown completed; log sequence number 0 43665
Oct 27 12:32:53 lnx1 mysqld[3854]: 061027 12:32:53 [Note] /usr/sbin/mysqld: Shutdown complete
Oct 27 12:32:53 lnx1 mysqld[3854]:
Oct 27 12:32:53 lnx1 mysqld_safe[4113]: ended
Oct 27 12:32:58 lnx1 mysqld_safe[4303]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Oct 27 12:32:58 lnx1 mysqld_safe[4303]: To do so, start the server, then issue the following commands:
Oct 27 12:32:58 lnx1 mysqld_safe[4303]: /usr/bin/mysqladmin -u root password 'new-password'
Oct 27 12:32:58 lnx1 mysqld_safe[4303]: /usr/bin/mysqladmin -u root -h lnx1.eldaria.net password 'new-password'
Oct 27 12:32:58 lnx1 mysqld_safe[4303]: See the manual for more instructions.
Oct 27 12:32:58 lnx1 mysqld_safe[4303]:
Oct 27 12:32:58 lnx1 mysqld_safe[4303]: NOTE:  If you are upgrading from a MySQL <= 3.22.10 you should run
Oct 27 12:32:58 lnx1 mysqld_safe[4303]: the /usr/bin/mysql_fix_privilege_tables. Otherwise you will not be
Oct 27 12:32:58 lnx1 mysqld_safe[4303]: able to use the new GRANT command!
Oct 27 12:32:58 lnx1 mysqld_safe[4303]:
Oct 27 12:32:58 lnx1 mysqld_safe[4303]: Please report any problems with the /usr/bin/mysqlbug script!
Oct 27 12:32:58 lnx1 mysqld_safe[4303]:
Oct 27 12:32:58 lnx1 mysqld_safe[4303]: The latest information about MySQL is available on the web at
Oct 27 12:32:58 lnx1 mysqld_safe[4303]: http://www.mysql.com
Oct 27 12:32:58 lnx1 mysqld_safe[4303]: Support MySQL by buying support/licenses at http://shop.mysql.com
Oct 27 12:32:59 lnx1 mysqld_safe[4535]: started
Oct 27 12:32:59 lnx1 mysqld[4538]: mysqld got signal 4;
Oct 27 12:32:59 lnx1 mysqld[4538]: This could be because you hit a bug. It is also possible that this binary
Oct 27 12:32:59 lnx1 mysqld[4538]: or one of the libraries it was linked against is corrupt, improperly built,
Oct 27 12:32:59 lnx1 mysqld[4538]: or misconfigured. This error can also be caused by malfunctioning hardware.
Oct 27 12:32:59 lnx1 mysqld[4538]: We will try our best to scrape up some info that will hopefully help diagnose
Oct 27 12:32:59 lnx1 mysqld[4538]: the problem, but since we have already crashed, something is definitely wrong
Oct 27 12:32:59 lnx1 mysqld[4538]: and this may fail.
Oct 27 12:32:59 lnx1 mysqld[4538]:
Oct 27 12:32:59 lnx1 mysqld[4538]: key_buffer_size=0
Oct 27 12:32:59 lnx1 mysqld[4538]: read_buffer_size=131072
Oct 27 12:32:59 lnx1 mysqld[4538]: max_used_connections=0
Oct 27 12:32:59 lnx1 mysqld[4538]: max_connections=100
Oct 27 12:32:59 lnx1 mysqld[4538]: threads_connected=0
Oct 27 12:32:59 lnx1 mysqld[4538]: It is possible that mysqld could use up to
Oct 27 12:32:59 lnx1 mysqld[4538]: key_buffer_size + (read_buffer_size + sort_buffer_size)*max_connections = 217599 K
Oct 27 12:32:59 lnx1 mysqld[4538]: bytes of memory
Oct 27 12:32:59 lnx1 mysqld[4538]: Hope that's ok; if not, decrease some variables in the equation.
Oct 27 12:32:59 lnx1 mysqld[4538]:
Oct 27 12:32:59 lnx1 mysqld_safe[4544]: ended
Oct 27 12:33:14 lnx1 /etc/init.d/mysql[4681]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Oct 27 12:33:14 lnx1 /etc/init.d/mysql[4681]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Oct 27 12:33:14 lnx1 /etc/init.d/mysql[4681]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Oct 27 12:33:14 lnx1 /etc/init.d/mysql[4681]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Oct 27 12:33:14 lnx1 /etc/init.d/mysql[4681]:


```

---

### Post by eldaria on 2006-10-27
Are you also running the 64bit packages?
This could be the reason, perhaps the 64bit packages are corrupt?

---

### Post by joostvdl on 2006-10-27
Also reported as bug #66702

[https://launchpad.net/distros/ubuntu/+source/mysql-dfsg-5.0/+bug/66702](https://launchpad.net/distros/ubuntu/+source/mysql-dfsg-5.0/+bug/66702)

---

### Post by eldaria on 2006-10-27
Ok that feels better. :-)

So now I know it is not my machine that is messed up. :-)

---

### Post by joostvdl on 2006-10-27
Only so if the bug is also is picked up by the developers ;-) Until then we have a problem.

I installed the old 5.0.22 version of MySQL as described above and this is a good temp solution.

---

### Post by martinoc on 2006-10-27
first 

mysqldump --all-databases -p > ~/backup.mysql

then 

apt-get --purge remove <all mysql packages here>

so we're removing mysql for the moment until we get the package manager fixed

then do 

apt-get -f install

if that works then finish with a reboot and 

apt-get dist-upgrade

---

### Post by martinoc on 2006-10-27
> **joostvdl said:**
> Only so if the bug is also is picked up by the developers ;-) Until then we have a problem.

I installed the old 5.0.22 version of MySQL as described above and this is a good temp solution.

The problem is that eldaria needs to get the package manager into a  consistent state as the upgrade is not finished.

---

### Post by codelad on 2006-10-27
> **eldaria said:**
> Are you also running the 64bit packages?
This could be the reason, perhaps the 64bit packages are corrupt?

I'm on amd64 as well, if that helps.

VJ

---

### Post by eldaria on 2006-10-27
Actually doing the apt-get -f install after sql is corrupted, will give me that there is nothing more to install.
After that if I do a apt-get dist-upgrade it will just tell me the problem with the SQL server, since it can't start it.

If I do it with SQL server uninstalled, it will tell me there is nothing more to upgrade.

Installing SQL server again leaves me with an unusable SQL server.

Since more people seems to have this problem with the 64 bit version,  i'm inclined to believe that it is related to that bug, will run with the old version for now, and keep an eye on the bug tracker.

Thanks to martinoc, for the advice that got the rest of the system working.

Everything is working now, but with old version of sql server.

---

### Post by martinoc on 2006-10-27
There is something you can do to keep your package manager happy with the older version if mysql until the bug is repaired.

It involves mixed versioning

first 

uninstall mysql 
then

```
cp /etc/apt/sources.list /etc/apt/sources.list.back
```


add the following to the end of sources.list

```

deb http://ie.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ dapper main restricted
deb http://ie.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

```

next create a file 

/etc/apt/preferences

with this 
```

Package: mysql-common
Pin: release a=dapper
Pin-Priority: 999

Package: mysql-server
Pin: release a=dapper
Pin-Priority: 999

```
repeat with any other needed packages

then

apt-get update
apt-get -t dapper install mysql
apt-get -f install
apt-get dist-upgrade

this should keep your old mysql and new everything else

---

