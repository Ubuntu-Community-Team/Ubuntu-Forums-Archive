---
title: "Problem during installation of Passenger 2.2.11 on Ubuntu Server"
date: 2010-04-20
forum: Installation &amp; Upgrades
---

### Post by gansvv on 2010-04-20
Hi,
I am trying to get Ruby on Rails installed on Ubuntu Server 8.04, but an getting stuck with Passenger installation.

I used the tutorials from here:
[http://www.modrails.com/documentation/Users%20guide%20Apache.html](http://www.modrails.com/documentation/Users%20guide%20Apache.html)

```

$ sudo passenger-install-apache2-module
...
gcc -Iext -Iext/common -fPIC -DLINUX=2 -D_REENTRANT -D_GNU_SOURCE -I/usr/include/apr-1.0 -I/usr/include/apr-1.0 -I/usr/include/postgresql -DLINUX=2 -D_GNU_SOURCE -D_REENTRANT -I/usr/include/apr-1.0 -I/usr/include/openssl -I/usr/include/postgresql -I/usr/include/xmltok -pthread -I/usr/include/apache2 -D_REENTRANT -I/usr/local/include -Wall -g -DPASSENGER_DEBUG -DBOOST_DISABLE_ASSERTS -o ext/apache2/mod_passenger.o -c ext/apache2/mod_passenger.c
rake aborted!
Command failed with status (127): [gcc -Iext -Iext/common -fPIC -DLINUX=2 -D_...]
/usr/lib/ruby/gems/1.8/gems/passenger-2.2.11/Rakefile:302
(See full trace by running task with --trace)

--------------------------------------------

It looks like something went wrong


```

I tried to compile mod_passenger.c outside on the commandline and that worked fine!

Could someone help me with this. Thanks!

---

### Post by gansvv on 2010-04-20
Never mind. It was a sudo problem.

The error was at line 302. It looks like the mod_passenger.o file wasn't getting written. Permission problems!

I added sudo to the compilation macro (CC) in the beginning of the Rakefile
```

:/usr/lib/ruby/gems/1.8/gems/passenger-2.2.11$ sudo vim Rakefile
...
CC = "sudo gcc"
...

```

Dirty hack... but the installation went fine!

G/

---

