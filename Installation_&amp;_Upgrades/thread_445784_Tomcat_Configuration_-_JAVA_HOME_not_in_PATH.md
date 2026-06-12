---
title: "Tomcat Configuration - JAVA_HOME not in PATH"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by saphil on 2007-05-16
I have an error in installing Tomcat```
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up tomcat5.5 (5.5.20-4ubuntu1) ...
 * no JDK found - please set JAVA_HOME
invoke-rc.d: initscript tomcat5.5, action "start" failed.
dpkg: error processing tomcat5.5 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of tomcat5.5-webapps:
 tomcat5.5-webapps depends on tomcat5.5 (>= 5.5.20-4ubuntu1); however:
  Package tomcat5.5 is not configured yet.
dpkg: error processing tomcat5.5-webapps (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tomcat5.5-admin:
 tomcat5.5-admin depends on tomcat5.5 (>= 5.5.20-4ubuntu1); however:
  Package tomcat5.5 is not configured yet.
dpkg: error processing tomcat5.5-admin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tomcat5.5
 tomcat5.5-webapps
 tomcat5.5-admin

```

I have gotten the JDK from SUN and loaded it in /opt/jdk1.6.0_01
I have ```
set JAVA_HOME=/opt/jdk1.6.0_01
```
and this doesn't seem to stick.  When I run the command set I get path=
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

should I append /opt/jdk..etc to the path, and how do I do that again?

I hav been having an ongoing problem with Firefox asking for an install of Java, until I loaded the new JDK, but Tomcat still cannot find it, even though I did the ./install on the command line (cannot get Java through synaptic (yet)

---

### Post by lexarrow on 2007-07-17
[this]("http://ubuntuforums.org/showthread.php?t=420034&highlight=tomcat6") will definitely help you if you didn't resolve it already. after the install you have to restart

---

### Post by saphil on 2007-07-18
thank you!  that is very helpful.

I will see what I can do when I get free time enough to do more with the project.  I just shelved the whole thing for a while.

---

