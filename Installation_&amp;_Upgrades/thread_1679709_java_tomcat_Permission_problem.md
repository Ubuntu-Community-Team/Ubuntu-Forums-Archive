---
title: "java tomcat Permission problem"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by fatmailer on 2011-02-01
Hi,
I was managing to put Java Tomcat on Ubuntu Server 10.10. Everything seemed to be OK until I started the Tomcat:

[COLOR=Blue]/opt/pache-tomcat-5.5.31/bin$ startup.sh[/COLOR]

I got:

[COLOR=Red]Using CATALINA_BASE:   /opt/apache-tomcat-5.5.31
Using CATALINA_HOME:   /opt/apache-tomcat-5.5.31
Using CATALINA_TMPDIR: /opt/apache-tomcat-5.5.31/temp
Using JRE_HOME:        /usr/lib/jvm/java-6-sun
Using CLASSPATH:       /opt/apache-tomcat-5.5.31/bin/bootstrap.jar

touch: cannot touch '/opt/apache-tomcat-5.5.31/logs/catalinaout': Permission denied

$ /opt/apache-tomcat-5.5.31/bin/catalina.sh: 373: cannot create /opt/apache-tomcat-5.5.31/logs/catalinaout: Permission denided
[/COLOR]
Well, I tried
[COLOR=Blue]sudo chown -R www:data-www:data $CATALINA_HOME[/COLOR]

(then typed in the password)

I got

[COLOR=Red]chown: invalid mode: 'www:data-www:data'[/COLOR]

Could anyone give me some ideas to make Tomcat runs?

Cheers,

F

---

