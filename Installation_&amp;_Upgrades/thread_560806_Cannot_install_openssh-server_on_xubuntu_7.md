---
title: "Cannot install openssh-server on xubuntu 7"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by albatroz2k on 2007-09-26
Everytime I try to install open-ssh server, i get the following results.
Why? Do I need to change the repositories?
I am trying this on xubuntu 7.04

[PHP]
ubuntu@ubuntu-desktop:~$ sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package openssh-server has no installation candidate
ubuntu@ubuntu-desktop:~$ 
[/PHP]

---

### Post by Pumalite on 2007-09-26
Try Synaptic>Search>open-ssh>open-ssh-server>install

---

### Post by albatroz2k on 2007-09-26
Only openssh-client is shown :(

---

### Post by albatroz2k on 2007-09-26
Solved my issue.
The solution?

Type
sudo apt-get update  
before
sudo apt-get install ssh

---

### Post by Pumalite on 2007-09-26
Good for you!

---

### Post by Simper on 2008-03-15
The reason openssh-server isn't found is because it is in the universe or multiverse repositories which are, by default, disabled.

To enable them in Xubuntu (7.10):

Applications>System>Software Sources> <type password>> check ... (main), ... (universe) and ...(multiverse) > Close

Now the required repositories have been enabled and you can install openssh-server:

# sudo apt-get install openssh-server

Or

Applications>System>Synaptic Package Manager>Search>"openssh-server" and check for installation, apply changes and you're all set.

Hope this will help you out.

Cheers!

---

