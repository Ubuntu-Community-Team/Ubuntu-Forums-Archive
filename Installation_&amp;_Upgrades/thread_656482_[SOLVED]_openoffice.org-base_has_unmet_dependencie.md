---
title: "[SOLVED] openoffice.org-base has unmet dependencies."
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by sdide on 2008-01-02
Hey

I upgraded to Hardy, and all went well - except for openoffice. which will not install

```

root@sisyfos:~# apt-get install openoffice.org-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  openoffice.org-base: Depends: libhsqldb-java (>= 1.8.0.8-1) but it is not going to be installed
E: Broken packages
root@sisyfos:~# 
```

I does say that if I use an unstable distribution, the package may not exist.
but ..

```
root@sisyfos:~# apt-cache showpkg libhsqldb-java
Package: libhsqldb-java
Versions: 
1.8.0.9-2 (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages
                  MD5: 214a2c1ad31e54bb2dc0632a9a88f65a


Reverse Depends: 
  openoffice.org-base,libhsqldb-java 1.8.0.8-1
  openoffice.org2-base,libhsqldb-java 1.8.0.0-2
  entagged,libhsqldb-java
  openoffice.org-base,libhsqldb-java 1.8.0.8-1
  libhsqldb-java-doc,libhsqldb-java
  libhsqldb-java-gcj,libhsqldb-java 1.8.0.9-2
  hsqldb-server,libhsqldb-java 1.8.0.9-2
Dependencies: 
1.8.0.9-2 - gij (16 (null)) java-gcj-compat (16 (null)) java2-runtime (0 (null)) libservlet2.4-java (0 (null)) java-virtual-machine (0 (null)) libhsqldb-java-doc (0 (null)) libhsqldb-java-gcj (0 (null)) openoffice.org-base (3 1:2.3.1~m8) 
Provides: 
1.8.0.9-2 - 
Reverse Provides: 
root@sisyfos:~# 
```

Show that it is installed, even in a newer version. 
What am I doing wrong?

---

### Post by sciencewhiz on 2008-01-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/176487](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/176487) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is a known bug in Hardy. See the following bug report for more information: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/176487](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/176487)

---

### Post by sdide on 2008-01-02
Yes, thank you - the solutions was in there.

---

