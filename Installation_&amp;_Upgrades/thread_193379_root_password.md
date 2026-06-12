---
title: "root password"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by jian on 2006-06-09
I just installed Ubuntu LTS, but I don't remember where it ask me to type in the root password.  Now I cannot log in as su.  Is there a way to help me out?  Thanks a lot!

---

### Post by aysiu on 2006-06-09
There is no root password.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

You may also want to read:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by FredB on 2006-06-10
[QUOTE=jian]I just installed Ubuntu LTS, but I don't remember where it ask me to type in the root password.  Now I cannot log in as su.  Is there a way to help me out?  Thanks a lot![/QUOTE]

Sudo will be the tool to use for root account user activities. More secure and cleaner ;)

---

### Post by rcarring on 2006-06-10
If, for some reason, you really need to be running as root, then

```

sudo su -

```

will put you in as root.

I don't recommend it though, makes a dreadful mess of installing applications that write folders in users home.

---

