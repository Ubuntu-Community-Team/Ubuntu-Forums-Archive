---
title: "MySQL Upstart Problems"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by cdnjay on 2010-05-11
Hi,

My MySQL server is no longer starting properly at startup and when I try to start it manually I get the following error message:

> jason@ubuntu-server:~$ start mysql
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.4" (uid=1000 pid=1854 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

I guess the scripts method has been deprecated or something as the system tells me I now have to use Upstart to start the service.

Help!

Jason

---

### Post by cdnjay on 2010-05-11
I just finished my upgrade to 10.04 so I'm guessing this was a problem with the final stages of the upgrade install.  It was an upgrade from 9.10.

---

### Post by santium on 2010-07-07
Bit old, but I have the same problem. Running 10.10

---

### Post by memet on 2010-07-19
From what I can tell you can't use the start/service commands as a mortal user so you have to do:
```
sudo service mysql start
```

---

### Post by tv3636 on 2010-07-21
> **memet said:**
> From what I can tell you can't use the start/service commands as a mortal user so you have to do:
```
sudo service mysql start
```

I'm having this problem and when I use this command ubuntu freezes (the cursor goes to the next line as if something is happening, and then I wait for 10 minutes and nothing happens)

If I try to start it with 
```
sudo mysql start
```

I get ERROR 2002: Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2)

I've been searching around and nothing I've found has been able to fix this.

---

### Post by samwilsonau on 2010-08-10
> **tv3636 said:**
> I'm having this problem and when I use this command ubuntu freezes (the cursor goes to the next line as if something is happening, and then I wait for 10 minutes and nothing happens)

Has anyone figured out what's going on with this?  I've got exactly this problem.

Thanks.

---

### Post by tv3636 on 2010-08-10
> **samwilsonau said:**
> Has anyone figured out what's going on with this?  I've got exactly this problem.

Thanks.

My problem was caused by changing the bind address in my.cnf.  I was trying to get Dreamweaver to connect to my mysql database (which I realize now is totally unnecessary and still don't know how to set up correctly) so I changed the bind-address to my laptop's IP address.  This change had everything working perfectly, so I thought I was all set.  The next day I turned everything on and mysql couldn't start because of the bind-address which was causing the socket error.  After changing it back to 127.0.0.1 (0.0.0.0 works as well) and restarting mysql started correctly when ubuntu started up and I am now always able to use it with mysql -u root - p.  Hope that helps solve your problem, but it seems like this error has a number of solutions/causes so it might not be the same case with your issue.

---

### Post by samwilsonau on 2010-08-10
Hooray!

Thanks for the reply, I did what you suggest (changed the bind-address from the machine's IP to 0.0.0.0) and after a reboot all is well!

Thank you. :-)

---

