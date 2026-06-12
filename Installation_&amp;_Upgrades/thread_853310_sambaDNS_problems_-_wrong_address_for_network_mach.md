---
title: "samba/DNS problems - wrong address for network machines"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by jeffrey1681 on 2008-07-08
I am running 7.10, installed initially from the Live CD for Restore ([http://restore-backup.com/](http://restore-backup.com/)).  However, I was unable to get restore to work, so I am now just using it as an ubuntu server (I think the CD is just 7.10 with the restore package included).  

My problem is that the DNS resolution for machines on my local network is messed up, which leaves me unable to mount them as samba drives (so that I can back them up from the server).  For example, if I run nslookup, I get the following:

$> nslookup miriam
Server:         68.237.161.12
Address:        68.237.161.12#53

Non-authoritative answer:
Name:   miriam
Address: 63.251.179.13
Name:   miriam
Address: 8.15.7.117

miriam is a computer on the local network and should have an ip address of the form 192.168.0.*.  I have no idea where the other addresses are coming from, though it definitely looks like my DNS settings are messed up somewhere.  Hopefully someone will be able to help me (or at least point me in the right direction), as the only other option I can think of is to format and reinstall with 8.04 and hope that the problems disappear.  I've tried searching online and on these forums without any luck.  Thanks.

---

