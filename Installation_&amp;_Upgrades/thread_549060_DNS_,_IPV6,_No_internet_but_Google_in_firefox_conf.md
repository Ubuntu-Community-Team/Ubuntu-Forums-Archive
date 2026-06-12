---
title: "DNS , IPV6, No internet but Google in firefox configuration problem"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by iloveketchup on 2007-09-12
Hi,

I'm using VMware on a windows xp box however i think that has little or nothing to my problem.  I can only connect to google pages within firefox.  

[LIST]
[*]i can get to **google based pages** in firefox using google.com, gmail.com ...
[*]I can use **gaim** without problem.
[*]i get an ip from my router
[*]i **can ping **opendns.org dns servers
[*]my /etc/resolv.conf file seems to be okay.  I just put in the 2 opendns.org ip's for nameservers
[*]i  changed /modprobe.d/aliases  (alias net -pf -0 ipv6) to (alias net -pf -0 **off**)
[*]in firefox i toggled "network.dns.disableIPV6" value to "**true**" from "false".  This should disable IPV6 in firefox.  I got there by typing in "about:config" in the url box and using the "filter"
[/LIST]

I don't know exactly what to check.  This is a fresh install of ubuntu.  i didn't see anything in the installer that i could have removed these options.  I don't seem to be able to use the apt-get feature because of this mess.  I can't believe that on a fresh install that i get this problem.  It's kind of rediculous.  Could my parents ever install this and use it as a primary OS?  

[-X

Thanks for any help in advance.

-Kenny

I've read these links in my search of the problem:

Disabling IPV6 in /etc/modprobe.d/aliases

[http://www.linuxquestions.org/questions/showthread.php?t=326645](http://www.linuxquestions.org/questions/showthread.php?t=326645)

Install problem - hangs when scanning mirrors.

[http://ubuntuforums.org/showthread.php?t=209617](http://ubuntuforums.org/showthread.php?t=209617)

This is due to a default mirror not being available anymore.

disabling IPv6 in firefox:

[http://ubuntu-tutorials.com/2006/10/20/how-to-speed-up-firefox-or-flock-ubuntu-606-610/](http://ubuntu-tutorials.com/2006/10/20/how-to-speed-up-firefox-or-flock-ubuntu-606-610/)

---

### Post by cursebg on 2007-09-12
> **iloveketchup said:**
> Hi,

I'm using VMware on a windows xp box however i think that has little or nothing to my problem.  I can only connect to google pages within firefox.  

[LIST]
[*]i can get to **google based pages** in firefox using google.com, gmail.com ...
[*]I can use **gaim** without problem.
[*]i get an ip from my router
[*]i **can ping **opendns.org dns servers
[*]my /etc/resolv.conf file seems to be okay.  I just put in the 2 opendns.org ip's for nameservers
[*]i  changed /modprobe.d/aliases  (alias net -pf -0 ipv6) to (alias net -pf -0 **off**)
[*]in firefox i toggled "network.dns.disableIPV6" value to "**true**" from "false".  This should disable IPV6 in firefox.  I got there by typing in "about:config" in the url box and using the "filter"
[/LIST]

I don't know exactly what to check.  This is a fresh install of ubuntu.  i didn't see anything in the installer that i could have removed these options.  I don't seem to be able to use the apt-get feature because of this mess.  I can't believe that on a fresh install that i get this problem.  It's kind of rediculous.  Could my parents ever install this and use it as a primary OS?  

[-X

Thanks for any help in advance.

-Kenny

I've read these links in my search of the problem:

Disabling IPV6 in /etc/modprobe.d/aliases

[http://www.linuxquestions.org/questions/showthread.php?t=326645](http://www.linuxquestions.org/questions/showthread.php?t=326645)

Install problem - hangs when scanning mirrors.

[http://ubuntuforums.org/showthread.php?t=209617](http://ubuntuforums.org/showthread.php?t=209617)

This is due to a default mirror not being available anymore.

disabling IPv6 in firefox:

[http://ubuntu-tutorials.com/2006/10/20/how-to-speed-up-firefox-or-flock-ubuntu-606-610/](http://ubuntu-tutorials.com/2006/10/20/how-to-speed-up-firefox-or-flock-ubuntu-606-610/)

lol man, I had this problem on my PPTP connection, too. You have set a smaller number for MTU  ( Maximum Transmittion Unit) for yur connection. If you don't know what I'm talking about just tell me what type is you connection and I'll ya what config files to edit ;) 

Hope you see this soon as I'm not having much time to hang around here :)

---

### Post by iloveketchup on 2007-09-12
connection type?  well it's a wired connection.  i think the MTU is supposed to be like 1500 but i'm not sure where to check yet.

---

### Post by iloveketchup on 2007-09-12
> **cursebg said:**
> lol man, I had this problem on my PPTP connection, too. You have set a smaller number for MTU  ( Maximum Transmittion Unit) for yur connection. If you don't know what I'm talking about just tell me what type is you connection and I'll ya what config files to edit ;) 

Hope you see this soon as I'm not having much time to hang around here :)

also:

eth0      Link encap:Ethernet  HWaddr 00:0C:29:21:50:39  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6054 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1099 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1215143 (1.1 MiB)  TX bytes:105055 (102.5 KiB)
          Interrupt:16 Base address:0x2000 


it says my MTU size is 1500.  this seems pretty normal.

---

