---
title: "I can't login as root"
date: 2006-03-01
forum: Installation &amp; Upgrades
---

### Post by Cosmic P on 2006-03-01
I just installed Ubuntu with GNome (version 5.10 for PC), since my last Linux installation (Kanotix) somehow got fucked up.

During the installation, an account for non-administrative purposes was created for me. But how do I login as root? During the installation, no password was set for the root account.

I can use Synaptic with my account password, but I still can't login as root, so I don't have access to some directories, etc.

---

### Post by Xian on 2006-03-01
You should not log in as root, as it is a very bad security practice. You instead use the sudo command to get admin rights when they are needed. For example, from a terminal:

$ sudo nautilus
$ sudo gedit

.... and so forth.

---

### Post by jibril on 2006-03-01
The problem is that it wont let me acquire root previlege.

Whn i type su at the prompt and enter the only password i have set, it says permission denied

jibril

---

### Post by PhilOSparta on 2006-03-01
Prudent advice is that you shouldn't log in as root, but some of us want or need that capability.   The following will allow you root access:

sudo -s -H

Now that you have enough rope, don't hang yourself.:D

---

### Post by TrendyDark on 2006-03-01
the root password should be your password.

---

### Post by frodon on 2006-03-01
[QUOTE=jibril]The problem is that it wont let me acquire root previlege.

Whn i type su at the prompt and enter the only password i have set, it says permission denied

jibril[/QUOTE]It's because the command with ubuntu is : ```
sudo su
```

---

### Post by aysiu on 2006-03-01
You don't *need* a root account.

[http://www.psychocats.net/linux/permissions](http://www.psychocats.net/linux/permissions)

---

