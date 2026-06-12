---
title: "Where does apt-get install packages"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by mistakentridgell on 2009-12-29
Suppose I execute the following command:

sudo apt-get install mysql-server

Where does the system install mysql-server. Is there any default place where apt-get installs the packages or does it depend on the package itself

How can I see where a package is installed

---

### Post by wojox on 2009-12-29
It depends. Apt-get does a good job of distributing the files. Try running 

```
whereis mysql-server
```

or 

```
locate mysql-server
```

---

### Post by mistakentridgell on 2009-12-29
I tried running 

whereis mysql-server      but the ouptut is not very helpful

mysql-server: 


locate mysql-server
/usr/share/app-install/desktop/mysql-server.desktop
/usr/share/mysql-common/internal-use-only/_etc_logrotate.d_mysql-server
/var/cache/apt/archives/mysql-server-core-5.1_5.1.37-1ubuntu5_i386.deb

However, as given above locate displays a bunch of results. However, I am not sure what they mean

I am assuming last line /var/cache/... represents the debian package that has been used to install....

I am still not sure where exactly is mysql-server installed

---

### Post by Robster2 on 2009-12-29
whereis did not work for me either

Have you tried running MySQL? It does not look like it is installed if that is all you got.

I installed it via the System>Administration>Synaptic Package Manager.

You have to do something else.  


/usr/share/doc/

Is where my file is located.


rob@rob-laptop:~$ locate mysql-server
/etc/logcheck/ignore.d.paranoid/mysql-server-5_0
/etc/logcheck/ignore.d.server/mysql-server-5_0
/etc/logcheck/ignore.d.workstation/mysql-server-5_0
/etc/logrotate.d/mysql-server
/usr/share/doc/mysql-server
/usr/share/doc/mysql-server-5.0
/usr/share/doc/mysql-server-core-5.0
/usr/share/doc/mysql-server/changelog.Debian.gz
/usr/share/doc/mysql-server/copyright
/usr/share/doc/mysql-server-5.0/EXCEPTIONS-CLIENT.gz
/usr/share/doc/mysql-server-5.0/NEWS.Debian.gz
/usr/share/doc/mysql-server-5.0/README.Debian.gz
/usr/share/doc/mysql-server-5.0/changelog.Debian.gz
/usr/share/doc/mysql-server-5.0/copyright
/usr/share/doc/mysql-server-5.0/copyright.more
/usr/share/doc/mysql-server-5.0/examples
/usr/share/doc/mysql-server-5.0/mysqld.sym.gz
/usr/share/doc/mysql-server-5.0/examples/my-huge.cnf.gz
/usr/share/doc/mysql-server-5.0/examples/my-innodb-heavy-4G.cnf.gz
/usr/share/doc/mysql-server-5.0/examples/my-large.cnf.gz
/usr/share/doc/mysql-server-5.0/examples/my-medium.cnf.gz
/usr/share/doc/mysql-server-5.0/examples/my-small.cnf
/usr/share/doc/mysql-server-5.0/examples/ndb_mgmd.cnf
/usr/share/doc/mysql-server-core-5.0/changelog.Debian.gz
/usr/share/doc/mysql-server-core-5.0/copyright
/usr/share/lintian/overrides/mysql-server-5.0
/usr/share/mysql-common/internal-use-only/_etc_logrotate.d_mysql-server
/var/lib/dpkg/info/mysql-server-5.0.conffiles
/var/lib/dpkg/info/mysql-server-5.0.config
/var/lib/dpkg/info/mysql-server-5.0.list
/var/lib/dpkg/info/mysql-server-5.0.md5sums
/var/lib/dpkg/info/mysql-server-5.0.postinst
/var/lib/dpkg/info/mysql-server-5.0.postrm
/var/lib/dpkg/info/mysql-server-5.0.preinst
/var/lib/dpkg/info/mysql-server-5.0.prerm
/var/lib/dpkg/info/mysql-server-5.0.templates
/var/lib/dpkg/info/mysql-server-core-5.0.list
/var/lib/dpkg/info/mysql-server-core-5.0.md5sums
/var/lib/dpkg/info/mysql-server.list
/var/lib/dpkg/info/mysql-server.md5sums
/var/lib/dpkg/info/mysql-server.preinst
rob@rob-laptop:~$ 
rob@rob-laptop:~$

---

