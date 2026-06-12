---
title: "FTP problem at shorewall"
date: 2006-03-19
forum: Installation &amp; Upgrades
---

### Post by robertoneto123 on 2006-03-19
Hello,

I got a Ubuntu gateway. On my network, I can use web, e-mail, ..., but no FTP.

On my gateway, if I try to do an FTP, it works fine. On a machine on my netwaork, I got:

230 User myuser logged in
ftp> ls
500 Illegal PORT command
425 Unable to build data connection: Connection refused

I can log in, but the only command that works is "bye" :).

Does anyone can solve this?

Thanks

---

### Post by davit on 2007-10-18
I am also trying to get the FTP pass-through working via Shorewall.

Have a XP box crossover wire to a Gutsy Gateway desktop/server with -> eth0 (loc) eth1 (net)->internet

all web, dns and ip routing working, but from the Xp and Server there is no internal or external FTP connection. :confused:

---

### Post by ruibernardo on 2007-10-18
You must load the FTP module for iptables in shorewall. This is done with a file named "modules" in you /etc/shorewall/ directory.

There is an example file of "modules" in /usr/share/doc/shorewall/default-config/modules

If you are satisfied about the modules you have loaded now (none?), just add
```
loadmodule nf_conntrack_ftp
```to an empty file named  /etc/shorewall/modules or copy the example file to /etc/shorewall/ directory and comment/delete all the lines and put only that one.

Then restart shorewall:

```
sudo shorewall restart
```

---

### Post by davit on 2007-10-19
I did not add the /etc/shorewall/modules file, (now I think its a good idea)

However, I did add the following to my
/etc/shorewall/rules 

```

FTP/ACCEPT	loc		$FW
FTP/ACCEPT	$FW		net 
```

and FTP from XP box seams to work with this as a basic format.

---

