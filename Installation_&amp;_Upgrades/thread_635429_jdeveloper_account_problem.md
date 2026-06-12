---
title: "jdeveloper account problem"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by mitjab on 2007-12-08
when i run priject i get this

[waiting for the server to complete its initialization...]
07/12/08 23:39:10 Error initializing server: OC4J administrator account is not configured correctly. Please make sure that at least one administration account is created and configured correctly.
07/12/08 23:39:10 Fatal error: server exiting

and in console i see this

java.net.UnknownHostException: localhost.localdomain mitjab-laptop: localhost.localdomain mitjab-laptop
        at java.net.InetAddress.getLocalHost(InetAddress.java:1353)
        at oracle.ideimpl.webupdate.CheckMasterListRunnable.buildLocalHostNames(CheckMasterListRunnable.java:52)
        at oracle.ideimpl.webupdate.CheckMasterListRunnable.<init>(CheckMasterListRunnable.java:38)
        at oracle.ideimpl.webupdate.AutomaticCheckForUpdates$5.<init>(AutomaticCheckForUpdates.java)
        at oracle.ideimpl.webupdate.AutomaticCheckForUpdates.checkMasterList(AutomaticCheckForUpdates.java:92)
        at oracle.ideimpl.webupdate.AutomaticCheckForUpdates.mav$checkMasterList(AutomaticCheckForUpdates.java:41)
        at oracle.ideimpl.webupdate.AutomaticCheckForUpdates$6.run(AutomaticCheckForUpdates.java:80)
        at java.lang.Thread.run(Thread.java:619)

my hostname file

localhost.localdomain mitjab-laptop

and hosts file

#localhost      localhost.localdomain localhost
192.168.2.171   mitjab.homelinux.net mitjab



i search for solution but i can not find id. Any idea?

thx

---

### Post by ekravche on 2007-12-08
Looks like you need to configure one admin account in oracle application server

---

### Post by mitjab on 2007-12-10
thx for your answer How can i do this?

---

