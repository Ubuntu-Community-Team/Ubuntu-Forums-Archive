---
title: "apt-get can't install postgres"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by markhorrocks on 2010-12-13
I am a relative newbie to Ubuntu. I had postgreql-8.4 install and removed it then installed 9.0 but it ran on the wrong port. I tried unsuccessfully to change the port in config so I set about removing every file i could containing postgresql*

Now apt-get can neither remove nor install postgresql-9.0. Is there any way i can download and replace the files I need? Here is the output


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  oidentd ident-server
The following NEW packages will be installed:
  postgresql-9.0
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 5,126kB of archives.
After this operation, 14.6MB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/pitti/postgresql/ubuntu/](http://ppa.launchpad.net/pitti/postgresql/ubuntu/) maverick/main postgresql-9.0 amd64 9.0.1-1~maverick [5,126kB]
Fetched 5,126kB in 16s (314kB/s)                                               
Selecting previously deselected package postgresql-9.0.
(Reading database ... 
dpkg: warning: files list file for package `postgresql-doc-8.4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `postgresql-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `postgresql-client' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `postgresql-client-8.4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `postgresql-doc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `postgresql-client-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `postgresql-client-9.0' missing, assuming package has no files currently installed.
(Reading database ... 37392 files and directories currently installed.)
Unpacking postgresql-9.0 (from .../postgresql-9.0_9.0.1-1~maverick_amd64.deb) ...
Setting up postgresql-9.0 (9.0.1-1~maverick) ...
.: 10: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-9.0 (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 postgresql-9.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
mark@ubuntu:~$ sudo dpkg --configure -a
Setting up postgresql-9.0 (9.0.1-1~maverick) ...
.: 10: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-9.0 (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 postgresql-9.0

---

### Post by tajiknomi on 2010-12-13
[SIZE=2]Try "sudo dpkg --configure -a"

then "sudo apt-get update"

see what is th outcome now..
[/SIZE]

---

### Post by markhorrocks on 2010-12-13
Still no joy

Reading package lists... Done
mark@ubuntu:~$ sudo apt-get install postgresql-9.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
postgresql-9.0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up postgresql-9.0 (9.0.1-1~maverick) ...
.: 10: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-9.0 (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 postgresql-9.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by markhorrocks on 2010-12-13
mark@ubuntu:~$ sudo dpkg --remove postgresql-9.0
(Reading database ... 
dpkg: warning: files list file for package `postgresql-doc-8.4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `postgresql-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `postgresql-client' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `postgresql-client-8.4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `postgresql-doc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `postgresql-client-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `postgresql-client-9.0' missing, assuming package has no files currently installed.
(Reading database ... 37563 files and directories currently installed.)
Removing postgresql-9.0 ...
.: 7: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-9.0 (--remove):
 subprocess installed pre-removal script returned error exit status 127
Errors were encountered while processing:
 postgresql-9.0

---

### Post by tajiknomi on 2010-12-13
[SIZE=2]Try these :-

[/SIZE]```
[SIZE=2]sudo apt-get install -f[/SIZE]
```

```
[SIZE=2]sudo apt-get clean[/SIZE]
```

then

```
[SIZE=2]sudo apt-get update[/SIZE]
```

---

### Post by markhorrocks on 2010-12-13
Tried all of those before - same result

I am downloading a bin graphical install from postgresql.

---

### Post by sikander3786 on 2010-12-14
> **markhorrocks said:**
> Tried all of those before - same result

I am downloading a bin graphical install from postgresql.
If it isn't solved yet, this one might help.

[http://www.linuxquestions.org/questions/debian-26/problems-with-apt-get-563086/](http://www.linuxquestions.org/questions/debian-26/problems-with-apt-get-563086/)

---

