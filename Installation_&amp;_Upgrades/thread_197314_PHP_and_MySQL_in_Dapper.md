---
title: "PHP and MySQL in Dapper"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by yellowtip on 2006-06-15
Hi,

I just upgraded my Breezy installation to Dapper. 

...big mistake! :( 

It upgraded my installations of PHP (from php 4.3.x to php 4.4.x) and MySQL (from 4.0.x to 5.x).

I'm running a php application on this server that requires php 4.3 and mysql 4.0 (nothing later!).

Up until now I was using the Synaptics package manager to manage all my installs. But in Dapper, it doesn;t show these old packages anymore.

I'm not a professional linux user, so I'm really hoping there's an easy way to downgrade. I'd hate to have to rebuild and install all of this manually.

Why can help me?

Thanks in advance.

---

### Post by ayoli on 2006-06-15
```
[21:44:48@root.zone]:/home/ayoli ># apt-cache search mysql-server-4.1
mysql-server-5.0 - mysql database server binaries
mysql-server-4.1 - mysql database server binaries
```

myql 4 seems to be in dapper repositories (universe)

but php 4 is only in 4.4.* version. but i don't think there's so much diff etween 4.3.* and 4.4.* series.

cheers.

---

### Post by yellowtip on 2006-06-15
Thanks for the response Ayoli,

MySQL 4.1 is indeed present, but when i try to install it I get installation errors. From what i can see, it also needs to install the mysql-common package and that is still the 5.0 version.

Appart from that, it's MySQL 4.0 that i need, not 4.1.

Do I need to format and make a clean install of Breezy to get these old packages to install again?

Is this simply a case that Dapper doesn't support MySQL 4.0 and PHP4.3 anymore?

Any help would be appreciated.

---

### Post by ayoli on 2006-06-15
so, i guess you will have to do your own builds or downgrade to breezy.:-&

---

