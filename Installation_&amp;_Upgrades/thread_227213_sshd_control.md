---
title: "sshd control"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by david_ts on 2006-08-01
Hi,
I accindetaly deleted /etc/inet.d/ssh script #-o 
so I do not have control over sshd deamon now.
i.e. I cannot /etc/inet.d/ssh restart  
I've then downloaded openssh (latest version Portable OpenSSH 4.3p2 ) from [http://www.openssh.com/](http://www.openssh.com/)
ssh seems to be running but neither incoming nor outgoing connections work. for remote access it says "connection time out". It seems to me sshd is not actually running?
I've tried the obvious things like 
sudo apt-get install ssh
and sudo apt-get install openssh-server
that didn't help either.
Little help, someone? ;) 
Thanks.
David

BTW, Ubuntu was the only OS that could recongnize bleeding -edge technology such as latest Intel Server Board S5000PSL and SCSCI hard disks, so Unbuntu rocks! Very nice operating system and more over, these Ubuntu forums are truly helpful! well done!

---

### Post by gborzi on 2006-08-01
I think a > sudo apt-get install --reinstall openssh-server
will do the task. Otherwise, copy the ssh file from my computer to /etc/init.d .

---

