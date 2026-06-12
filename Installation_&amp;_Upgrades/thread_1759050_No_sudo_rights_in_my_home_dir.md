---
title: "No sudo rights in my home dir?"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by ~Gh05t~ on 2011-05-15
Hello together, 
i have set up my ubuntu 11.04 client to fetch everything from my 10.04 LTS server: 
Users from LDAP, Homedirectories with NFS4 using autofs (from LDAP, too).

Ive used [that]("https://help.ubuntu.com/community/LDAPClientAuthentication") tutorial to set up PAM-LDAP, in simply words i installed ldap-auth-client and set up nss config.

Unfortunately i can not access files in my home dir (nfs mount) with sudo, all other locations outside my home dir are valid:
```

$ sudo touch ~/test.txt
touch: can not touch test.txt: Permission denied
$ touch ~/test.txt
--> works!
$ sudo touch /root/test.txt
--> works!
$
```
Any ideas about that? Iam in the "admin" group on my ldap.

---

### Post by dino99 on 2011-05-15
seems you have to file the full path to get it working

---

### Post by lechien73 on 2011-05-15
Is your home folder exported using the no_root_squash option? You can check this in the /etc/exports file on your server.

It's vital, however to read up on the potential security risks of switching off root squashing before you do, though. It seems to me that the behaviour you are describing for a remote-mounted NFS share is correct, and I would not advise exporting an NFS share without root squashing enabled.

---

### Post by ~Gh05t~ on 2011-05-15
> **lechien73 said:**
> Is your home folder exported using the no_root_squash option? You can check this in the /etc/exports file on your server.

It's vital, however to read up on the potential security risks of switching off root squashing before you do, though. It seems to me that the behaviour you are describing for a remote-mounted NFS share is correct, and I would not advise exporting an NFS share without root squashing enabled.
Yeah, i think that was it. Thank you!

---

