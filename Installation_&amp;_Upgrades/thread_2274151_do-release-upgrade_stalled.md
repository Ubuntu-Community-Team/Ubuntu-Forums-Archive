---
title: "do-release-upgrade stalled"
date: 2015-04-18
forum: Installation &amp; Upgrades
---

### Post by hansg2 on 2015-04-18
I am in the middle of a `do-release-upgrade` 10.04 to 12.04 server but it appears to have stalled while upgrading `mysql`


```
    Configuration file `/etc/mysql/my.cnf'
     ==> Modified (by you or by a script) since installation.
     ==> Package distributor has shipped an updated version.
       What would you like to do about it ?  Your options are:
        Y or I  : install the package maintainer's version
        N or O  : keep your currently-installed version
          D     : show the differences between the versions
          Z     : start a shell to examine the situation
     The default action is to keep your current version.
    *** my.cnf (Y/I/N/O/D/Z) [default=N] ? n
    Setting up adduser (3.113ubuntu2) ...
    Installing new version of config file /etc/deluser.conf ...
    Selecting previously unselected package mysql-server-5.5.
    (Reading database ... 180718 files and directories currently installed.)
    Unpacking mysql-server-5.5 (from .../mysql-server-5.5_5.5.41-0ubuntu0.12.04.1_i386.deb) ...

```

With no progress for 40 minutes.


The logs in `/var/log/dist-upgrade` show no other indication of errors.


Can anyone recommend best next step?

---

### Post by dino99 on 2015-04-18
in the past week, i've seen several issues like yours to upgrade 10.04 to 12.04. That should have been tested enough, but users met troubles. So a clean fresh install is the way to get a stable installation

---

### Post by hansg2 on 2015-04-18
I was fearing that answer, though have already begun prepping for it...

Usual, I test on multiple copies of server but as soon as I do it on live it breaks :)

Is there anyway to ctrl+c this do-release-upgrade and rerun?

---

