---
title: "tomcat7 and jdbc-pooling support problems in repository"
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by jamiegau on 2013-06-24
I have been using Ubuntu server for a long time, I have started using tomcat7 that comes with ubuntu over hand made installs.
Recently I came across a problem with the Ubuntu repository version of the tomcat7 deb file..

When writting a web app, it is best to utilise database pooling (For connections to the database)

To do this you need a JAR file called tomcat-jdcb.jar
this file typically comes with the directly down loaded version of tomcat7 (From the Apache website), so all works fine if you use that..
However, if you jump to using the tomcat7 that comes in the Ubuntu repository, your in trouble, as tomcat-jdbc.jar is not available in any deb files from what I can see..
So I had to get the latest version and copy it into the lib directory for tomcat.

This is broken, and could some one look into adding tomcat-jdcb.jar to the typical tomcat7 install deb file.

Thanks,
James

---

