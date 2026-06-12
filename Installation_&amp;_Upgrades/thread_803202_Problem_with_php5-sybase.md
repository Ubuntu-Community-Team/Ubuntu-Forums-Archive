---
title: "Problem with php5-sybase"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by trukulo on 2008-05-22
I upgraded 7.10 to 8.04 and i have a problem with sybase package.

I have several webs in php that use sybase to connect sql server, all of them were working before upgrade, but now, i have an error:

```
Fatal error: Call to undefined function sybase_connect() in /var/www/creacion.php on line 3
```

Same problem in all webs.

I have verified if apache2, php5, php5-sybase are well installed, and they are. I try reinstalling them, restarting services (apache2) and rebooting server (i now, this is stupid, but i did).

Can anyone help me with this annoying problem?

Notes: No pending configuration wit apt-get install -f , nor incorrectly installed packages.

I'm really lost here.

---

### Post by trukulo on 2008-05-22
Ok, i've found the answer.

I have to replace all sybase references for mssql.

Instead of using sybase_connect, i have to use mssql_connect, and all other functions the same.

Pretty annoying, but at least, it works.

---

### Post by DawgDaze on 2008-06-16
Does anyone have a better answer for this? I'd like not to have to refactor all of my code for this. It seems as though the aliases for the sybase_* functions that point to the mssql_* functions are just gone for some reason. Please post here if anyone has tips for restoring them.

Thanks

---

### Post by odie015 on 2008-08-27
I changed the sybase calls to mysql calls, but does anyone know how to configure the sybase-apache2 properly on hardy?

am getting this error: "Warning: mysql_connect() [function.mysql-connect]: Unknown MySQL server..."

---

### Post by IQRules on 2008-12-20
Did you source SYBASE.csh before restart apache2 server?

Is 8.04 okay to run ASE servers?

---

