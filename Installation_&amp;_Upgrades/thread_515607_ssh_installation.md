---
title: "ssh installation"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by nanjil on 2007-08-02
hello:

I followed ssh installation procedure in ubuntu wiki

However when i try to ssh from the remote machine the host key verification fails .

if i use the option
-o StrictHostKeyChecking=no
I get "permission denied" message.

1. how do i verify whether ssh is really running in ubuntu?

2. how I do get over this host key verification problem?

thanx

u
    * Read #General Notes
    * Read #How to add extra repositories 

sudo apt-get install ssh

[edit]
How to SSH into remote Ubuntu machine

    * Read #General Notes 

    e.g. Assumed that remote Ubuntu machine have installed SSH Server service 
    Read #How to install SSH Server for remote administration service 
    Remote Ubuntu machine: 192.168.0.1 

ssh username@<my_ubuntu_machine>

---

### Post by Pumalite on 2007-08-02
If firewalls: open port 22. If not: go to>/home/<username>View>Show Hidden Files>.ssh>Edit known_hosts(erase the encrypted key present; leave the file empy). Try again.

In Konqueror:  fish://<username>@IP

---

### Post by nanjil on 2007-08-02
> **Pumalite said:**
> If firewalls: open port 22. If not: go to>/home/<username>View>Show Hidden Files>.ssh>Edit known_hosts(erase the encrypted key present; leave the file empy). Try again.

In Konqueror:  fish://<username>@IP

how do ii find out whether there is a firewall and

how do i open th firewall port?
thanx

---

### Post by Pumalite on 2007-08-02
Ping an IP in your terminal. See what it gets you.
P.S. Ubuntu comes without firewall by default.  Suse does. Most common firewalls: Firestarter and Guarddog. Where to look for them: 'Security'

---

### Post by davidshere on 2007-08-03
> **nanjil said:**
> hello:
1. how do i verify whether ssh is really running in ubuntu?
2. how I do get over this host key verification problem?


Not sure on the second one, sorry.. but if you're getting "permission denied", or anything other than "connection timed out" or "connection refused", ssh server is most likely running, and you're not having a firewall issue.  You can also click System> Administration> Services> and look for SSH.  Mine looks like this:

[ATTACH]39701[/ATTACH]

Also, I believe I install openssh-server, is that the package you installed?  It should start itself after you install it.

---

