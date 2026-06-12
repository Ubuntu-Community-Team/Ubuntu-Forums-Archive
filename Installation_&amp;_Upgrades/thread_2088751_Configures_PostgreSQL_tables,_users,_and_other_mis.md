---
title: "Configures PostgreSQL tables, users, and other miscellaneous settings"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by Rbacon on 2012-11-27
I am attempting to install OPENNMS on my server... I got it loaded but need to run /usr/share/opennms/bin/install -dis and when I try it gives me...
Warning: unable to load /usr/share/opennms/ect/opennms.properties
Exception in thread "main" java.io.FileNotFoundException: /usr/share/opennms/etc/opennms-datasources.xml (Permission denied)
at java.io.FileInputStream.open(Native Method)
at java.io.FileInputStream.<init>(FileInputStream.java:137)
at org.opennms.install.Installer.install(Installer.java:161)
at org.opennms.install.Installer.main(Installer.java:949)

This is my first attempt at a server in a VERY long time and so I am in need of OPENNMS for dummies

---

### Post by Rbacon on 2012-11-28
I have tried a few different things to help move myself forward and Now when I try to install opennms i receive this

Exception in thread "main" org.opennms.core.schema.MigrationException: an error occurred getting the version from the database
   at org.opennms.core.schema.Migrator.getDatabaseVersion(Migrator.java:0206)
Also 
Caused by: org.postgresql.util.PSQLException: Connection refused. Check that the hostname and port are correct and that the post master is accepting TCP/IP connections.

Any help would be great! Thank you

---

