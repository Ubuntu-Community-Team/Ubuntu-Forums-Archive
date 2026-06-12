---
title: "Why is oracle &amp; PHP not working with apache"
date: 2014-07-17
forum: Installation &amp; Upgrades
---

### Post by mysexybluefeet on 2014-07-17
Hey Guys,

I'm a bit stuck on my troubleshooting. I've installed oracle and php and apache using [http://gunbladeiv.blogspot.com.au/2011/11/ubuntu-apache-php-oracle-with-oci8.html](http://gunbladeiv.blogspot.com.au/2011/11/ubuntu-apache-php-oracle-with-oci8.html)  and I can get php and oracle working correctly but when I try to run it via apache it doesn't connect to the database.  I have a script doing the f
$conn = oci_connect('user','passsword','host');
if (!$conn) {
	echo "conn not established";
	}
if ($conn) {
        echo "conn established";
        }

and if I run it via php, the connection is established. But when I visit it via localhost/script.php, I get connection is not established. Any ideas? I've restarted apache after every change. I have run php_info with the following:

php_info()
oci8

OCI8 Support => enabled
OCI8 DTrace Support => disabled
OCI8 Version => 2.0.8
Revision => $Id: f04114d4d67cff


I feel it could be the environment that I've set for ORACLE_HOME  - what file/files/folder should I specifically be pointing to (as in where i installed the skd and basic oracle packages, in its /lib etc)

I have noticed when I restarted oracle i get this:

Shutting down Oracle Database 11g Express Edition instance.
Stopping Oracle Net Listener.

Starting Oracle Net Listener.
Starting Oracle Database 11g Express Edition instance.
Failed to start Oracle Net Listener using /u01/app/oracle/product/11.2.0/xe/bin/tnslsnr and Oracle Express Database using /u01/app/oracle/product/11.2.0/xe/bin/sqlplus.

I'm a bit stuck on where to go from here. Any help is greatly appreciated.

---

### Post by SeijiSensei on 2014-07-18
Are you connecting to localhost in the script?  If you don't specify a host, does it connect via a socket?  

Any helpful log file entries?  PHP errors are logged in /var/log/apache2/error.log. I don't know where the Oracle instance logs.

---

### Post by mysexybluefeet on 2014-07-20
I am not connecting to local host- but testing the oci-connect function in php alone, I can connect. I can also connect via using sqldeveloper. If you mean, am I accessing the script using localhost in the url, then yes

Oh thank you, /var/log/apache2/error.log had 

PHP Warning:  Module 'oci8' already loaded in Unknown on line 0
[Sun Jul 20 07:39:41.732159 2014] [mpm_prefork:notice] [pid 12055] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.3 configured -- resuming normal operations
[Sun Jul 20 07:39:41.732188 2014] [core:notice] [pid 12055] AH00094: Command line: '/usr/sbin/apache2'
[Mon Jul 21 09:23:37.493616 2014] [mpm_prefork:notice] [pid 12055] AH00169: caught SIGTERM, shutting down
PHP Warning:  Module 'oci8' already loaded in Unknown on line 0
[Mon Jul 21 09:24:59.382984 2014] [mpm_prefork:notice] [pid 1546] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.3 configured -- resuming normal operations
[Mon Jul 21 09:24:59.383090 2014] [core:notice] [pid 1546] AH00094: Command line: '/usr/sbin/apache2'

I had extension=/usr/lib/php5/20121212/oci8.so in both  /etc/php5/apache2/php.ini  and  gedit /etc/php5/cli/php.ini but I noticed if I took this line out of /etc/php5/apache2/php.ini  , that the "Module 'oci8' already loaded" is removed. 
However I can't fix the "ORA-12154: TNS:could not resolve the connect identifier specified in "

After some googling, I ran through the perms for my tnsnames.ora file and that it was in $TNS_ADMIN and its perms were -rwxr-xr-x 1 oracle dba . Its being read by php but not apache, so I'm a bit stuck again. Any ideas?

Thank you for your help so far :)

---

### Post by mysexybluefeet on 2014-07-20
Note to others, I managed to get it working from this point, using the extended version of (DESCRIPTION =(ADDRESS = (PROTOCOL = TCP)(Host = whatever your host is)(Port = 1526))(CONNECT_DATA =(SERVER = DEDICATED)(SERVICE_NAME = hostname)))

However if you have any ideas or explanations, I would still like to hear them so I could learn.

Thanks,
Manda

---

