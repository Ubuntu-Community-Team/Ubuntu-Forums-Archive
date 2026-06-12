---
title: "postgresql-8.1 isn't listening"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by likes2skate on 2007-09-09
I need a new SQL server so I installed postgresql-8.1 on ubuntu 6.06.  The IP address of the new server is 192.168.0.188.

Postgresql 8 is a major upgrade from version 7.  The ubuntu server guide covers version 7, and key configuration file details are different, so the guide is not a big help.

[http://doc.ubuntu.com/ubuntu/serverguide/C/postgresql.html](http://doc.ubuntu.com/ubuntu/serverguide/C/postgresql.html)

I turned the firewall off for troubleshooting.

On the server, postgresql is working; I can connect from my user account no problem.

But postgresql-8.1 isn't listening to computers on the local network.  For example, from my workstation:

[INDENT]$psql -h 192.168.0.188 -d template1
 psql: could not connect to server: Connection refused
        Is the server running on host "192.168.0.188" and accepting
        TCP/IP connections on port 5432?
[/INDENT]

On the server, I put this line in pg_hba.conf:

[INDENT]host    all         all         192.168.0.1/16        trust[/INDENT]

I put these two lines in postgresql.conf:

[INDENT]listen_addresses = '*'
port = 5432[/INDENT]


From my workstation, nmap says postgresql is not listening:

[INDENT]$nmap -v -p1-5888 192.168.0.188

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-09-09 15:59 ICT
...
Scanning 192.168.0.188 [5888 ports]
Discovered open port 22/tcp on 192.168.0.188
Completed Connect() Scan at 15:59, 3.74s elapsed (5888 total ports)
Host 192.168.0.188 appears to be up ... good.
Interesting ports on 192.168.0.188:
Not shown: 5887 closed ports
PORT   STATE SERVICE
22/tcp open  ssh

Nmap finished: 1 IP address (1 host up) scanned in 4.817 seconds
[/INDENT]

In the root account of the server, I ran netstat:

[INDENT]netstat -ae | grep tcp | grep LIST
tcp  0 0 localhost:postgresql *:* LISTEN postgres 8303
tcp6 0 0 *:ssh                *:* LISTEN root     8382
[/INDENT]

I would appreciate any help to get this server to listen.

Thanks,

---

### Post by pheeror on 2007-09-09
If you look at netstat output, you can see postgresql is listening only on localhost. Change  listen_addresses directive in postgresql.conf. However, listen_addresses="*" looks good. Does postgresql use that configuration file? Did you restart postgresql server?

---

### Post by likes2skate on 2007-09-10
pheeror,

> Does postgresql use that configuration file? 

That is from the file in the data directory.  How do I tell which configuration file postgresql is reading?

> Did you restart postgresql server?

Over and over.  Also rebooted several times.

Thanks,

---

### Post by likes2skate on 2007-09-10
pheeror,

> Does postgresql use that configuration file?
 
Thanks for the clue; I found the problem.

The conf files you are supposed to edit are here:

/etc/postgresql/8.1/main

They are buried so deeply, I instead found the decoy copies that the installation put in my data directory.  

In an ideal world, if they are going to plant decoy copies of the configuration files in a location an administrator is likely to find, with the decoy copies should be a README that tells were the real conf files are located.  

So in the files in /etc/postgresql/8.1/main, I made the changes that I described, and now postgresql-8.1 is listening.

Thanks,

---

