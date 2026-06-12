---
title: "upgrade errors"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by MoHamm on 2007-07-08
Hi all ....
 
I was getting the following error when trying to upgrade;

> dpkg: syntax error: unknown user `postfix' in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)

then after reading some threads and finding out its related to deleting old users and adding new ones,
 I deleted the following lines in; 

> sudo gedit /var/lib/dpkg/statoverride

postfix postdrop 02710 /var/spool/postfix/public
root postdrop 02555 /usr/sbin/postdrop

leaving;

> 
root postdrop 02555 /usr/sbin/postqueue
hplip root 755 /var/run/hplip


now I get the following when trying to upgrade;

> 
dpkg: statoverride file contains empty line
E: Sub-process /usr/bin/dpkg returned an error code (2)


any help that can be offered before i start messing up my system..

thanks

---

### Post by waster on 2007-07-08
are there any empty lines in the file?

---

### Post by MoHamm on 2007-07-08
this is the exact output for;

> 
gedit /var/lib/dpkg/statoverride


root postdrop 02555 /usr/sbin/postqueue
hplip root 755 /var/run/hplip

not sure what else should be on there..

thanks waster

---

### Post by bapoumba on 2007-07-08
[http://ubuntuforums.org/showthread.php?t=329560]("http://ubuntuforums.org/showthread.php?t=329560")
You may have checked that thread already. Please check the end of the file, if there is an empty line and remove it.

Here is mine, as an example:
```
~$ cat /var/lib/dpkg/statoverride
hplip root 755 /var/run/hplip
```

---

### Post by MoHamm on 2007-07-09
thanks much bapoumba, there was indeed an empty line...

all is well again.

---

### Post by bapoumba on 2007-07-09
You're welcome!
Glad to see you got it to work.

---

