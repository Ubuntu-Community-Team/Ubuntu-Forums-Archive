---
title: "Can't stop powernapd on 16.04.1"
date: 2016-07-31
forum: Installation &amp; Upgrades
---

### Post by David_Partridge on 2016-07-31
After modifying the powernap service settings to be compatible with 16.04, I was able to start powernap OK

Unfortunately, it isn't possible to stop it!

```
root@Charon:/var/log# powernapd
root@Charon:/var/log# cat powernap.log
2016-07-30_15:34:19 INFO     Starting powernap
root@Charon:/var/log# ps -ef | grep powernap
root     12398     1  1 15:34 ?        00:00:00 /usr/bin/python /usr/sbin/powernapd
root     12602  4695  0 15:34 pts/1    00:00:00 grep --color=auto powernap
root@Charon:/var/log# kill 12398
root@Charon:/var/log# cat powernap.log
2016-07-30_15:34:19 INFO     Starting powernap
2016-07-30_15:34:46 INFO     Stopping powernap
root@Charon:/var/log# ps -ef | grep powernap
root     12398     1  0 15:34 ?        00:00:00 /usr/bin/python /usr/sbin/powernapd
root     12732  4695  0 15:35 pts/1    00:00:00 grep --color=auto powernap
root@Charon:/var/log#


```

As you can see it logs a message saying "Stopping powernap" when sent a signal, but doesn't go away!


 Cheers
Dave

---

### Post by David_Partridge on 2016-08-01
Bump

---

### Post by zeke2135 on 2016-12-06
Hello
This is a pretty old question, but in case you're still interested in an answer...
I found that for some reason in the script /usr/sbin/powerwake-now, powernap does not respond to kill -USR2. Instead I changed it to kill -KILL. I don't know if this is the proper thing to do, but it seems to work. 

Also just FYI, I noticed that for some reason a machine where I recently installed 16.04.1 does not like the fact that ethtool is in /sbin and not /usr/sbin. See /usr/share/powernap/powernap-ethtool. Powernap does not start w/ systemd, which says it can't find ethtool. My solution was to copy powernap-ethtool to /etc/powernap/ethtool-command and modify it to use the correct path for ethtool (and comment out the part where the script looks for /etc/powernap/ethtool-command). One could just modify powernap-ethtool in place. Or or maybe even just remove the ExecutePre line in the systemd unit file, unless wol is necessary.

---

