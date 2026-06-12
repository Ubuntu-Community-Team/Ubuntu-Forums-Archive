---
title: "eclipse start up error (added attachment)"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by moonhk on 2007-01-24
Dear Reader

I have install eclipse. Then run the application have below error

An error has occurred. See the log file
/home/moonhk/.eclipse/org.eclipse.platform_3.1.2/configuration/1169651853829.log.

try to get new update
root@hex:~# apt-get install eclipse
Reading package lists... Done
Building dependency tree... Done
eclipse is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@hex:~#



Attachment is error log.

---

### Post by Paul41 on 2007-01-24
Have you looked for /home/moonhk/workspace/.metadata to see if it exists and that you have permissions to it since it looks like that is part of the error?

You could also test to see if permissions are the problem by opening Eclipse with root privileges.

From the terminal:
```
gksudo eclipse
```

---

### Post by moonhk on 2007-01-24
[FONT="System"]You are right. Now OK. 
Thank a lot.

moonhk@hex:~/workspace$ ls -la
total 12
drwxr-xr-x  3 moonhk moonhk 4096 2007-01-18 16:00 .
drwxr-xr-x 45 moonhk moonhk 4096 2007-01-25 09:22 ..
drwxr-xr-x  3 moonhk root   4096 2007-01-25 09:21 .metadata
moonhk@hex:~/workspace$[/FONT]

---

