---
title: "Installing Apache, MySQL and PHP in Desktop?"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by jrhnewark on 2007-05-14
Hi,

I've setup an old machine as a server using Ubuntu Desktop as I'd also like to use things like multimedia output out of it, hence why I didn't use the Server version.

Is there anything like LAMP for Ubuntu Desktop that'll install everything for a web server for me automatically? I can't even find Apache in "add programs".

Thanks!

---

### Post by flat4 on 2007-05-14
I also trying to do the same thing, What I need to know is the command to also download the dependencies each program needs to operate properly

thanks

---

### Post by Rippey on 2007-05-14
system > administration > synaptic package manager
gl :-)

---

### Post by flat4 on 2007-05-14
thanks, got it.

---

### Post by jrhnewark on 2007-05-14
Cheers. :)

---

### Post by roshash on 2007-05-17
i wanna do the same...
after going to synaptic manager, how did you install apache, mysql and php.......
any help is appreciated......:confused:

---

### Post by mlind on 2007-05-17
To install php 5, apache 2.2 and mysql 5 (server)
```

sudo aptitude install php5 apache2 mysql-server

```

---

### Post by flat4 on 2007-05-17
for me I looked thru synaptic and found all of the modules and marked them for installation and it did the rest by it self.

---

### Post by jingo811 on 2007-05-21
mlind or anybody else out there how do I start and stop Apache+MySQL I'm getting some bad error it seems?
I've been learning this stuff the WAMP way so far and was forced to use XAMPP because of lack of time.  Now I'm dissapointed at the bad control and slow support over at XAMPP.

**How do I start and stop Apache and MySQL?**
```

mike@sanka:~$ **sudo /usr/sbin/apache2ctl start**
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
httpd (pid 8409) already running
mike@sanka:~$ **sudo /usr/sbin/apache2ctl stop**
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
mike@sanka:~$ **sudo /usr/sbin/apache2ctl start**
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
mike@sanka:~$
```

**Second analysis:**
Never mind ppl I'm being too quick again.  "Speaking before Thinking"
I'll go through this tutorial first before asking next time:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by roshash on 2007-05-25
> **mlind said:**
> To install php 5, apache 2.2 and mysql 5 (server)
```

sudo aptitude install php5 apache2 mysql-server

```

thank you very much, the install worked..............:D

---

