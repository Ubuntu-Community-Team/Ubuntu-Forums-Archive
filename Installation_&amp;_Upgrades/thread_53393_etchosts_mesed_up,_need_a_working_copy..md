---
title: "/etc/hosts mesed up, need a working copy."
date: 2005-07-31
forum: Installation &amp; Upgrades
---

### Post by dragonneverdies on 2005-07-31
Hello all,
         I was trying to set up my new cable internet but I messed up my /etc/hosts somehow and each boot prompts for me to add to /etc/hosts. So can anyone post their working  hosts file? or an original copy of it? once again i need /etc/hosts

---

### Post by macgyver2 on 2005-07-31
All you need to start off with is a line like the following:
```
127.0.0.1	localhost.localdomain	localhost   <your-hostname>
```

This was also in my default hosts file...(I comment it out since I don't use IPv6):

```
# The following lines are desirable for IPv6 capable hosts
::1	 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by dragonneverdies on 2005-07-31
how do i get my hostname?

hostname?

cat /etc/hostname?

---

### Post by dragonneverdies on 2005-07-31
Macgyver, your advice didnt work. When I login, I get a prompt.

"Could not find an internet address for .
This will cause Gnome to not work properly
You can fix this problem by adding to /etc/hosts"

I overwrote my hosts.conf to the one Maxgyver suggested and no such luck.

I attempted to go /Adminstration/System/Networking and "Networking" does no launch. Someone please help me. :)

---

### Post by varunus on 2005-07-31
I'm not sure if the above is a typo, but the hosts file is /etc/hosts, not /etc/hosts.conf.  hosts.conf doesn't exist for me.

---

### Post by dragonneverdies on 2005-07-31
yes, its /etc/hosts. sorry. can anyone help me please? or else i will have to use windows until ubuntu works again.

---

### Post by hod139 on 2005-07-31
I believe the default hostname is ubuntu.  So, your /etc/hosts would look like

```
127.0.0.1 localhost.localdomain localhost ubuntu

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
This is of course unless you changed your hostname during the install.  If you open up a terminal, you can easily see your hostname.  It is the name after your username.  For example, my hostname is ubuntu, and when I open a terminal I get:
sberard@ubuntu:~$

---

### Post by dragonneverdies on 2005-07-31
thanks alot. how do i get my "Networking" to stop crashing?

---

### Post by dragonneverdies on 2005-07-31
or how do i get my ubuntu to stop connecting to a blank entity?

either would be great to know. thanks everyone. ubuntu is great!

---

### Post by hod139 on 2005-07-31
[QUOTE=dragonneverdies]thanks alot. how do i get my "Networking" to stop crashing?[/QUOTE]

What terminal output do you get if you type:
```
sudo network-admin
```

---

### Post by dragonneverdies on 2005-07-31
thanks alot everyone. i ran network-admin in terminal and i changed the ethernet so it all works now.

---

### Post by dragonneverdies on 2005-07-31
btw, i am using a remote hostname. how do i get a local one?

---

### Post by varunus on 2005-08-02
You should be able to change your host name in the "network-admin" tool.

---

