---
title: "k3b doesn't start"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by mitjab on 2007-04-25
```

mitjab@localhost:~$ k3b
/usr/bin/iceauth: /tmp/dcopPfMg8b:1:  bad "add" command line
/usr/bin/iceauth: /tmp/dcopPfMg8b:2:  bad "add" command line
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
ICE Connection rejected!

kdeinit: DCOPServer could not be started, aborting.
ERROR: KUniqueApplication: Can't setup DCOP communication.
mitjab@localhost:~$ 


```

what is wrong?

---

### Post by mitjab on 2007-04-26
can someone help me with tjis problem?

---

### Post by mitjab on 2007-05-03
anyone has similar problem?

---

### Post by leumicard on 2007-05-26
K3b his made for KDE you need kde to start K3b

---

### Post by Pumalite on 2007-05-27
> **leumicard said:**
> K3b his made for KDE you need kde to start K3b

Your problem is DCOPserver and .ICEauthority file. Do a little googling on them and you will find your answer. K3b can run in Gnome BTW.

---

### Post by Robi400 on 2007-06-03
Hi,
i have the same Problem
on k3b, on Rosegarden, on Amarok and other KDE programms.
i have reinstall all of them, it don't help
i have searched for .ICEauthority but i found nothing information that help.
please, whoever now somthing, give me a help
if i try to start dcopserver  with sudo i get the following error
 
sudo dcopserver
/usr/bin/iceauth: /tmp/dcopPfMg8b:1:  bad "add" command line
/usr/bin/iceauth: /tmp/dcopPfMg8b:2:  bad "add" command line
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
ICE Connection rejected!

thank's for any idea
Robi400

---

### Post by mlissner on 2007-06-09
I just did rm ~/.DCOPserver...

And my problems were fixed. I'm running edgy though, so who knows...

---

