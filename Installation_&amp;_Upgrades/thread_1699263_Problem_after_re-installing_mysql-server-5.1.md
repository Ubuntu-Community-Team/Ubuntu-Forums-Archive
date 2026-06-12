---
title: "Problem after re-installing mysql-server-5.1"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by Bobi86 on 2011-03-03
Hi all,
          I'm using Ubuntu 10.04 LTS - the Lucid Lynx.
I have reinstalled mysql-server-5.1 using the command "sudo apt-get --reinstall install mysql-server-5.1
". 
But its giving error message at the end of installation when its trying to start the server. 

The error message is as follows.
"Setting up mysql-server-5.1 (5.1.41-3ubuntu12.10) ...
110303 22:02:21 [Note] Plugin 'FEDERATED' is disabled.
110303 22:02:21  InnoDB: Started; log sequence number 0 44233
110303 22:02:21  InnoDB: Starting shutdown...
110303 22:02:23  InnoDB: Shutdown completed; log sequence number 0 44233
start: Job failed to start

Setting up libhtml-template-perl (2.9-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
balaji@ubuntu:
" 

When i tried to start the server after the installation, i get this error message
"balaji@ubuntu:/etc$ start mysql
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.57" (uid=1000 pid=2269 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
"

Note : The file "/etc/mysql/my.cnf" is empty. I'm not able to diagnose these issues.

Someone kindly do help me fix this issue.

Regards,
Balaji Radhakrishnan.

---

### Post by Bobi86 on 2011-03-06
No one there to help me sort this out?

---

