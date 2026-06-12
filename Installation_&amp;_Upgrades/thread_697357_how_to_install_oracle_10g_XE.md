---
title: "how to install oracle 10g XE"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by sevensky on 2008-02-15
is there anybody can help me to install oracle 10g express edition..

i use ubuntu gutsy gibbon..and  i don't know how to install it..
please tell me the depedency before install oracle..
i download oracle-xe_10.2.0.1-1.0_i386.deb from oracle.com..
sorry for my bad english..

---

### Post by Beefeater on 2008-02-15
```
sudo dpkg -i oracle-xe_10.2.0.1-1.0_i386.deb
```

---

### Post by Waappu on 2008-02-19
[http://www.debian-administration.org/articles/430](http://www.debian-administration.org/articles/430)

---

### Post by sevensky on 2008-02-22
i've done installing oracle 10g express edition

after dpkg -i ....

/etc/init.d/oracle[tab] configure

enter..
enter..

finish..

ooo...so that easy...
thanks for help

---

### Post by DreamerHxC on 2008-02-29
It isn't working for me; I get this error:
```

Listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC_FOR_XE)))
Error listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=noloman)(PORT=1521)))
TNS-12545: Connect failed because target host or object does not exist
 TNS-12560: TNS:protocol adapter error
  TNS-00515: Connect failed because target host or object does not exist
   Linux Error: 110: Connection timed out
No longer listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC_FOR_XE)))

```

I have been looking in [http://ora-12545.ora-code.com/](http://ora-12545.ora-code.com/) and [http://www.davidpashley.com/articles/oracle-install.html](http://www.davidpashley.com/articles/oracle-install.html) but I still haven't solved the problem, because I'm sure what to do :confused:

---

### Post by Beefeater on 2008-02-29
> **DreamerHxC said:**
> It isn't working for me; I get this error:
```

Listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC_FOR_XE)))
Error listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=noloman)(PORT=1521)))
TNS-12545: Connect failed because target host or object does not exist
 TNS-12560: TNS:protocol adapter error
  TNS-00515: Connect failed because target host or object does not exist
   Linux Error: 110: Connection timed out
No longer listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC_FOR_XE)))

```

I have been looking in [http://ora-12545.ora-code.com/](http://ora-12545.ora-code.com/) and [http://www.davidpashley.com/articles/oracle-install.html](http://www.davidpashley.com/articles/oracle-install.html) but I still haven't solved the problem, because I'm sure what to do :confused:

When are you getting this? During install?
What does your /etc/default/oracle-xe look like?

It's not possible for some to start oracle with 
```
/etc/init.d/oracle-xe start
```

Doing
```
/etc/init.d/oracle-xe restart
```
usually works though.

---

### Post by DreamerHxC on 2008-02-29
This is my /etc/deault/oracle-xe:
```

# ORACLE_DBENABLED:'true' means to load the Database at system boot.
ORACLE_DBENABLED=false

# LISTENER_PORT: Database listener
LISTENER_PORT=1521

# HTTP_PORT : HTTP port for Oracle Application Express
HTTP_PORT=8080

# Configuration : Check whether configure has been done or not
CONFIGURE_RUN=true

```

By the way, I can start oracle with /etc/init.d/oracle-xe start and restart works too, but I'm getting that same error when I try enter in [http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex)

---

### Post by Beefeater on 2008-02-29
Are you running apache?

I had the same problem (or similar) a few weeks ago. I had to do a new installation of Ubuntu anyway so when that was finished I installed Oracle before Apache and everything  worked. Might be something, might be nothing.

---

### Post by DreamerHxC on 2008-02-29
No, I'm not running Apache

---

### Post by Beefeater on 2008-02-29
Maybe there is a problem with your tnsnames.ora

Let us have a look.

It's located in
```
/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/admin
```
on my installation.

---

### Post by DreamerHxC on 2008-02-29
This is my tnsnames.ora:
```

<alias>= [ (DESCRIPTION_LIST =  # Optional depending on whether u have 
				# one or more descriptions
				# If there is just one description, unnecessary ]
	  (DESCRIPTION=
	    [ (SDU=2048) ]	# Optional, defaults to 2048
				# Can take values between 512 and 32K
	    [ (ADDRESS_LIST=    # Optional depending on whether u have
				# one or more addresses
				# If there is just one address, unnecessary ]
	      (ADDRESS=
		[ (COMMUNITY=<community_name>) ] 
		(PROTOCOL=tcp)
		(HOST=127.0.0.1)
		(PORT=<portnumber (1521 is a standard port used)>)
	      )
	      [ (ADDRESS=
		  (PROTOCOL=ipc)
		  (KEY=<ipckey (PNPKEY is a standard key used)>)	
		)
	      ]
	      [ (ADDRESS=
		  [ (COMMUNITY=<community_name>) ]
		  (PROTOCOL=decnet)
		  (NODE=<nodename>)
		  (OBJECT=<objectname>)
		)
	      ]
              ... # More addresses
	    [ ) ] # Optional depending on whether ADDRESS_LIST is used or not 
	    [ (CONNECT_DATA=
		(SID=<oracle_sid>)
		[ (GLOBAL_NAME=<global_database_name>) ]
	      )
	    ]
	    [ (SOURCE_ROUTE=yes) ]  
	  )
	  (DESCRIPTION=     
	    [ (SDU=2048) ]	# Optional, defaults to 2048
				# Can take values between 512 and 32K
	    [ (ADDRESS_LIST= ]	# Optional depending on whether u have more
				# than one address or not
				# If there is just one address, unnecessary
	      (ADDRESS
		[ (COMMUNITY=<community_name>) ]
		(PROTOCOL=tcp)
		(HOST=127.0.0.1)
		(PORT=<portnumber (1521 is a standard port used)>)
	      )
	      [ (ADDRESS=
		  (PROTOCOL=ipc)
		  (KEY=<ipckey (PNPKEY is a standard key used)>)
	         )
	      ]
	      ... 		# More addresses
	    [ ) ] 		# Optional depending on whether ADDRESS_LIST  
				# is being used
	    [ (CONNECT_DATA=
		(SID=<oracle_sid>)
		[ (GLOBAL_NAME=<global_database_name>) ]
	      )
	    ]
	    [ (SOURCE_ROUTE=yes) ]
	  )
	  [ (CONNECT_DATA=
	      (SID=<oracle_sid>)
	      [ (GLOBAL_NAME=<global_database_name>) ]
	    )
	  ]
	  ...   # More descriptions 
	[ ) ]	# Optional depending on whether DESCRIPTION_LIST is used or not

```

I just changed localhost for 127.0.0.1

---

### Post by Beefeater on 2008-02-29
that's a sample file. You should have another one located one level down.

---

### Post by DreamerHxC on 2008-02-29
# tnsnames.ora Network Configuration File:

XE =
  (DESCRIPTION =
    (ADDRESS = (PROTOCOL = TCP)(HOST = localhost)(PORT = 1521))
    (CONNECT_DATA =
      (SERVER = DEDICATED)
      (SERVICE_NAME = XE)
    )
  )

EXTPROC_CONNECTION_DATA =
  (DESCRIPTION =
    (ADDRESS_LIST =
      (ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC_FOR_XE))
    )
    (CONNECT_DATA =
      (SID = PLSExtProc)
      (PRESENTATION = RO)
    )
  )

---

### Post by Beefeater on 2008-02-29
This was a weird one.
Hmm..what does your /etc/hosts look like?

---

### Post by DreamerHxC on 2008-02-29
```

127.0.0.1 localhost
127.0.1.1 noloman.WORKGROUP

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by Beefeater on 2008-02-29
> **DreamerHxC said:**
> ```

127.0.0.1 localhost
127.0.1.1 noloman.WORKGROUP

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

This should do it

```
127.0.1.1 noloman noloman.WORKGROUP
```

And restart Oracle.

If not I'm gonna eat my hair and throw my beer out the window (dont wanna do that)

---

### Post by DreamerHxC on 2008-02-29
I did it so my /etc/hosts looks now like:
```

127.0.0.1 localhost
127.0.1.1 noloman noloman.WORKGROUP

```
And I tried [http://127.0.1.1:8080/apex](http://127.0.1.1:8080/apex), [http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex) and [http://localhost:8080/apex](http://localhost:8080/apex)

In this moment I just can think of reinstalling and reconfiguring oracle..., anyway I'm sure the solution of the problem will be a stupidity

---

### Post by Beefeater on 2008-02-29
What does
```
/etc/init.d/oracle-xe status
```
give you?

Yes it is stupid. Because it shouldn't work without noloman in hosts, but now that you have it ..

---

### Post by DreamerHxC on 2008-02-29
```

LSNRCTL for Linux: Version 10.2.0.1.0 - Production on 29-FEB-2008 15:58:11

Copyright (c) 1991, 2005, Oracle.  All rights reserved.

Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC_FOR_XE)))
STATUS of the LISTENER
------------------------
Alias                     LISTENER
Version                   TNSLSNR for Linux: Version 10.2.0.1.0 - Production
Start Date                29-FEB-2008 15:33:41
Uptime                    0 days 0 hr. 24 min. 29 sec
Trace Level               off
Security                  ON: Local OS Authentication
SNMP                      OFF
Default Service           XE
Listener Parameter File   /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/admin/listener.ora
Listener Log File         /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/log/listener.log
Listening Endpoints Summary...
  (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC_FOR_XE)))
  (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=noloman)(PORT=1521)))
Services Summary...
Service "PLSExtProc" has 1 instance(s).
  Instance "PLSExtProc", status UNKNOWN, has 1 handler(s) for this service...
Service "XE" has 1 instance(s).
  Instance "XE", status BLOCKED, has 1 handler(s) for this service...
Service "XE_XPT" has 1 instance(s).
  Instance "XE", status BLOCKED, has 1 handler(s) for this service...
The command completed successfully

```

---

### Post by Beefeater on 2008-02-29
Everything looks good except one thing. Nothing is running on 8080
You should have this as well

```
(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=127.0.0.1)(PORT=8080))(Presentation=HTTP)(Session=RAW))
```

Let's have a look in

```
/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/log/listener.log
```

---

### Post by DreamerHxC on 2008-02-29
Wow, this is a large log. Here it goes:
```

Listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC_FOR_XE)))
Error listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=noloman)(PORT=1521)))
TNS-12545: Connect failed because target host or object does not exist
 TNS-12560: TNS:protocol adapter error
  TNS-00515: Connect failed because target host or object does not exist
   Linux Error: 110: Connection timed out
No longer listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC_FOR_XE)))

TNSLSNR for Linux: Version 10.2.0.1.0 - Production on 29-FEB-2008 11:57:06

Copyright (c) 1991, 2005, Oracle.  All rights reserved.

System parameter file is /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/admin/listener.ora
Log messages written to /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/log/listener.log
Trace information written to /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/trace/listener.trc
Trace level is currently 0

Started with pid=31494
Listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC_FOR_XE)))
Error listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=noloman)(PORT=1521)))
TNS-12545: Connect failed because target host or object does not exist
 TNS-12560: TNS:protocol adapter error
  TNS-00515: Connect failed because target host or object does not exist
   Linux Error: 110: Connection timed out
No longer listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC_FOR_XE)))

TNSLSNR for Linux: Version 10.2.0.1.0 - Production on 29-FEB-2008 15:08:21

Copyright (c) 1991, 2005, Oracle.  All rights reserved.

System parameter file is /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/admin/listener.ora
Log messages written to /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/log/listener.log
Trace information written to /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/trace/listener.trc
Trace level is currently 0

Started with pid=31627
Listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC_FOR_XE)))
Error listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=noloman)(PORT=1521)))
TNS-12545: Connect failed because target host or object does not exist
 TNS-12560: TNS:protocol adapter error
  TNS-00515: Connect failed because target host or object does not exist
   Linux Error: 110: Connection timed out
No longer listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC_FOR_XE)))

TNSLSNR for Linux: Version 10.2.0.1.0 - Production on 29-FEB-2008 15:33:41

Copyright (c) 1991, 2005, Oracle.  All rights reserved.

System parameter file is /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/admin/listener.ora
Log messages written to /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/log/listener.log
Trace information written to /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/trace/listener.trc
Trace level is currently 0

Started with pid=3508
Listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC_FOR_XE)))
Listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=noloman)(PORT=1521)))
Listener completed notification to CRS on start

TIMESTAMP * CONNECT DATA [* PROTOCOL INFO] * EVENT [* SID] * RETURN CODE
29-FEB-2008 15:33:42 * (CONNECT_DATA=(CID=(PROGRAM=)(HOST=noloman)(USER=oracle))(COMMAND=status)(ARGUMENTS=64)(SERVICE=LISTENER)(VERSION=169869568)) * status * 0
29-FEB-2008 15:33:42 * service_register * XE * 0
29-FEB-2008 15:33:43 * service_update * XE * 0
29-FEB-2008 15:34:08 * ping * 0
29-FEB-2008 15:34:10 * service_update * XE * 0
29-FEB-2008 15:36:46 * 12502
TNS-12502: TNS:listener received no CONNECT_DATA from client
29-FEB-2008 15:36:47 * 12502
TNS-12502: TNS:listener received no CONNECT_DATA from client
29-FEB-2008 15:36:51 * 12502
TNS-12502: TNS:listener received no CONNECT_DATA from client
29-FEB-2008 15:36:59 * 12502
TNS-12502: TNS:listener received no CONNECT_DATA from client
29-FEB-2008 15:36:59 * 12502
TNS-12502: TNS:listener received no CONNECT_DATA from client
29-FEB-2008 15:37:01 * 12502
TNS-12502: TNS:listener received no CONNECT_DATA from client
29-FEB-2008 15:58:11 * (CONNECT_DATA=(CID=(PROGRAM=)(HOST=noloman)(USER=oracle))(COMMAND=status)(ARGUMENTS=64)(SERVICE=LISTENER)(VERSION=169869568)) * status * 0

```

---

### Post by Beefeater on 2008-02-29
OK let's see.. we have solved the hostname-issue.

Can you connect to SQL Plus as user 'system' ?

If not do this first.

```
export ORACLE_BASE=/usr/lib/oracle/xe/app/oracle
export ORACLE_HOME=$ORACLE_BASE/product/10.2.0/server
export PATH=$PATH:$ORACLE_HOME/bin
export ORACLE_HOME_LISTNER=$ORACLE_HOME
export ORACLE_SID=XE
```

Then

```
sqlplus
```
```

call dbms_xdb.setHttpPort(8080)
/
alter system register
/
quit
```

```
lsnrctl status
```

What is your output?

Hopefully you will see something like ..

(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=noloman)(PORT=8080))(Presentation=HTTP)(Session=RAW))

---

### Post by DreamerHxC on 2008-02-29
When I try to log as system, I enter the password but I get:
```

ERROR:
ORA-01033: ORACLE initialization or shutdown in progress

```

I don't know if it's because it might be a wrong password or because it isn't still working.
Anyway I tried /etc/init.d/oracle-xe restart but I'm getting the same error.

---

### Post by Beefeater on 2008-02-29
Reboot your computer :-)

---

### Post by DreamerHxC on 2008-02-29
It isn't still working.
Take a look at this:
```

noloman@noloman:~$ sudo /etc/init.d/oracle-xe status

LSNRCTL for Linux: Version 10.2.0.1.0 - Production on 29-FEB-2008 17:57:24

Copyright (c) 1991, 2005, Oracle.  All rights reserved.

Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC_FOR_XE)))
TNS-12541: TNS:no listener
 TNS-12560: TNS:protocol adapter error
  TNS-00511: No listener
   Linux Error: 111: Connection refused
Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=noloman)(PORT=1521)))
TNS-12541: TNS:no listener
 TNS-12560: TNS:protocol adapter error
  TNS-00511: No listener
   Linux Error: 111: Connection refused

```

---

### Post by Beefeater on 2008-02-29
:-)

Post your listener.ora

---

### Post by DreamerHxC on 2008-02-29
```

# listener.ora Network Configuration File:

SID_LIST_LISTENER =
  (SID_LIST =
    (SID_DESC =
      (SID_NAME = PLSExtProc)
      (ORACLE_HOME = /usr/lib/oracle/xe/app/oracle/product/10.2.0/server)
      (PROGRAM = extproc)
    )
  )

LISTENER =
  (DESCRIPTION_LIST =
    (DESCRIPTION =
      (ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC_FOR_XE))
      (ADDRESS = (PROTOCOL = TCP)(HOST = noloman)(PORT = 1521))
    )
  )

DEFAULT_SERVICE_LISTENER = (XE)

```

---

### Post by Beefeater on 2008-02-29
And you can ping noloman right?

Try this [http://gentoo-wiki.com/Talk:HOWTO_Install_Oracle_10g_Express_Edition](http://gentoo-wiki.com/Talk:HOWTO_Install_Oracle_10g_Express_Edition)

---

### Post by DreamerHxC on 2008-02-29
```
noloman@noloman:~$ ping noloman
PING noloman (127.0.1.1) 56(84) bytes of data.
64 bytes from noloman (127.0.1.1): icmp_seq=1 ttl=64 time=0.039 ms
64 bytes from noloman (127.0.1.1): icmp_seq=2 ttl=64 time=0.042 ms
64 bytes from noloman (127.0.1.1): icmp_seq=3 ttl=64 time=0.019 ms
64 bytes from noloman (127.0.1.1): icmp_seq=4 ttl=64 time=0.037 ms
```

Yes, I can

EDIT: I can do this:
```

SQL*Plus: Release 10.2.0.1.0 - Production on Fri Feb 29 19:12:56 2008

Copyright (c) 1982, 2005, Oracle.  All rights reserved.

SQL> connect / as sysdba
Connected.
SQL> connect

```
But I still can't enter through web to the server

---

### Post by Beefeater on 2008-02-29
OK I managed to reproduce your problem (finally).```

su - oracle

export ORACLE_BASE=/usr/lib/oracle/xe/app/oracle
export ORACLE_HOME=$ORACLE_BASE/product/10.2.0/server
export PATH=$PATH:$ORACLE_HOME/bin
export ORACLE_HOME_LISTNER=$ORACLE_HOME
export ORACLE_SID=XE

lsnrctl start

sqlplus

call dbms_xdb.setHttpPort(8080)
/
alter system register
/
quit

lsnrctl status

exit

sudo /etc/init.d/oracle-xe restart

sudo /etc/init.d/oracle-xe status
```

---

### Post by DreamerHxC on 2008-02-29
This is what I get when I do lsnrctl start:
```

noloman@noloman:~$ lsnrctl start

LSNRCTL for Linux: Version 10.2.0.1.0 - Production on 29-FEB-2008 19:20:59

Copyright (c) 1991, 2005, Oracle.  All rights reserved.

Starting /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/tnslsnr: please wait...

TNSLSNR for Linux: Version 10.2.0.1.0 - Production
NL-00280: error creating log stream /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/log/listener.log
 NL-00278: cannot open log file
  SNL-00016: snlfohd: error opening file
   Linux Error: 13: Permission denied

Listener failed to start. See the error message(s) above...

```

---

### Post by Beefeater on 2008-02-29
> **DreamerHxC said:**
> This is what I get when I do lsnrctl start:
```

noloman@noloman:~$ lsnrctl start

LSNRCTL for Linux: Version 10.2.0.1.0 - Production on 29-FEB-2008 19:20:59

Copyright (c) 1991, 2005, Oracle.  All rights reserved.

Starting /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/tnslsnr: please wait...

TNSLSNR for Linux: Version 10.2.0.1.0 - Production
NL-00280: error creating log stream /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/log/listener.log
 NL-00278: cannot open log file
  SNL-00016: snlfohd: error opening file
   Linux Error: 13: Permission denied

Listener failed to start. See the error message(s) above...

```

You have to login as user oracle as mentioned

---

### Post by DreamerHxC on 2008-02-29
But if I do a su - oracle I get an authentication error because I don't know what the password is

---

### Post by Beefeater on 2008-02-29
System - Administration - Users and groups

change it :-)

---

### Post by DreamerHxC on 2008-02-29
```

Enter user-name: connect / as sysdba
Enter password: 

Connected to:
Oracle Database 10g Express Edition Release 10.2.0.1.0 - Production

SQL> call dbms_xdb.setHttpPort(8080)
/
alter system register
/
quit  2  call dbms_xdb.setHttpPort(8080)
*
ERROR at line 1:
ORA-01109: database not open


SQL>   2  
System altered.

```

I continued to do the rest, but web isn't still working.

---

### Post by Beefeater on 2008-02-29
> **DreamerHxC said:**
> ```

Enter user-name: connect / as sysdba
Enter password: 

Connected to:
Oracle Database 10g Express Edition Release 10.2.0.1.0 - Production

SQL> call dbms_xdb.setHttpPort(8080)
/
alter system register
/
quit  2  call dbms_xdb.setHttpPort(8080)
*
ERROR at line 1:
ORA-01109: database not open


SQL>   2  
System altered.

```

I continued to do the rest, but web isn't still working.

try
```
startup
```
before call dbms_xdb.setHttpPort(8080) ...

---

### Post by DreamerHxC on 2008-02-29
```

SQL> startup
ORA-01081: cannot start already-running ORACLE - shut it down first

```
This is getting a real pain...

---

### Post by Beefeater on 2008-02-29
Tell me about it ..
shutdown immediate;

---

### Post by DreamerHxC on 2008-02-29
I already did a /etc/init.d/oracle-xe stop, then as you said before, I did a startup, but I'm getting the same

---

### Post by Beefeater on 2008-02-29
No you do it in sqlplus

```
stop immediate;
startup;
call dbms_xdb.setHttpPort(8080);
alter system register;
quit

lsnrctl status
```

post the output```


exit

sudo /etc/init.d/oracle-xe restart
sudo /etc/init.d/oracle-xe status
```

---

### Post by DreamerHxC on 2008-02-29
```

SQL> shutdown
;
ORA-01507: database not mounted


ORACLE instance shut down.
SQL>   1* alter system register
SQL> startup;
ORACLE instance started.

Total System Global Area  608174080 bytes
Fixed Size                  1260316 bytes
Variable Size             167773412 bytes
Database Buffers          436207616 bytes
Redo Buffers                2932736 bytes
ORA-00205: error in identifying control file, check alert log for more info


SQL> call dbms_xdb.setHttpPort(8080);
call dbms_xdb.setHttpPort(8080)
*
ERROR at line 1:
ORA-01109: database not open


SQL> alter system register;

System altered.

SQL> quit
Disconnected from Oracle Database 10g Express Edition Release 10.2.0.1.0 - Production
oracle@noloman:~$ lsnrctl status

LSNRCTL for Linux: Version 10.2.0.1.0 - Production on 29-FEB-2008 20:10:16

Copyright (c) 1991, 2005, Oracle.  All rights reserved.

Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC_FOR_XE)))
STATUS of the LISTENER
------------------------
Alias                     LISTENER
Version                   TNSLSNR for Linux: Version 10.2.0.1.0 - Production
Start Date                29-FEB-2008 19:41:18
Uptime                    0 days 0 hr. 28 min. 58 sec
Trace Level               off
Security                  ON: Local OS Authentication
SNMP                      OFF
Default Service           XE
Listener Parameter File   /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/admin/listener.ora
Listener Log File         /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/log/listener.log
Listening Endpoints Summary...
  (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC_FOR_XE)))
  (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=noloman)(PORT=1521)))
Services Summary...
Service "PLSExtProc" has 1 instance(s).
  Instance "PLSExtProc", status UNKNOWN, has 1 handler(s) for this service...
Service "XE" has 1 instance(s).
  Instance "XE", status BLOCKED, has 1 handler(s) for this service...
Service "XE_XPT" has 1 instance(s).
  Instance "XE", status BLOCKED, has 1 handler(s) for this service...
The command completed successfully

```

when I do sudo /etc/init.d/oracle-xe restart and sudo /etc/init.d/oracle-xe status I get nothing as output (I am logged with user oracle)

---

### Post by Beefeater on 2008-02-29
post
/usr/lib/oracle/xe/app/oracle/admin/XE/bdump/alert_XE.log

---

### Post by DreamerHxC on 2008-02-29
I'll post the last log because this log is really large:
```

Starting up ORACLE RDBMS Version: 10.2.0.1.0.
System parameters with non-default values:
  sessions                 = 49
  __large_pool_size        = 0
  sga_target               = 608174080
  control_files            = /usr/lib/oracle/xe/oradata/XE/control.dbf
  __db_cache_size          = 440401920
  compatible               = 10.2.0.1.0
  db_recovery_file_dest    = /usr/lib/oracle/xe/app/oracle/flash_recovery_area
  db_recovery_file_dest_size= 10737418240
  undo_management          = AUTO
  undo_tablespace          = UNDO
  remote_login_passwordfile= EXCLUSIVE
  dispatchers              = (PROTOCOL=TCP) (SERVICE=XEXDB)
  shared_servers           = 4
  job_queue_processes      = 4
  background_dump_dest     = /usr/lib/oracle/xe/app/oracle/admin/XE/bdump
  user_dump_dest           = /usr/lib/oracle/xe/app/oracle/admin/XE/udump
  core_dump_dest           = /usr/lib/oracle/xe/app/oracle/admin/XE/cdump
  audit_file_dest          = /usr/lib/oracle/xe/app/oracle/admin/XE/adump
  db_name                  = XE
  open_cursors             = 300
  os_authent_prefix        = 
  pga_aggregate_target     = 201850880
PMON started with pid=2, OS id=16924
PSP0 started with pid=3, OS id=16926
MMAN started with pid=4, OS id=16928
DBW0 started with pid=5, OS id=16930
LGWR started with pid=6, OS id=16932
CKPT started with pid=7, OS id=16934
SMON started with pid=8, OS id=16936
RECO started with pid=9, OS id=16938
CJQ0 started with pid=10, OS id=16940
MMON started with pid=11, OS id=16942
MMNL started with pid=12, OS id=16944
Fri Feb 29 20:09:32 2008
starting up 1 dispatcher(s) for network address '(ADDRESS=(PARTIAL=YES)(PROTOCOL=TCP))'...
starting up 4 shared server(s) ...
Oracle Data Guard is not available in this edition of Oracle.
Fri Feb 29 20:09:32 2008
ALTER DATABASE   MOUNT
Fri Feb 29 20:09:32 2008
ORA-00202: control file: '/usr/lib/oracle/xe/oradata/XE/control.dbf'
ORA-27037: unable to obtain file status
Linux Error: 2: No such file or directory
Additional information: 3
Fri Feb 29 20:09:32 2008
ORA-205 signalled during: ALTER DATABASE   MOUNT...

```

---

### Post by Beefeater on 2008-02-29
Does the file
/usr/lib/oracle/xe/oradata/XE/control.dbf
exist?

---

### Post by DreamerHxC on 2008-02-29
No, it doesn't exists

---

### Post by Beefeater on 2008-02-29
Sweet! We're getting somewhere.

Remove
[http://download.oracle.com/docs/cd/B25329_01/doc/install.102/b25144/toc.htm#CIHDDHJD](http://download.oracle.com/docs/cd/B25329_01/doc/install.102/b25144/toc.htm#CIHDDHJD)

Reinstall through Synaptic so you are sure you get all dependencies.

---

### Post by DreamerHxC on 2008-02-29
Ok, I uninstalled and then reinstalled through Synaptics, and then I do:
```
noloman@noloman:~$ sudo /etc/init.d/oracle-xe configure
[sudo] password for noloman:
Oracle Database 10g Express Edition is already configured

```
 but the web interface isn't still working

---

### Post by Beefeater on 2008-02-29
Let's just focus on getting you a working installation.
Follow the steps in 7.2 in
[http://download.oracle.com/docs/cd/B25329_01/doc/install.102/b25144/toc.htm#CIHDDHJD](http://download.oracle.com/docs/cd/B25329_01/doc/install.102/b25144/toc.htm#CIHDDHJD)
and we take it from there.

---

### Post by DreamerHxC on 2008-03-01
Allright, I uninstalled following step 7.2 and then installed through Synaptics.
Now what?

---

### Post by Beefeater on 2008-03-01
Have you configured it and checked that 
/usr/lib/oracle/xe/oradata/XE/control.dbf exist?

---

### Post by DreamerHxC on 2008-03-01
It is working! :-D
But how can I do this automatically for example when I start Oracle server? For not doing it on the console everytime I start Oracle manually
```

export ORACLE_BASE=/usr/lib/oracle/xe/app/oracle
export ORACLE_HOME=$ORACLE_BASE/product/10.2.0/server
export PATH=$PATH:$ORACLE_HOME/bin
export ORACLE_HOME_LISTNER=$ORACLE_HOME
export ORACLE_SID=XE

```

Now I just have to experiment a little more with this.
I don't really know what I did to solve this, just uninstalled and reinstalled and configured, and when I opene the web, it worked!

Thank you very much :-)

---

### Post by Beefeater on 2008-03-01
Great news! :-)

You can add it to ~/.bashrc

---

### Post by olofgaga on 2008-04-02
Hi all,

I have a problem too with Oracle XE. Installation works fine. I can access the page [http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex). But I can access this page from another computer on my network, with the IP address of the machine.

Anyone has the same problem ?

Thank you !

---

### Post by Waappu on 2008-04-02
> **olofgaga said:**
> Hi all,

I have a problem too with Oracle XE. Installation works fine. I can access the page [http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex). But I can access this page from another computer on my network, with the IP address of the machine.

Anyone has the same problem ?

Thank you !

See if this help
[http://www.debian-administration.org/articles/430](http://www.debian-administration.org/articles/430)
> - By default OracleXe installation does not allow sql network connections to your XE database. To enable it, logon to web management console and enable "Remote connections": "Administration->enable "Available from local server and remote clients"-> press "Apply Changes".

---

### Post by olofgaga on 2008-04-03
Oh yes, it helps... It was that simple.

Thank you !

---

