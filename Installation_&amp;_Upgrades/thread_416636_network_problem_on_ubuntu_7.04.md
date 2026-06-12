---
title: "network problem on ubuntu 7.04"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Piviul on 2007-04-21
Hi all, 
I've just upgraded to ubuntu 7.04; all seems works good excepts the netowk: I can browse only google. I can't reach any other site from the browser, I can't reach any pop mail, I can't reach the repository for updating my distribution. I know, sounds strange but that's true. For example I can ping the repository site I have in /etc/apt/sources.list, but I can't connect to them, I can ping my pop mail but thunderbird can't contact it, I can ping an http site but firefox can't browse it (except google as I've said). 

Someone have an idea where is the problem and how can I solve it?

Perhaps some more information can be usefull.

I have no iptables rule:
> 
antonella@antonella-desktop:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


This is my routing table
> 
antonella@antonella-desktop:~$ sudo route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.30.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.30.1    0.0.0.0         UG    0      0        0 eth0


When I try to update my system from the shell prompt I can see
> 
antonella@antonella-desktop:~$ sudo aptitude update
0% [Accesso in corso]

but never more happens. I have to type Ctrl-C to break the command.

This is my sources.list
```

antonella@antonella-desktop:~$ cat /etc/apt/sources.list | grep ^deb
deb ftp://na.mirror.garr.it/mirrors/ubuntu-archive/ feisty main restricted multiverse universe
deb ftp://na.mirror.garr.it/mirrors/ubuntu-archive/ feisty-updates main restricted multiverse universe
deb ftp://na.mirror.garr.it/mirrors/ubuntu-archive/ feisty-security main restricted multiverse universe

```

So I've tried to connet via ftp to the server:
```

antonella@antonella-desktop:~$ ftp na.mirror.garr.it
Connected to na.mirror.garr.it.
220 ProFTPD 1.2.10 Server (Debian) [193.206.140.37]
Name (na.mirror.garr.it:antonella): anonymous
331 Anonymous login ok, send your complete email address as your password.
Password:
230-Welcome, archive user anonymous@host231-30.pool8250.interbusiness.it !
230-

```
and no more messages are displayed and I have to press Ctrl-C...

Then I've changed the repository and I've selected the other italian one in http and I have tried to download Release.gpg
```

antonella@antonella-desktop:~$ wget http://ubuntu.fastbull.org/ubuntu/dists/feisty/Release.gpg
--19:05:01--  http://ubuntu.fastbull.org/ubuntu/dists/feisty/Release.gpg
           => `Release.gpg'
Risoluzione di ubuntu.fastbull.org in corso... 194.116.84.5
Connessione a ubuntu.fastbull.org|194.116.84.5:80... connesso.
HTTP richiesta inviata, aspetto la risposta... 

```
and I have to press Ctrl-C once more...

And I'm very confused: I can't understand how to solve or only understand the problem...

Piviul

---

### Post by Piviul on 2007-04-22
I've found the problem: there is an incompatibility with my router and I've moved this thread to networking and wireless ([http://ubuntuforums.org/showthread.php?t=418144]("http://ubuntuforums.org/showthread.php?t=418144"))

Piviul

---

