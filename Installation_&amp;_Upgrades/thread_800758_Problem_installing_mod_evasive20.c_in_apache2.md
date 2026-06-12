---
title: "Problem installing mod_evasive20.c in apache2"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by cjtjamandra on 2008-05-20
I have a 64 bit ubuntu server and iam trying to install mod_evasive. but in the steps where i will execute the command:

```
sudo /usr/bin/apxs2 -cia mod_evasive20.c
```


an error has occured:

```
line 1222: x86_64-linux-gnu-gcc: command not found
```

what does this error mean?

please help.. thx

---

### Post by ciya on 2008-12-02
i have same question too.


root@ubuntu:~# /usr/bin/apxs2 -i -c mod_evasive20.c
/usr/share/apr-1.0/build/libtool --silent --mode=compile --tag=disable-static x86_64-linux-gnu-gcc -prefer-pic -DLINUX=2 -D_GNU_SOURCE -D_REENTRANT -I/usr/include/apr-1.0 -I/usr/include/openssl -I/usr/include/postgresql -I/usr/include/xmltok -pthread     -I/usr/include/apache2  -I/usr/include/apr-1.0   -I/usr/include/apr-1.0 -I/usr/include/postgresql  -c -o mod_evasive20.lo mod_evasive20.c && touch mod_evasive20.slo
/usr/share/apr-1.0/build/libtool: line 1222: x86_64-linux-gnu-gcc: command not found
apxs:Error: Command failed with rc=65536
.

---

