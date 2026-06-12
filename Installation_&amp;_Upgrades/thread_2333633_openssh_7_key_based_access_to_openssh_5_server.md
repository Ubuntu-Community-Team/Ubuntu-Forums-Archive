---
title: "openssh_7 key based access to openssh_5 server"
date: 2016-08-11
forum: Installation &amp; Upgrades
---

### Post by dkoleary on 2016-08-11
Hey;

I just upgraded my ubuntu laptop to ubuntu 16.04 which went very smoothly as all previous updates have.  Openssh_7 turned off support for DSA keys so I'm off to create a new RSA key for myself.  I generated the key pair and can use it to access accounts on my laptop w/o issue; however, I cannot access a Centos 6.8 system running openssh_5.3.  The key isn't being accepted:

```
$ ssh -i ./id_rsa fw
Permission denied (publickey,gssapi-keyex,gssapi-with-mic).

```
Permissions are set correctly as proven by the fact that I can access accounts locally w/o issue:

```
$ ssh localhost hostname
Enter passphrase for key '/home/dkoleary/.ssh/id_rsa': 
oleary1

```
I suspect it's a difference in the key encryption as the key fingerprint on the openssh_7 system doens't look the same as it does on the openssh_5 box:

```
$ ssh-keygen -lf ./id_rsa
2048 SHA256:OWiBtrNCcrw3w4dHsT81R5UNpf6D618XzyGgK8OWXfc dkoleary@oleary1 (RSA)
$ exit
Connection to 192.168.12.146 closed.
$ head -1 /home/dkoleary/.ssh/authorized_keys | kf
b1:f3:e3:15:b2:87:10:42:d2:19:72:d8:41:8e:09:4e oleary1          dkoleary@oleary1

```
Those are the exact same keys...

Has anyone into this and know how to get around it?  My google-foo is weak today as I haven't been able to find any mention of it.

Thanks for any help/hints/tips/suggestions.

Doug O'Leary

---

### Post by dkoleary on 2016-08-12
Hey;

Never mind, dumb #$%^ error on my part... server was misconfigured.  

Thanks

Doug

---

