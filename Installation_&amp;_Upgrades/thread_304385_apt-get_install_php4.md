---
title: "apt-get install php4"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by endiku on 2006-11-21
I just installed a new 6.06 LAMP ubuntu server. Everything is great except I need to run php4 not 5. 

I've done a apt-get remove php5-common and also removed the libapache2-mod-php5

However now I want to install php4 and it just isn't happening.

sudo apt-get install php4
E: Couldn't find package php4

sudo apt-get install php4-common
E: Couldn't find package php4-common

I've gone in and uncommented the additional lines in /etc/apt/sources.list but it doesn't help find the php4

So any ideas out there?

---

### Post by adamkane on 2006-11-21
This is how you do it:

Apache2/PHP4/MySQL4:
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```Apache2/PHP5/MySQL4:
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Apache2/PHP5/MySQL5:
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Reboot (or start mysql manually).

Open phpmyadmin from network or remote machine:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by endiku on 2006-11-21
apache2 is already the newest version.
E: Couldn't find package php4

---

### Post by adamkane on 2006-11-21
You may  need to enable the universe repository.

Edit /etc/apt/sources.list.

Uncomment the universe.

---

### Post by endiku on 2006-11-21
Sorry to be a jerk but did you read my post at all? I did that already.

---

### Post by adamkane on 2006-11-21
No worries. My dumb posts at least help get attention to your thread, even if I don't know the answer.

Probably something is wrong with sources.list or your internet connection.

You may need to:
```

sudo apt-get update

```

---

### Post by endiku on 2006-11-22
Finally got it. I had to place the dns entries in /etc/resolv.conf is all

---

