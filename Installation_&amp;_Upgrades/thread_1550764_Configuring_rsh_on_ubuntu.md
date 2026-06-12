---
title: "Configuring rsh on ubuntu"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by ubuntuv on 2010-08-11
Hi,

I am using ubuntu 10.04. I installed inetutils-inetd,rsh-server & rsh-client. Created user "user1".

disabled firewall using the command 
$ sudo ufw disable

$ su user1
$ cd ~
$ vi .rhosts
Entered ip address of another host and saved
$ chmod 600 .rhosts

Restarted the service by
$ sudo /etc/init.d/inetutils-inted restart

From other machine I typed 'rsh <ip> ls', it says

-----------
permission denied
cant' establish connection
-----------

When I issued 'tail -f /var/log/messages', I got no messages.

Please tell me, do I have to disable any other services to do this work.

Thanks
uv

---

