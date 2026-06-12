---
title: "package not found"
date: 2012-11-03
forum: Installation &amp; Upgrades
---

### Post by alexDgreat on 2012-11-03
i tried installing openssh-server with this command

sudo apt-get -y openssh-server

and this is the response i got

Package openssh-server is not available, but is refereeed to by another package. This may mean that the package is missing, has been obsoleted or is only available from another source
E: Package openssh-server has no installation candidate

kindly assist to overcome this problem.

---

### Post by alexDgreat on 2012-11-03
i tried installing openssh-server with this command

sudo apt-get -y openssh-server

and this is the response i got

Package openssh-server is not available, but is refereeed to by another  package. This may mean that the package is missing, has been obsoleted  or is only available from another source
E: Package openssh-server has no installation candidate

kindly assist to overcome this problem.

---

### Post by newb85 on 2012-11-03
I assume you meant
```
sudo apt-get **install** -y openssh-server
```

It should be available in the Main repository.  What release are you using?  Also, do you know which mirror you are using?

---

### Post by Frogs Hair on 2012-11-03
The package in synaptic for 12.10 is named openssh-server. It could be -y causing the problem.

---

### Post by ajgreeny on 2012-11-03
Please don't duplicate the same post in two places.  It dilutes the answers you get and is not helpful.

To answer your question, however, the command should be ```
sudo apt-get install openssh-server
```
I'm surprised your command did anything, or did you simply mistype your command in this post?

---

### Post by newb85 on 2012-11-03
> **Frogs Hair said:**
> The package in synaptic for 12.10 is named openssh-server. It could be -y causing the problem.

-y is an option for apt-get that shouldn't be causing any problems.

Actually, based on the typos in the terminal outputs, I would say the OP is not using copy and paste.

---

### Post by lisati on 2012-11-03
Threads merged.
Please do not start multiple threads for the same question, it dilutes the community's ability to help.

---

