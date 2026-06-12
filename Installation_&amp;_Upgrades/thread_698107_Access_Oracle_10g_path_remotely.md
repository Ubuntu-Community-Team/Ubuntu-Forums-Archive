---
title: "Access Oracle 10g path remotely ?"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by rompstar420 on 2008-02-15
I installed Oracle 10g the Express edition, to follow a book and to learn SQ.  Oracle 10g for those who don't know is accessed mostly through a web browser, works quite nicely.  Normally on the same machine that is running the server, I access the local host by this URL:

[http://192.168.1.2:8080/apex](http://192.168.1.2:8080/apex)

192.168.1.2 is the IP address of the machine running oracle

So from my wireless network 192.167.1.1 I can access it, but I can't access it from outside of the internet, meaning [http://real.ip:8080/apex](http://real.ip:8080/apex) from outside, but normally [http://real.ip](http://real.ip) works as I access my web site all the time.

my host IP address is 192.168.1.2, and then a router that is connected to the outside forwards HTTP traffic request to 192.168.1.2 from the real IP address.

The thing is that I can't put the real I.P. address of the server to access it

[http://real.ip:8080/apex](http://real.ip:8080/apex) from the outside to access Oracle.

Does anyone know what I have to do ?

---

### Post by Waappu on 2008-02-19
Hi

See this page
[http://www.debian-administration.org/articles/430](http://www.debian-administration.org/articles/430)

>  
By default OracleXe installation does not allow sql network connections to your XE database. To enable it, logon to web management console and enable "Remote connections": "Administration->enable "Available from local server and remote clients"-> press "Apply Changes". The same procedure can also be done from the commandline:
```
$ sqlplus -S system/password@//localhost/XE <<!
EXEC DBMS_XDB.SETLISTENERLOCALACCESS(FALSE); 
EXIT;
/
!
```

---

### Post by rompstar420 on 2008-02-20
I have Remote HTTP enabled, and I still can't access from an outside network, from work.

[http://IPADDRESS:8080/apex/](http://IPADDRESS:8080/apex/)

don't work, this kinda sucks, I wanted to show off Oracle 10G express to a couple people and I can't even connect to it.

---

