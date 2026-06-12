---
title: "Root confusion"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by gcoug on 2005-06-28
I am still not sure I understand the use of 'root' but I don't remember setting a root password during the installation process.  I remember setting a user and user password and it seems to work as root in most cases but several cases it hasn't.

This is confusing since several of the other distros installations (FC3/4 and Mepis) forced me to create a root password.  Is there a root password and how do you change it?

Bob

---

### Post by SGC on 2005-06-28
Ubuntu does not create a root account like others distro, It uses **sudo** instead, where you enter **sudo** before the command and then you enter your password.

To create the root account, use the following command:
```
sudo passwd root
```

---

### Post by gcoug on 2005-06-29
Thanks SGC!

If I create a root account in that manner, is 'sudo' still used or do you access the root via 'su'.  While I like trial and error while learning, I really don't like locking myself out and having to reinstall.  I built this box just to learn (or play) with different distros.

Bob

---

### Post by SGC on 2005-06-29
Sudo will works even if you create the root account, so you can uses either su or sudo

For more on this topic, read this:
[http://ubuntuguide.org/#usersadministration](http://ubuntuguide.org/#usersadministration)

---

