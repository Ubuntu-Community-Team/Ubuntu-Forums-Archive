---
title: "can not start k3b"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by mitjab on 2007-06-10
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

i see this bug report but no solution yet.
[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/102532](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/102532)

can someone help me?

---

### Post by floke on 2007-06-10
does 'sudo k3b' work?

I used to have to do this...

---

### Post by mitjab on 2007-06-11
no the same

---

### Post by stchman on 2007-06-11
> **mitjab said:**
> mitjab@localhost:~$ k3b
/usr/bin/iceauth: /tmp/dcopPfMg8b:1:  bad "add" command line
/usr/bin/iceauth: /tmp/dcopPfMg8b:2:  bad "add" command line
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
ICE Connection rejected!

kdeinit: DCOPServer could not be started, aborting.
ERROR: KUniqueApplication: Can't setup DCOP communication.

i see this bug report but no solution yet.
[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/102532](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/102532)

can someone help me?

Try uninstalling and reinstalling K3B.  Sounds like it is corrupted.

---

### Post by Detonate on 2007-06-17
I'm having the same problem.  I reinstalled k3b.  Still doesn't work.  Locks up my computer, I get the dcopserver error message when I try to run it from the command line.  I've done some google work on this, but did not find any really good answers.  I tried deleting the .DCOPserver  files in my home folder.  they came back exactly the same.  When I reinstalled, I first used aptitude with the purge option so it removed all of the configuration files.  So I had a clean install.  Still have the problem.  Note that k3b runs fine on Fedora 7, KDE 3.5.6 on the same computer.

Using KDE 3.5.7 and k3b  1.0.

---

### Post by Pumalite on 2007-06-17
> **Detonate said:**
> I'm having the same problem.  I reinstalled k3b.  Still doesn't work.  Locks up my computer, I get the dcopserver error message when I try to run it from the command line.  I've done some google work on this, but did not find any really good answers.  I tried deleting the .DCOPserver  files in my home folder.  they came back exactly the same.  When I reinstalled, I first used aptitude with the purge option so it removed all of the configuration files.  So I had a clean install.  Still have the problem.  Note that k3b runs fine on Fedora 7, KDE 3.5.6 on the same computer.

Using KDE 3.5.7 and k3b  1.0.

Sometimes deleting the file /.ICEauthority works. That happened to me in the past and that's how I solved. When you reboot, the system builds the file again, and then k3b works! It all has to do with a socket that is otherwise unavailable.

---

### Post by Detonate on 2007-06-17
Thank you.  I deleted the DCOPserver files and the .ICEauthority file and now it's working.

---

