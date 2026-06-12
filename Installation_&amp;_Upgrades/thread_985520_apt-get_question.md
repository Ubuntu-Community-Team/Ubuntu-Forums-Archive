---
title: "apt-get question"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by eweibust on 2008-11-17
I've used apt-get to install something.  What is the best/easiest way to find out where it installed it?

Thanks...

---

### Post by oldos2er on 2008-11-17
Type its name in a terminal.

---

### Post by eweibust on 2008-11-17
That was worthless.  I do that and my cmd launches.  I want to know where the app is installed.

---

### Post by amauk on 2008-11-17
which <command>

---

### Post by evilkastel on 2008-11-17
show a little manners dude, he's just trying to help. 99 out of 100 times, it is in /home/usr/.thisisanexample . (replace thisisnaexample with the package you installed. remember, there is not such thing as fool proof)

EDIT: offcourse, which <command> should work too. i was a bit distracted.

---

### Post by issih on 2008-11-17
One definite way is to open synaptic package manager and search for the installed package. If you then select the package and hit properties, one of the tabs will list all the installed files associated with that package.

The advice you have been given wasn't bad though, generally its easiest to find things by guessing the likely name and using tab completion.

Hope that helps

---

### Post by eweibust on 2008-11-17
which mysql doesn't help either.  It just tells me that apt-get stuck the client cmd in /usr/bin.  Where is the server?

Thanks for at least responding.  I'm getting closer.

---

### Post by amauk on 2008-11-17
The MySQL daemon is located at /usr/sbin/mysqld

---

### Post by snova on 2008-11-17
```
dpkg -L <package name>
```

Will output a list of file in the package.

```
dpkg -L <package name> | grep bin/
```

Will find all files located in /usr/bin and /usr/sbin, where program binaries are (usually) located.

If you want to find where a particular program is running from, use the 'which' command.

---

### Post by akelsall on 2008-11-17
Try **locate** *program_name*. **Locate** searches through a database that's created once a day (via cron), so it's a lot quicker when you need to find ANY file (not just an executable) on your system. The downside is if a file was crated between the time cron ran and the current time, it won't find it (if that makes sense). 

If you installed it within the past 24 hours, you can try:

sudo find / -name *program_name*

Andy

---

### Post by spawn. on 2008-11-17
Wow

---

