---
title: "update apache 2.2.22 on ubuntu 12.04"
date: 2014-03-18
forum: Installation &amp; Upgrades
---

### Post by SavenetSolutions on 2014-03-18
Hi all,

I need to upgrade apache on my ubuntu 12.04 server.
I do not know how to do it. apt-get gives me no updates, neither does synaptic package manager.
all i need is to upgrade to apache 2.2.23 to fix the following vulnerabilitie

Insecure LD_LIBRARY_PATH handling 
Cross-site scripting in mod_negotiation when untrusted uploads are supported Affected Versions:
Apache HTTP Server prior to version 2.2.23Successful exploitation may lead to execution of arbitrary code on the system within the context of the affected applications.
Solution
These vulnerabilities have been patched in Apache 2.2.23.

I have zabbix server running on my ubuntu server.

thanks in advance for all your help

regards,

Sebastian

---

### Post by 7sbaV8Kt5PTh on 2014-03-19
There isn't an upgrade in the repository for > 2.2.22.  However, Ubuntu does backport security updates, and that one has been covered.  In looking around, it is a minimal security vulnerability (localhost only) anyway.  If you are dead set on upgrading Apache, you will have to do it manually, outside of the package upgrade path.  In this case, I wouldn't do that, since the fix was integrated in 2.2.22.

-John the Danger Monkey

---

### Post by SeijiSensei on 2014-03-19
Just to add, the practice of "backporting" security fixes is pretty common among all major distributions.  Often, as in this case, a security patch will be applied to the source code from the current release version rather than upgrading the release to the newer version.  This is especially true for long-term support versions like 12.04 and, e.g, RedHat and its derivatives like CentOS. These types of releases with long lifespans maintain the same versions of each package throughout except for "backported" security updates.

You can check to see whether a particular fix has been applied by looking at the Changelog for a package.  Here's the one for apache2: [http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.2.22-1ubuntu1.4/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.2.22-1ubuntu1.4/changelog).  The problem with mod_negotiation appears to have been addressed in November, 2012.

---

