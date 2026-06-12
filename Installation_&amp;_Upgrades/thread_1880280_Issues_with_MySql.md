---
title: "Issues with MySql"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by ServerSwag on 2011-11-13
Well I have just started my first Ubuntu server with lamp and everything was running well at first but about 3 months later I was going in to work on my mysql databases and it would not let me in no matter what I did to resole it. So I decided to uninstall and than reinstall mysql. The uninstallation went fine but the reinstallation does not seem to work. it looks like this 
```
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-common 5.1.41-3ubuntu12.10
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libmysqlclient16 5.1.41-3ubuntu12.10
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid/main libdbd-mysql-perl 4.012-1ubuntu1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-client-core-5.1 5.1.41-3ubuntu12.10
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-client-5.1 5.1.41-3ubuntu12.10
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-server-core-5.1 5.1.41-3ubuntu12.10
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-server-5.1 5.1.41-3ubuntu12.10
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-client 5.1.41-3ubuntu12.10
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-server 5.1.41-3ubuntu12.10
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main php5-mysql 5.3.2-1ubuntu4.10
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ lucid-security/main php5-mysql 5.3.2-1ubuntu4.10
  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-common_5.1.41-3ubuntu12.10_all.deb  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/libmysqlclient16_5.1.41-3ubuntu12.10_amd64.deb  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdbd-mysql-perl/libdbd-mysql-perl_4.012-1ubuntu1_amd64.deb  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-client-core-5.1_5.1.41-3ubuntu12.10_amd64.deb  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-client-5.1_5.1.41-3ubuntu12.10_amd64.deb  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-server-core-5.1_5.1.41-3ubuntu12.10_amd64.deb  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-server-5.1_5.1.41-3ubuntu12.10_amd64.deb  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-client_5.1.41-3ubuntu12.10_all.deb  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-server_5.1.41-3ubuntu12.10_all.deb  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-mysql_5.3.2-1ubuntu4.10_amd64.deb  Temporary failure resolving 'security.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

every time I try.

---

### Post by sanderd17 on 2011-11-13
Start with trying what the command says:

> **ServerSwag said:**
> 
```

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```



And also try if the servers are still up:
```

ping us.archive.ubuntu.com

```

---

### Post by ServerSwag on 2011-11-13
Well I have already tried to use the suggestions and it did not work and I tried the ping but it came up with unknown host idk if that was from my lack of knowledge and typing it in wrong or is it just the absence of servers.

---

### Post by SeijiSensei on 2011-11-13
Can you ping 91.189.92.169, one of the hosts that answers to archive.us.ubuntu.com?  If so, then you have a name resolution problem.  If not, you have a networking problem.

---

### Post by sanderd17 on 2011-11-13
I can access the server. Can you access other sites? Like google:

```

ping google.com

```

---

### Post by ServerSwag on 2011-11-13
ok its something I'm doing. it just said unknown host

---

### Post by sanderd17 on 2011-11-13
> **ServerSwag said:**
> ok its something I'm doing. it just said unknown host

No, that means it has a network problem. Which command said "unknown host"? Mine, or the one from SeijiSensei?

---

### Post by ServerSwag on 2011-11-13
```
$ ping 91.189.92.169
connect: Network is unreachable
$ ping google.com
ping: unknown host google.com

```

---

### Post by sanderd17 on 2011-11-13
> **ServerSwag said:**
> ```
$ ping 91.189.92.169
connect: Network is unreachable
$ ping google.com
ping: unknown host google.com

```

Ok, so what is your network configuration? Wired or wireless? Do other computer on the same network have problems with reaching the internet? Do neighbours have problems?

---

### Post by ServerSwag on 2011-11-13
> Ok, so what is your network configuration?
idk what exactly you mean by that

> Wired or wireless?
wired

> Do other computer on the same network have problems with reaching the internet?
on occasion

> Do neighbours have problems?
idk

---

### Post by sanderd17 on 2011-11-13
> **ServerSwag said:**
> 

on occasion


And now? What do you do in those occasions? Can you reach your router?

I can reach my router with a ping, but I don't know if yours will accept it. So if you don't get an answer from ping, you know nothing, but if you get an answer from ping, you know that the problem is between your internet provider and your router.

```

ping 192.168.1.1

```

---

### Post by ServerSwag on 2011-11-13
well, I got an answer from that ping

---

### Post by sanderd17 on 2011-11-13
Then the problem is your network providor, or something between your network provider and the router.

Try rebooting the router and check the cables.

---

### Post by ServerSwag on 2011-11-13
I reset the router and tried the ping aegean and it did not work

---

### Post by sanderd17 on 2011-11-13
> **ServerSwag said:**
> I reset the router and tried the ping aegean and it did not work

Sorry, can't help a lot anymore.

You will need to get help from your internet provider I suppose.

---

### Post by ServerSwag on 2011-11-13
alright I'll come back later after a chat with my isp

---

### Post by ServerSwag on 2011-11-13
Wait is there another way to install mysql?

---

### Post by ServerSwag on 2011-11-13
Actually I think I fixed it. 2 nights ago I was trying to set a static ip to my server and I guess I did something wrong but its all good now thanks for your help!

---

