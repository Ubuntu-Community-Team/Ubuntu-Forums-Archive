---
title: "edgy : sudo doesn't work"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by tortue17 on 2006-11-21
Hi,

after installing dapper on computers at my work, we decide to test the edgy's Ubuntu.
We have an installation procedure, and I apply it to the edgy's installation.
After some little problems which are regulate, we have a last one that we can't resolve.

The sudo command doesn't work. The message are :

xxx@libserv-irit:~/script$ sudo synaptic 
xxx is not allowed to run sudo on libserv-irit.  This incident will be reported.

/etc/sudoers is OK, like in dapper's procedure installation

# User privilege specification
root    ALL=(ALL) ALL
xxx localhost = PASSWD: /usr/sbin/synaptic, /usr/bin/network-admin

the log in messages :

Nov 21 15:37:40 localhost sudo:  xxx : user NOT authorized on host ; TTY=pts/8 ; PWD=/home/xxx/script ; USER=root ; COMMAND=/bin/su

The problem is the same for a local user than a ldap user.
Why sudo works fine under Dapper but doesn't fine under edgy :-k 

If someone has an idea :confused: 

thanks a lot.

---

### Post by taurus on 2006-11-21
What groups do you belong to?  You need to be on both adm & admin in /etc/group so run this command at the prompt to see if both of those two groups are on the list...

```
id
```

---

### Post by aysiu on 2006-11-21
If you need help getting back into the *admin* group, try this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by tortue17 on 2006-11-21
I try .....and I saw.

If my user are in the "admin" group, sudo works fine
If not, it doesn't work :-k 

Why under Dapper, I've not this problem :-k 
non one of my users are in the "admin" group, but they can lauch sudo ](*,) 

What's the problem with Edgy :confused:

---

### Post by aysiu on 2006-11-21
> **tortue17 said:**
> 
If my user are in the "admin" group, sudo works fine
If not, it doesn't work :-k This is the way Ubuntu works and has always worked.

> 
Why under Dapper, I've not this problem :-k 
non one of my users are in the "admin" group, but they can lauch sudo ](*,) Maybe you did something to your /etc/sudoers file in Dapper to allow all users to *sudo*.

---

### Post by tortue17 on 2006-11-22
If you look at my sudoer's file , you can see that I define an user to do root command :

# User privilege specification
root ALL=(ALL) ALL
xxx localhost = PASSWD: /usr/sbin/synaptic, /usr/bin/network-admin

xxx can launch in sudo, synaptic and network-admin
I did not add xxx in admin group, because I would restrict user in sudo command

:-k

---

### Post by tortue17 on 2008-02-06
This is a long time, but I forgot to post the answer 

Under edgy, in the sudoers file, I change **localhost** by the **name_of_the_computer**, and sudo run.
That's all

---

