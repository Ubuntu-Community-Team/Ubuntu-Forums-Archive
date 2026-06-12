---
title: "After upgrade cannot connect to internet"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by BeginnerCsisz on 2010-08-29
Hi Ubuntu Users,
 
I recently installed Ubuntu, and begin to work with it, and I enjoy it so much. But: after a while I upgraded the 9.04 ubuntu to 9.10. I had a DSL connection, and I was able to connect to the internet before the upgrade, but after the upgrade I wasn't able to. I also have a windows installed, and I can connect to the internet from there. If I start the older kernel, I still cannot connect to the Internet. What can I do? What can cause the problem?
 
Thanks
BeginnerCsisz

---

### Post by carl4926 on 2010-08-29
What did you have to do originally to get it working in 9.04

---

### Post by BeginnerCsisz on 2010-08-29
I had to configure a DSL internet connection in the Network Manager. This DSL configuration didn't change after the upgrade, but the connection is not working...
 
BeginnerCsisz

---

### Post by carl4926 on 2010-08-29
Try deleting all connections in Network Manager and make a new one

---

### Post by BeginnerCsisz on 2010-08-29
I tried your tip, but it didn't worked. Can I configure a connection not in the network manager, but from terminal, or it is a stupid idea?
 
Thanks,
BeginnerCsisz

---

### Post by carl4926 on 2010-08-29
Please explain your connection more clearly.
DSL: What exactly is DSL in your case, give us details, make etc..

---

### Post by bacchusmarsh on 2010-08-29
search 'open dns' and follow the directions on their site. That fixes the problem on mine and my friends ubuntus.
It allows you to use an open source DNS to browse.

https:[//store.opendns.com/setup/device/ubuntu]("http://store.opendns.com/setup/device/ubuntu")

---

### Post by BeginnerCsisz on 2010-08-29
> **carl4926 said:**
> Please explain your connection more clearly.
DSL: What exactly is DSL in your case, give us details, make etc..
 
Away for a while, but back. Tried to run the internet configuration method on the following link (1st step, the instructions are in hungarian, but the commands are international:))):
 
[http://rontogyula.blog.hu/2008/07/09/teljes_ubuntu_linux_beallitas_a_kezdetektol](http://rontogyula.blog.hu/2008/07/09/teljes_ubuntu_linux_beallitas_a_kezdetektol)
 
I got the following error message in terminal:
 
```
root@csiszgab-desktop:~# sudo pppoeconf
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
root@csiszgab-desktop:~# plog
Aug 30 01:05:44 csiszgab-desktop pppd[2249]: Connect: ppp0 <--> eth0
Aug 30 01:05:47 csiszgab-desktop pppd[2249]: PAP authentication succeeded
Aug 30 01:05:47 csiszgab-desktop pppd[2249]: peer from calling number 00:21:55:13:38:1A authorized
Aug 30 01:05:47 csiszgab-desktop pppd[2249]: Cannot determine ethernet address for proxy ARP
Aug 30 01:05:47 csiszgab-desktop pppd[2249]: local IP address 81.182.117.138
Aug 30 01:05:47 csiszgab-desktop pppd[2249]: remote IP address 145.236.238.175
Aug 30 01:05:47 csiszgab-desktop pppd[2249]: primary DNS address 84.2.44.1
Aug 30 01:05:47 csiszgab-desktop pppd[2249]: secondary DNS address 84.2.46.1
root@csiszgab-desktop:~# exit
exit
csiszgab@csiszgab-desktop:~$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
csiszgab@csiszgab-desktop:~$ plog
Aug 30 01:06:51 csiszgab-desktop pppd[2294]: PAP authentication succeeded
Aug 30 01:06:51 csiszgab-desktop pppd[2294]: peer from calling number 00:21:55:13:38:1A authorized
Aug 30 01:06:52 csiszgab-desktop pppd[2294]: not replacing existing default route through ppp0
Aug 30 01:06:52 csiszgab-desktop pppd[2294]: Cannot determine ethernet address for proxy ARP
Aug 30 01:06:52 csiszgab-desktop pppd[2294]: local IP address 81.182.116.219
Aug 30 01:06:52 csiszgab-desktop pppd[2294]: remote IP address 145.236.238.175
Aug 30 01:06:52 csiszgab-desktop pppd[2294]: primary DNS address 84.2.46.1
Aug 30 01:06:52 csiszgab-desktop pppd[2294]: secondary DNS address 84.2.44.1
csiszgab@csiszgab-desktop:~$ ^C
csiszgab@csiszgab-desktop:~$ 

```
 
Can anybody please translate me what the message means?
 
During the system upgrade, several programs have been removed - may be this is the reason I lost the internet connection?
 
Thanks,
BeginnerCsisz

---

### Post by dineshs on 2010-08-30
> Can anybody please translate me what the message means?
You are connected.You should be able to browse.(Assuming the DNS servers 84.2.44.1 and 84.2.46.1 are working)
by the way If you are using Network Manager avoid pppoeconf.Try DSL tab.But in your case it is not working.Maybe due to Bug
[http://ubuntuguide.net/fix-dsl-pppoe-connection-problem-with-network-manager-in-ubuntu-9-10](http://ubuntuguide.net/fix-dsl-pppoe-connection-problem-with-network-manager-in-ubuntu-9-10)
So what I suggest is try to confogure modem in PPPoE mode if it supports

---

### Post by BeginnerCsisz on 2010-08-30
Thanks,

That comment was helpful. It explains my problem though I reinstalled the whole Ubuntu because I run some applications, which caused the Network Manager to crash:))) (I wasn't even able to try to run a network connection).

Regards,
BeginnerCsisz

---

