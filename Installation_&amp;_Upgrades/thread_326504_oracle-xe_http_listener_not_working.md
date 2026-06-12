---
title: "oracle-xe http listener not working"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by horrendo on 2006-12-27
I have successfully (?) installed oracle-xe.  The database starts and is accessible from SQL*Plus :

steve@au-stb-mobile:/etc/init.d$ sqlplus / as sysdba

SQL*Plus: Release 10.2.0.1.0 - Production on Thu Dec 28 10:35:13 2006

Copyright (c) 1982, 2005, Oracle.  All rights reserved.


Connected to:
Oracle Database 10g Express Edition Release 10.2.0.1.0 - Production

If I try to connect via apex firefox tells me "Firefox can't establish a connection to the server at localhost:8080".  I could swear it was working at some point, but can't guarantee it.

Not sure if this is indicative of a problem but I also get this :

root@au-stb-mobile:/etc# telnet localhost 8080
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

I would greatly appreciate any clues to solving this.

---

### Post by troach on 2006-12-28
> **horrendo said:**
> I have successfully (?) installed oracle-xe.  The database starts and is accessible from SQL*Plus :

steve@au-stb-mobile:/etc/init.d$ sqlplus / as sysdba

SQL*Plus: Release 10.2.0.1.0 - Production on Thu Dec 28 10:35:13 2006

Copyright (c) 1982, 2005, Oracle.  All rights reserved.


Connected to:
Oracle Database 10g Express Edition Release 10.2.0.1.0 - Production

If I try to connect via apex firefox tells me "Firefox can't establish a connection to the server at localhost:8080".  I could swear it was working at some point, but can't guarantee it.

Not sure if this is indicative of a problem but I also get this :

root@au-stb-mobile:/etc# telnet localhost 8080
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

I would greatly appreciate any clues to solving this.

Login as the Oracle user and issue this command:  lsnrctl status

Post the results here.

Did you do this command also prior to setting it up?

/etc/init.d/oracle-xe configure

??

It will walk you through configuring it. Another thing to do is to ceck your firewall settings. Is port 8080 being blocked? Is it being used by something else?

Try changing the port with this command to something else.

Connect as sys dba through sqlplus.

SQL> call dbms_xdb.setHttpPort(8080); "Or whatever port you want it to use"
Call completed.
SQL> alter system register; "Reregisters the DB and all services with the listener.
System altered.

Now issue lsnrctl status again and see if it is listening on that port?

---

