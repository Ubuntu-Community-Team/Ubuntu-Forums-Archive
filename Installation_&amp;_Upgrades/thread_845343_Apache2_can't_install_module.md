---
title: "Apache2 can't install module????"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by KingTermite on 2008-06-30
I have downloaded the mod_auth_sspi module (which contains the mod_auth_sspi.so) library.

I copied that library into the /usr/lib/apache2/modules directory where all the other library modules seem to be stored.

I added the lines (per instructions of module):
```
<IfModule !mod_auth_sspi.c>

    LoadModule sspi_auth_module modules/mod_auth_sspi.so

</IfModule>
```
to the httpd.conf file (where I have other similarly loaded already).

When I try to restart apache I get the error:
```
apache2: Syntax error on line 187 of /etc/apache2/apache2.conf: Syntax error on line 6 of /etc/apache2/httpd.conf: Cannot load /etc/apache2/modules/mod_auth_sspi.so into server: /etc/apache2/modules/mod_auth_sspi.so: cannot open shared object file: No such file or directory

```

It appears to be trying to force "/etc/apache2" on front of the modules directory. That's not the location....its in /usr/lib/apache2. Why is this doing this? And why does it not do it for the other modules I have set with LoadModule (they just say "already installed...skipping")??

---

### Post by KingTermite on 2008-07-01
bump...anybody?

---

### Post by cmatte on 2008-08-08
Same question here...someone?

---

