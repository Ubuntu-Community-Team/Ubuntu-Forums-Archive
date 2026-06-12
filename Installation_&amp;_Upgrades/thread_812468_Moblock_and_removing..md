---
title: "Moblock and removing."
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by schnoodles on 2008-05-29
Hello i installed Moblock but now every time i try to use any aptitude function it runs moblock and i get a 

```
tail -f /var/log/moblock-control.log
Stopping MoBlock                                                         [fail]
2008-05-30 02:15:03 JST End: moblock-control stop
2008-05-30 11:44:06 JST Begin: moblock-control start
 * Error 7: Missing file /etc/moblock/guarding.p2p.
 * Check the BLOCKLIST settings in /etc/moblock/moblock.conf.
 * Also check /etc/default/moblock.
2008-05-30 11:48:32 JST Begin: moblock-control reload
Building blocklist *  Error 9: There are no blocklists! Aborting.
2008-05-30 11:48:32 JST Begin: moblock-control update
 * Error 171: No connection to www.bluetack.co.uk. Aborting!

```

at the end of the aptitude process.

Due to this error i cant even uninstall moblock.

Does anyone have any idea on how i can uninstall moblock ?

---

### Post by iaculallad on 2008-05-29
Try relating to this [Moblock Uninstall Error]("http://ubuntuforums.org/showthread.php?t=674929") thread.

---

### Post by schnoodles on 2008-05-29
Ive had a look at that, but none of that seems to help me.

It seems to happen because when i do moblock-control stop. it fails. And i dont have a clue why it fails :\

---

### Post by iaculallad on 2008-05-30
> **schnoodles said:**
> Ive had a look at that, but none of that seems to help me.

It seems to happen because when i do moblock-control stop. it fails. And i dont have a clue why it fails :\

Did you try using sudo?

Code:

```
sudo moblock-control stop
```

---

### Post by schnoodles on 2008-05-30
Yes i did try and use sudo. that is why i find it so wierd that it fails.

---

### Post by schnoodles on 2008-05-30
```
2008-05-30 21:37:38 JST Begin: moblock-control stop
Deleting iptablesiptables v1.3.8: Couldn't load target `moblock_in':/lib/iptables/libipt_moblock_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_out':/lib/iptables/libipt_moblock_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_fw':/lib/iptables/libipt_moblock_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: Bad rule (does a matching rule exist in that chain?)
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
 * Some iptables rules could not be deleted. The most common reason for this is
 * that they did not exist. If MoBlock was not running this is the correct
 * behaviour. But if MoBlock was running there is some problem. Make sure that
 * MoBlock inserts its iptables rules correctly and that other software, e.g.
 * firewall applications, don't delete them. Make sure that MoBlock is started
 * after other firewall applications.
Stopping MoBlock                                                        [fail]
2008-05-30 21:37:38 JST End: moblock-control stop
```

That seems to happen when i say stop. I dont seem to be able to find the moblock_*.so files and i cant seem to find them :\

---

### Post by jre on 2008-05-30
> **schnoodles said:**
> I dont seem to be able to find the moblock_*.so files and i cant seem to find them :\
This jsut relates to the iptables rules, but aren't any files.

Indeed not very informative why it fails to stop.

What do you get on [FONT="Courier New"]moblock-control status[/FONT] and what on [FONT="Courier New"]start[/FONT] (console output and logfile)?
Which version do you use (dpkg --list moblock)?

Try as a quick fix for aptitude (but you still won't have a working moblock):
```
sudo touch /etc/moblock/guarding.p2p
```
This creates an empty blocklist file.

---

### Post by schnoodles on 2008-05-31
Hey here are my results i get back

> josh@schnootop:~/workspace$ sudo moblock-control status
[sudo] password for josh: 
Current iptables rules (this may take awhile):

Chain INPUT (policy ACCEPT 25676 packets, 25M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 23938 packets, 2754K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Please check if the above printed iptables rules are correct!

 * moblock is not running.


> 2008-05-31 15:28:34 JST Begin: moblock-control start
 * Error 7: Missing file /etc/moblock/guarding.p2p.
 * Check the BLOCKLIST settings in /etc/moblock/moblock.conf.
 * Also check /etc/default/moblock.


Although, touching that .p2p file seemed to make it all work pretty nicely. Lets me delete the whole of moblock and also start and stop it. Looked like that was my only problem not having that file.

Thankyou jre :)

---

### Post by jre on 2008-05-31
> **schnoodles said:**
> Looked like that was my only problem not having that file.
I still fear that there was some bug because the stop failed. For now I changed moblock-control to do only really necessary tests for valid variables when it stops. This way we avoid an refusal to stop if moblock is misconfigured.

Glad I could help anyway
jre

---

