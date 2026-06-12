---
title: "Cannot ssh to other computer"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by polka on 2006-06-22
I did an install with the alternate iso (6.06) and it went well, but I cannot ssh to my other computer.
Computer A (running linux) can ping and ssh into computer B (running Kubuntu), but computer B cannot ping or ssh into A. B can ping localhost and ssh into itself. This tells me that both NICs are working and the connection works. I am on a dialup modem and can access the net on B.  
I am a member of the ssh group and ran "sudo /etc/init.d/ssh restart" without error.

jerry@backup:/etc/ssh$ ssh jerry@main -v
OpenSSH_4.2p1 Debian-7ubuntu3, OpenSSL 0.9.8a 11 Oct 2005
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Connecting to main [192.168.1.50] port 22.


ssh hangs there. If I run "echo $?' immediately afterwards I get:
jerry@backup:/etc/ssh$ echo $?
130

I know 0 means command executed properly and any other number is an error. I don't remember where to locate the list of error codes.

I did install openssh-server because I compared the files on the 2 computers and it was not present on B. I also could not ssh into B when it was not installed.

/var/log/auth.log says:
Jun 22 02:41:35 localhost sudo:    jerry : TTY=pts/1 ; PWD=/etc/ssh ; USER=roo
t ; COMMAND=/etc/init.d/ssh restart
Jun 22 02:41:35 localhost sshd[7002]: Received signal 15; terminating.
Jun 22 02:41:35 localhost sshd[7070]: Server listening on :: port 22.
Jun 22 02:42:23 localhost sshd[7076]: Accepted password for jerry from 192.168
.1.50 port 38894 ssh2
Jun 22 02:42:23 localhost sshd[7078]: (pam_unix) session opened for user jerry
 by (uid=0)
Jun 22 02:42:28 localhost sshd[7078]: (pam_unix) session closed for user jerry
(END)

The first line   is where I restarted ssh.
I don't know what happened on line 2. (signal 15)
I sshed from A (192.168.1.50) and closed the connection.
I tried to ssh from B to A but there is nothing in auth.log.

I would appreciate any help to get ssh working.
Thanks

---

### Post by simonn on 2006-06-22
Is port 22 open on computer A?

---

### Post by polka on 2006-06-23
Before I installed Kubuntu on B I could ssh both directions.

I am not sure how to check which ports are open. What is the command to check open ports?

Thanks   for your  response

---

