---
title: "Can Somebody help me?"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by cheepeng on 2008-10-11
i'm a currently a University student, i'm taking physic course. Besides, i'm also a beginner of LINUX.

The problem occurs in my computer is...

now i have a simulation about parallel virtual machine, using computers to measure the current and charge of a material of semiconductor... i have connected to 8 computer (7 slave, 1 master) as a research base. By following the construction of installation, i have install Red Hat LINUX version 7.3 in my computer. The problem is i can't connect the master computer with others 7 slave computer. Once i start up the others 7 slave computer, this message will show...

Mounting NFS filesystems: mount: RPC: Port Mapper Failure: unable to receive

I have no idea with this message...Besides, when i start up my master computer, and i get in to PVM:-

[root@master]# pvm
pvm> add fizlan01

Successfull 0       can't start pvmd
Rsh/Rhosts access failed-'poll': protocol failure in current setup
Auto-diagnosing failed hosts....fizlan01
verifying local path to "rsh"...
Rsh found in /usr/bin/rsh  - 0.K.
Testing Rsh/Rhosts access to host "fizlan01"
Rsh/Rjosts access is O.K.
Checking O.S. Type(unix test)) on host "fizlan01"
Host fizlan01 is unix-based
checking $PVM_Root on host "fizlan01"
The value of the $PVM_Root environment variables on fizlan01 is invalid
use the absolute path to the pvm3/directory

pvm>

Hope can somebody help me in troubleshooting this problem...thank  s a lot...:(

---

