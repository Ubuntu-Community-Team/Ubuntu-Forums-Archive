---
title: "Problem with Apache2"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by ierpe on 2008-09-10
Hey, I dont know if I'm in the right place for this post... please move me if i am not! :)


So I installed Apache2+php+mysql and I needed to install tomcat as well. A problem occured the first time i tried to install tomcat. Now i installed it and it seems to be fine, but Apache2 is not running properly anymore..

I get the following error:
```

root@ubuntu:~# /etc/init.d/apache2 restart
 * Restarting web server apache2 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

```

Please help me!

---

### Post by vietseo on 2008-09-10
So [apache]("http://www.vietseo.net") is listening on port 80 of all IP addresses. This is as it should be.
In this [topic]("http://ubuntuforums.org/showthread.php?t=715940")

---

### Post by manishtech on 2008-09-10
Just give us the output of this command from the Terminal

```
ps -A | grep -i apache
```

---

### Post by ierpe on 2008-09-11
> 
pierre@ubuntu:~$ ps -A | grep -i apache
 6046 ?        00:00:00 apache2
 6185 ?        00:00:00 apache2
 6186 ?        00:00:00 apache2
 6187 ?        00:00:00 apache2
 6188 ?        00:00:00 apache2
 6189 ?        00:00:00 apache2



Its working again now after a tomcat reinstall and reboot... but why is there 6 apache processes?
And I don't really like having a problem solved by itself... :p

---

