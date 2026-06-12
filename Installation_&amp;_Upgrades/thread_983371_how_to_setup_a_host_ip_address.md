---
title: "how to setup a host ip address"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by Surendra on 2008-11-15
Hi i am new to unix,
I installed ubuntu on my virtual pc. Everything went fine. But i am not able to access this server from another computer through putty.

i added  /etc/hosts

cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ubuntu

172.18.0.1 bollu.com

and restart networking, when i restart network, i am getting below message

sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
postconf: fatal: open /etc/postfix/main.cf: No such file or directory

Can anybody let me know how fix these.
1. I need setup hostname and static ipaddress 
2. I need access this server through ssh (putty) from another.
3. i didn't find main.cf under /etc/postfix.

Thanks in Advance
Surendra

---

### Post by rebel789 on 2008-11-15
Get cool freestuff at
[http://www.prizerebel.com/index.php?r=487360](http://www.prizerebel.com/index.php?r=487360)

---

