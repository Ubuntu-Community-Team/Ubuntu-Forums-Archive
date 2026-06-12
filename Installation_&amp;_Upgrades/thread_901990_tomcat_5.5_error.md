---
title: "tomcat 5.5 error"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by vedanta_2004 on 2008-08-26
Hi,
I got following error when I tried to install some python libraries..

Setting up python-matplotlib-doc (0.91.2-0ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 tomcat5.5
 tomcat5.5-webapps
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up tomcat5.5 (5.5.25-5ubuntu1) ...
 * no JDK found - please set JAVA_HOME
invoke-rc.d: initscript tomcat5.5, action "start" failed.
dpkg: error processing tomcat5.5 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of tomcat5.5-webapps:
 tomcat5.5-webapps depends on tomcat5.5 (>= 5.5.25-5ubuntu1); however:
  Package tomcat5.5 is not configured yet.
dpkg: error processing tomcat5.5-webapps (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tomcat5.5
 tomcat5.5-webapps


E: tomcat5.5: subprocess post-installation script returned error exit status 1
E: tomcat5.5-webapps: dependency problems - leaving unconfigured

Please help..

-Vedanta.

---

### Post by prostar on 2008-08-27
I had this problem as well.  Luckily a Yahoo search turned this up...

[http://douglasjarquin.com/articles/java-and-tomcat-on-ubuntu-hardy/](http://douglasjarquin.com/articles/java-and-tomcat-on-ubuntu-hardy/)

What a PITA!  This is so obscure I would have spent hours just like the blogger...

---

