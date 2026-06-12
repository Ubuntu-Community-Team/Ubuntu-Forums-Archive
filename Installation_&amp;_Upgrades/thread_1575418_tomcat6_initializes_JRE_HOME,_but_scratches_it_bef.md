---
title: "tomcat6 initializes JRE_HOME, but scratches it before use"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by hphenriques on 2010-09-15
hph@ubuntu:~$ sudo service tomcat6 stop
 * Stopping Tomcat servlet engine tomcat6
hph@ubuntu:~$ sudo service tomcat6 start
 * Starting Tomcat servlet engine tomcat6
Using CATALINA_BASE:   /var/lib/tomcat6
Using CATALINA_HOME:   /usr/share/tomcat6
Using CATALINA_TMPDIR:   /tmp/tomcat6-tmp
Using JRE_HOME:               /usr/lib/jvm/java-6-openjdk
Using CLASSPATH:            /usr/share/tomcat6/bin/bootstrap.jar

hph@ubuntu:~$ echo $CATALINA_HOME

hph@ubuntu:~$ echo $CLASSPATH

hph@ubuntu:~$ echo $JRE_HOME

Can anyone please tell me why my environment variables are NULL?

Thanks,
Harry

---

### Post by hphenriques on 2010-09-15
Hello,

I discovered that the environment variables that I mentioned in my previous post need to be setup in /etc/environment, manually.  The initialization of variables during the startup of Tomcat6 don't persist past the invocation with "$ sudo service tomcat6 start."

Harry

---

