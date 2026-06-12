---
title: "MySQL Server 5 Security Update"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by twygly on 2007-03-25
Hi, new to Ubuntu (Edgy) and it's trying to update a security release for MySQL but fails because it can't stop the existing instance.

At the command prompt I type: 
```
sudo /etc/init.d/mysql stop
```
and get:
```
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
```

Any suggestions? I've tried installing the GUI admin for MySQL and it also can't stop it. I've also tried ignoring it but the problem persists.

Thanks.

---

### Post by westli on 2007-03-25
If you have configured MySQL with a user with the proper priviledges, you can use:

mysqladmin -u[username] -p[password] shutdown

Insert the proper username and password, of course.  I found that that still didn't allow the upgrade to go without error, however,  and MySQL wasn't running.  After restarting the computer (which may have been overkill but is simple) it was upgraded and working.

But due to the error, I can't install anything else until that's fixed. 

bummer...

---

### Post by twygly on 2007-03-27
Thanks for that.

What I eventually discovered is that my permission tables where from a prior version of MySQL and I had to run an upgrade first, then do a reboot, a manual shutdown of mysqladmin and stop of mysql before the security update worked.

---

