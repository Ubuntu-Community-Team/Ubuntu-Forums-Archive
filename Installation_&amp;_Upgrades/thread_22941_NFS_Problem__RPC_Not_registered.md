---
title: "NFS Problem : RPC Not registered"
date: 2005-03-30
forum: Installation &amp; Upgrades
---

### Post by ericb on 2005-03-30
Hi All !
I installed nfs on my ubuntu box (apt-get install kernel-nfs-server or something like that), edited /etc/exports, restarted nfs, and it didn't worked as expected :

on the ubuntu server, when trying to mount -t nfs localhost:/something /test
it works

however, when 
mount -t nfs imac.local:/something /test

I got error : RPC not registered,
looks like nfs is only listening lo...

it's not an interface problem or a dns problem, host imac.local reports 192.168.5.11, and ifconfig reports eth0 is up at 192.168.5.11 ...  strange...
...

ps -A report portmap is running, nfsd and mountd
beside, rpcinfo don't exists on this system and apt-cache search rpcinfo reported nothing !!

anyone can help ??

---

### Post by dragev on 2005-04-10
I have exactly same problem with ubuntu 5.04.
Did you find a solution ?

---

### Post by kleeman on 2005-04-10
Try this troubleshooter:

[http://nfs.sourceforge.net/nfs-howto/troubleshooting.html](http://nfs.sourceforge.net/nfs-howto/troubleshooting.html)

---

### Post by dragev on 2005-04-10
seems like theres only portmap innstalled and running on my system.
so i guess finding a nice nfs server is the way to go.

any tips ?

---

### Post by byronsalty on 2005-06-19
[QUOTE=dragev]I have exactly same problem with ubuntu 5.04.
Did you find a solution ?[/QUOTE]
 I got the same error message. My steps to fix were:

Make sure 'nfs' and 'autofs' were on both server and client (don't know if both were necessary but hey - it worked). To check this run:
lsmod | grep fs

If not run: modprobe -i nfs autofs

After that I restarted networking on the client and restarted /etc/init.d/nfs-kernel-server on the server.

---

### Post by cubeice24 on 2006-04-26
I'm running Hoary and here's the list of things I did on my server machine in order to get a succesful mount:
1)apt-get-installed portmapper, nfs-common and nfs-kernel-server
2)edited /etc/exports : /home/ez/Shared 139.8.8.25(rw)
3)restarted the following services:
   /etc/init.d/portmap restart
   /etc/init.d/nfs-common restart
   /etc/init.d/nfs-kernel-server restart


[QUOTE=ericb]Hi All !
I installed nfs on my ubuntu box (apt-get install kernel-nfs-server or something like that), edited /etc/exports, restarted nfs, and it didn't worked as expected :

on the ubuntu server, when trying to mount -t nfs localhost:/something /test
it works

however, when 
mount -t nfs imac.local:/something /test

I got error : RPC not registered,
looks like nfs is only listening lo...

it's not an interface problem or a dns problem, host imac.local reports 192.168.5.11, and ifconfig reports eth0 is up at 192.168.5.11 ...  strange...
...

ps -A report portmap is running, nfsd and mountd
beside, rpcinfo don't exists on this system and apt-cache search rpcinfo reported nothing !!

anyone can help ??[/QUOTE]

---

