---
title: "Error while running apt-get upgrade."
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by nmahadkar on 2010-12-24
I am getting the following error while running apt-get upgrade.

> (Reading database ... 90%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `gdebi': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


I have tried everything but cant seem to figure it out.  I am hoping someone can shed some light on this.

---

### Post by Rubi1200 on 2010-12-25
Hi and welcome to the forums :)

Try running these commands in the terminal:

```
sudo apt-get install -f

sudo dpkg --configure -a
```

Report back with errors (copy/paste from the terminal).

Thanks.

---

### Post by susema on 2010-12-25
Look here, there is a solution about this problem;

[http://ubuntuforums.org/showpost.php?p=7999235&postcount=9](http://ubuntuforums.org/showpost.php?p=7999235&postcount=9)

---

### Post by nmahadkar on 2010-12-25
```
 mv /var/lib/dpkg/info/[PACKAGE NAME].list  /var/lib/dpkg/info/[PACKAGE NAME].list.broke
```

Solved the problem.  You must do this for all unreadable packages.  Then run ```
apt-get update
apt-get upgrade
```

Thank you everyone.

---

### Post by karthick87 on 2010-12-25
Mark this as [COLOR=Red][SOLVED][/COLOR]

---

