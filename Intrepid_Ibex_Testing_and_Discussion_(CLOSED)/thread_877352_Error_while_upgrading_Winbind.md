---
title: "Error while upgrading Winbind"
date: 2008-08-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Peaceable Frood on 2008-08-01
Every time I do a sudo apt-get update, it fails to upgrade winbind. I keep getting this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ubuntu-desktop
The following packages will be upgraded:
  winbind
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
16 not fully installed or removed.
Need to get 0B/3334kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 150092 files and directories currently installed.)
Preparing to replace winbind 2:3.2.0-4ubuntu2 (using .../winbind_2%3a3.2.0-4ubuntu3_i386.deb) ...
/etc/init.d/winbind: 54: Syntax error: ")" unexpected (expecting ";;")
invoke-rc.d: initscript winbind, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/etc/init.d/winbind: 54: Syntax error: ")" unexpected (expecting ";;")
invoke-rc.d: initscript winbind, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/winbind_2%3a3.2.0-4ubuntu3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
/etc/init.d/winbind: 54: Syntax error: ")" unexpected (expecting ";;")
invoke-rc.d: initscript winbind, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/winbind_2%3a3.2.0-4ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried deleting the new deb and redownloading it, but it ends up with the same error.

EDIT - Nevermind, I didn't see the post describing how to fix it.

---

### Post by vishnu on 2008-08-02
which post?  can you link to it?

---

### Post by vishnu on 2008-08-02
nm.  found it

---

### Post by Yannick Le Saint kyncani on 2008-08-02
> **vishnu said:**
> nm.  found it

And yet you didn't provide a link to it yourself ;)

( just teasing you )

---

### Post by ]FT[ on 2008-08-02
Maybe this: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg943816.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg943816.html)

---

### Post by eeclark on 2008-08-04
Or this...
[http://ubuntuforums.org/showthread.php?t=876981]("http://ubuntuforums.org/showthread.php?t=876981")

---

