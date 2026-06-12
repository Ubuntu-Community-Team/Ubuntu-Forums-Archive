---
title: "how to remove references to mod security for apache2?"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by remifrommontpellier on 2008-02-20
[I]First post after using ubuntu for 2 years. Usually i find answers in the forum or google but...

I had to upgrade my server from dapper to gutsy (7.10) as i needed python 5. All seemed to work until i tried to access a database on my server with phpmyadmin.

It seems that all the upgrades have reset the computer to default ubuntu behavior of not behaving as a web server.

So i looked into the apache2 configuration. Reinstalled apache2. got message:[/I]

 * Starting web server (apache2)...                                             apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/mod-security.load: Cannot load /usr/lib/apache2/modules/mod_security.so into server: /usr/lib/apache2/modules/mod_security.so: cannot open shared object file: No such file or directory

[I]Looked into this mod security module. It is obsolete and no longer referenced in the distributions, due to license issues. 

Marked all apache modules for complete removal, then reinstalled them. Same error message!

I don't need mod security at the moment. It must be referenced somewhere in my files to appear there. If anyone know how i can remove all reference to this module - or to get my apache server going - it would be well appreciated.

Remi[/I]

---

### Post by whazooo on 2008-02-20
what does line 185 read in your /etc/apache2/apache2.conf

---

### Post by remifrommontpellier on 2008-02-21
Thanks. line 185 referenced mod-security, so i commented it out.

i can now access the index page of the web server, but:

firefox doesn't open the php file (from phpmyadmin). it seems to complain about https, which of course was no problem before the upgrade. hmmm!

thanks for your advice, 

Remi

---

### Post by whazooo on 2008-02-21
Hi,
Glad you got the mod-security problem worked out.

A few questions for you

what is the exact error of [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

What is the output of 
ls -ls /etc/apache2/mods-enabled

What is the output of
ls  /etc/apache2/sites-available
and
ls /etc/apache2/sites-available/ssl

and

cat /etc/apache2/sites-available/default

---

### Post by whazooo on 2008-02-21
I'm asking because if you had mod-ssl installed before the upgrade,
And your ssl directory is still in sites-available with your ssl stuff

you might just have to open /etc/apache2/ sites-available/default

and change;

```

NameVirtualHost *
<virtualhost *>
```

with

```

NameVirtualHost *:80
<virtualhost *:80>
```

---

