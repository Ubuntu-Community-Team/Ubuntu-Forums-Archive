---
title: "Database Firebird: Access denied"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by waffen on 2007-11-19
I install Firebird 2.0 and Flamerobin from Synaptic, all good. But I never receipt any ask for setup the User and password for the server.

So when I try to perform (in Flamerobin) a simple Server retrieve verion I receipt:

None of the credentials of the databases could be used.
You need to supply a valid username and password.

I setup both for default (SYSDBA and masterkey) and receipt this:

```
 *** IBPP::SQLException ***
Context: Service::Connect
Message: isc_service_attach failed

SQL Message : -902
Unsuccessful execution caused by a system error that precludes
successful execution of subsequent statements

Engine Code    : 335544721
Engine Message :
Unable to complete network request to host "localhost".
Failed to establish a connection.
```

That is in my PC Desktop in my laptop (both have the same config: Ubuntu Gutsy and....) I receipt a message like:

```
 
You dont have permission in file blah blah

Access denied


```

So I change the permission for the .FDB file, but dont fix the trouble.

Thats error show me in both instalation: from Synaptic and compile from sources.

Any idea??

Thanks!

---

### Post by mariuz on 2007-12-06
please remove any firebird2.0-* packages from synaptic (Mark them for complete removal)

You will be asked to 
Delete password databse (click and check it)
Delete database from /var/lib/firebird2.0/data (click and check it)

Then click forward

Next install Firebird2.0-* packages from synaptic 
Check all minus the firebird.2.0-classic that is not needed 

And then click apply 

you will be asked to choose the Firebird Version 
then choose firebird2.0-super
password for SYSDBA
Choose an random password for you 

Then install flamerobin and create an database in /tmp/foo.fdb 
Firebird runs under firebird user and the directory where it writes must have 
perimissions for that user 

The employee.fdb archive will be under this dir
 /usr/share/doc/firebird2.0-examples/examples/empbuild/
$cd /usr/share/doc/firebird2.0-examples/examples/empbuild/
 $sudo gunzip employee.fdb.gz
 $sudo chown firebird.firebird employee.fdb
 $sudo mv employee.fdb /var/lib/firebird/2.0/data/
connect to db
$ isql-fb


SQL> connect "employee.fdb" user 'SYSDBA' password 'masterkey';



ps: you can reset the password with sudo dpkg-reconfigure firebird2.0-super

Also you can install from console [http://www.firebirdnews.org/?p=1353](http://www.firebirdnews.org/?p=1353)

---

### Post by judo_ras on 2007-12-12
I tried to make everything following instructions. BUT:
password for SYSDBA
Choose an random password for you 
1. I wasn't ask to set the SYSDBA password, but I changed the password to masterkey with
sudo dpkg-reconfigure firebird2.0-super
Then install flamerobin and create an database in /tmp/foo.fdb
Firebird runs under firebird user and the directory where it writes must have
perimissions for that user 
2. I installed flamerobin. But how should I create new database???
I click on Localhost in flamerobin and then choose 'create new database'
This is what I enter :
Display name: 'New' (but really as I understand it doesn't matter)
Database path: '/tmp/foo.fdb' (also tried /home/ras/new.fdb)
username SYSDBA
password masterkey
And that's it. FlameRobin creates nothing. Just writes this:
*** IBPP::SQLException ***
Context: Database::Create
Message: isc_dsql_execute_immediate failed

SQL Message : -902
Unsuccessful execution caused by a system error that precludes
successful execution of subsequent statements

Engine Code    : 335544721
Engine Message :
Unable to complete network request to host "gds_db".
Failed to locate host machine.
The specified name was not found in the hosts file or Domain Name Services.

What's wrong?

---

### Post by mariuz on 2007-12-19
what do you have at hostname ? 

could you put localhost

also check if the firebird server is up (ps aux | grep firebird)

check also if you have gds_db on /etc/services

 grep gds /etc/services
gds_db		3050/tcp			# InterBase server
gds_db		3050/udp

also check if the firebird port is open 
telnet localhost gds_db
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
quit
Connection closed by foreign host.

---

### Post by bat266 on 2007-12-19
i have exactly the same problem. Telnet gives a connection refused. Can anybody help me with that ?

---

### Post by yellow5464 on 2007-12-26
i had the same issue with version 1.5, and have solved it by installing the version 2.0. Hope it will help. :)

---

