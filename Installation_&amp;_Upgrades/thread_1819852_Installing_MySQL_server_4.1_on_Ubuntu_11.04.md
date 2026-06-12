---
title: "Installing MySQL server 4.1 on Ubuntu 11.04"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by drewbocz on 2011-08-06
Hi, how do I need to install mySQL server 4.1 on Ubuntu 11.04 server for a legacy app to run (it breaks on mySQL 5).

```
sudo apt-get mysql-server-4.1
``` doesn't work - "package is missing, obsoleted or available from another source".

Thanks.

---

### Post by lmarmisa on 2011-08-06
Hi and welcome to the forums.

Try this command:

```

sudo apt-get install mysql-server

```

---

### Post by karlson on 2011-08-06
> **drewbocz said:**
> Hi, how do I need to install mySQL server 4.1 on Ubuntu 11.04 server for a legacy app to run (it breaks on mySQL 5).

```
sudo apt-get mysql-server-4.1
``` doesn't work - "package is missing, obsoleted or available from another source".

Thanks.

Does your application have a need for the libmysqld?  If not why would you need a server rather then just a client?

---

### Post by karlson on 2011-08-06
> **lmarmisa said:**
> Hi and welcome to the forums.

Try this command:

```

sudo apt-get install mysql-server

```

I think the issue is the specific version here.  "mysql-server" package installs the current version, which 4.1 isn't.

---

### Post by drewbocz on 2011-08-06
@Imarmisa:

Nope, that would just install the latest server version which is 5.1.

Already did that the first time. That's when I found out that my app breaks.

---

### Post by wojox on 2011-08-06
> **drewbocz said:**
> That's when I found out that my app breaks.

Maybe fix your app? MySQL 4.1 will only be supported for so long, so eventually you will need to tinker with the code. :P

---

### Post by drewbocz on 2011-08-06
> **karlson said:**
> Does your application have a need for the libmysqld?  If not why would you need a server rather then just a client?

Hmm, I have no idea. I'm trying to migrate from a Windows Server to Ubuntu Server. I have a Foxpro app connecting to mySQL server 4.1 on Windows.

Just trying to replicate that on Ubuntu. So far, I've got it to the point where the app is already up and running from a remote machine (on mySQL 5.1). However, I have tested and verified that some functions don't work well and it is because of the difference in mySQL versions.

---

### Post by drewbocz on 2011-08-06
> **wojox said:**
> Maybe fix your app? MySQL 4.1 will only be supported for so long, so eventually you will need to tinker with the code. :P

I know, however, it's not my app (yet) as it was developed by someone else long ago and I am still in the process of negotiating for the source code.

In the meantime, I want this thing to run on Ubuntu.

---

