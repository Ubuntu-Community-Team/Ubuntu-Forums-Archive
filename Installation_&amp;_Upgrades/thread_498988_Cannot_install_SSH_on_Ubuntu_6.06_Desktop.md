---
title: "Cannot install SSH on Ubuntu 6.06 Desktop"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by textguru on 2007-07-12
I have freshly installed Ubuntu Desktop 6.06 and notice that I cannot install SSH Server. It tells that SSH package is not available, package has no installation candidate. Here is the command that I made:

sudo apt-get install ssh openssh-server

Any error that I made?

---

### Post by louieb on 2007-07-12
Dapper already has the **openssh-clien**t. The **ssh** is a meta package that has **openssh-server** and **openssh-client**. Probably just need to [B]sudo aptitude openssh-server  
[/B]Later, Lou

---

### Post by textguru on 2007-07-12
does it mean that I can directly ssh this machine? If yes, I have tried it and it didn't work. I normally install ssh server so I may able to connect to the pc remotely.

---

### Post by louieb on 2007-07-12
To ssh into the machine you still have to install **openssh-server** first.
Actually don't know why your apt-get did not work. Though apt-get may have gotten confused because you asked for the same package twice.  The ssh stuff is in the main repository. Perhaps your /etc/apt/sources.list is messed up. Did you get the 100+ package update notice after the install?    

Try Synaptic and search for **openssh** you should get a list of a dozen or so packages including openssh-server.

---

### Post by textguru on 2007-07-15
> **louieb said:**
> To ssh into the machine you still have to install **openssh-server** first.
Actually don't know why your apt-get did not work. Though apt-get may have gotten confused because you asked for the same package twice.  The ssh stuff is in the main repository. Perhaps your /etc/apt/sources.list is messed up. Did you get the 100+ package update notice after the install?    

Try Synaptic and search for **openssh** you should get a list of a dozen or so packages including openssh-server.
Just solved it! I just ran apt-get update and install ssh and it works!:KS

---

