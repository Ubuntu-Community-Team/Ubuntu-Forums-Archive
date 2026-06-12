---
title: "MySQL Server problems"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by redi1 on 2010-03-08
My installation is an upgrade from 9.10 Karmic to Lucid. During installation I clicked to keep my old MySQL settings and as a result it no longer worked under lucid. Whenever I would type "sudo start mysql" it would just hang there until I ctrl-c and retrying says it is already on even tho it actually weren't.

I then removed the MySQL server with apt-get and using --purge. I removed mysql-server5.1 and the core, and then deleted the /mysql folder under /etc. Then apt-get clean into installing the packages back, setting up the default password for sql when it asked and again get into troubles.

```
red@kaliapullo:/tmp$ sudo start mysql
start: Job failed to start

```

I've taken a strace out of the starting call if it's helpful, read it here: [http://pastebin.com/E5bsB63y](http://pastebin.com/E5bsB63y)
I really need to get SQL working asap so I can continue working with a few web projects. Thanks for help! :)

---

### Post by iponeverything on 2010-03-08
Just run "sudo mysqld" from the command line and see if anything gets printed out, encase something is getting masked by upstart.

---

### Post by redi1 on 2010-03-08
red@kaliapullo:/tmp$ sudo mysqld
100308 19:43:34 [ERROR] Fatal error: Please read "Security" section of the manual to find out how to run mysqld as root!

100308 19:43:34 [ERROR] Aborting

100308 19:43:34 [Note] mysqld: Shutdown complete

red@kaliapullo:/tmp$

---

### Post by iponeverything on 2010-03-08
try it without the sudo.

---

### Post by gshegosh on 2010-04-15
redi1, did You manage to fix this issue?

I have similar thing, just running mysqld manually starts it up properly and then service stop mysql and service start mysql work properly, but after rebooting it doesn't start mysql and service start mysql hangs. It also hangs when trying to update using aptitude :-(

---

### Post by Mutant on 2010-04-17
Also have a similar problem as redi1. I did something like this:

1. Installed fresh install of Lucid, and mysql 5.1
2. Found some (unrelated) mysql issues with 5.1, so downgraded to 5.0
3. Discovered this wasn't supported, so purged all mysql packages, and reinstalled 5.1
4. I now have the same symptom as below (I get "start: Job failed to start" when trying to start up mysql... nothing in the logs, as far as I can tell).

I can workaround this by logging in as the mysql user and manually running /usr/sbin/mysqld.

Maybe this needs a bug raised?

---

