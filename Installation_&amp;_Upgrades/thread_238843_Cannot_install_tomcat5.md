---
title: "Cannot install tomcat5"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by clanie on 2006-08-18
I have installed Tomcat on other Ubuntu Dapper servers before, but when i tried it today on a newly installed server (installed from the  ubuntu-6.06.1-alternate-amd64 CD), it failed with the messages below.

Are all these packages really broken, or is it my installation that's messed up?

Any way to fix it?

# aptitude install tomcat5
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libcommons-beanutils-java libcommons-digester-java
  libcommons-launcher-java libcommons-modeler-java libmx4j-java
  libtomcat5-java
The following NEW packages will be automatically installed:
  libcommons-collections-java libcommons-collections3-java
  libcommons-dbcp-java libcommons-el-java libcommons-fileupload-java
  libcommons-pool-java libservlet2.4-java
The following NEW packages will be installed:
  libcommons-collections-java libcommons-collections3-java
  libcommons-dbcp-java libcommons-el-java libcommons-fileupload-java
  libcommons-pool-java libservlet2.4-java tomcat5
0 packages upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 7038kB of archives. After unpacking 16,8MB will be used.
The following packages have unmet dependencies:
  libtomcat5-java: Depends: ant which is a virtual package.
                   Depends: libregexp-java which is a virtual package.
                   Depends: libcommons-logging-java which is a virtual package.
  libcommons-modeler-java: Depends: libcommons-logging-java which is a virtual p
ackage.
  libcommons-beanutils-java: Depends: libcommons-logging-java which is a virtual
 package.
  libcommons-launcher-java: Depends: libcommons-logging-java which is a virtual
package.
  libmx4j-java: Depends: liblog4j1.2-java which is a virtual package.
                Depends: libbcel-java (>= 5.0) which is a virtual package.
  libcommons-digester-java: Depends: libcommons-logging-java which is a virtual
package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
libcommons-beanutils-java [Not Installed]
libcommons-digester-java [Not Installed]
libcommons-fileupload-java [Not Installed]
libcommons-launcher-java [Not Installed]
libcommons-modeler-java [Not Installed]
libmx4j-java [Not Installed]
libtomcat5-java [Not Installed]
tomcat5 [Not Installed]

Score is 62

Accept this solution? [Y/n/q/?]

---

### Post by clanie on 2006-08-21
Problem solved.
The installer had commented-out a line in apt's sources.list "because it failed to verify".

---

