---
title: "MySQL ODBC Connection Mishap"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by smd333 on 2007-01-14
As I begin my linux conversion I am almost done without trouble. :D However, a minor MySQL problem provides a set back. I have the MySQL server installed and running following the docs on Edgy. When trying to connect via dev machine on network, I receive : Host '192.168.1.101' is not allowed to connect to this MySQL server. The only change I made was setting the Bind-Address = 192.168.1.103 and I am using MySQL ODBC driver 3.51 to connect. It must be a permissions thing given the error message. I am using username and password which I set up on install: mysqladmin -u root -p password mypassword.

---

### Post by smd333 on 2007-01-14
Here's the kicker... Don't forget to grant yourself permissions. :rolleyes: 

```
GRANT ALL ON test.* to 'myuser'@'192.168.1.101' IDENTIFIED BY 'mypassword';
```

Later

---

