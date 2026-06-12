---
title: "Problems with apt-get"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by yuneyev on 2006-09-28
Well, I have installed, postgres-8.1 by apt-get, and now trying to uninstall I get this error:

Removing postgresql-8.1 ...
 * Stopping PostgreSQL 8.1 database server  * Error: specified cluster does not exist
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.1, action "stop" failed.
dpkg: erro processando postgresql-8.1 (--remove):
 subprocesso pre-removal script retornou código de saída de error 1
 * Starting PostgreSQL 8.1 database server  * Error: specified cluster does not exist
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.1, action "start" failed.
dpkg: erro enquanto efetuava-se a limpeza:
 subprocesso post-installation script retornou código de saída de error 1
Removing postgresql-client-8.1 ...
Erros foram encontrados durante processamento de:
 postgresql-8.1
E: Sub-process /usr/bin/dpkg returned an error code (1)

And it says me to execute sudo apt-get install -f

When I do that I get this:

dpkg: erro processando postgresql-8.1 (--configure):
 subprocesso post-installation script retornou código de saída de error 1
Erros foram encontrados durante processamento de:
 postgresql-8.1
E: Sub-process /usr/bin/dpkg returned an error code (1)

I can't reinstall it neither remove.

What should I do? :(

---

### Post by yuneyev on 2006-09-28
bump

---

### Post by lovepolo on 2006-11-10
did you find a solution? 

i have the same issue.

---

