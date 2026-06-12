---
title: "Normal user without sudo capability?"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by saltydog on 2008-05-25
I am in the need to install Ubuntu on 10 desktops in a small office. The problem is that the Admin doesn't want the single PC user to have sudo capability but he needs to have his own root account on each PC, to be able to connect to it via SSH.

IS there any automation to do this during install, or should I modify /etc/sudoers on each PC?

---

### Post by mbaker824 on 2008-05-25
> **saltydog said:**
> I am in the need to install Ubuntu on 10 desktops in a small office. The problem is that the Admin doesn't want the single PC user to have sudo capability but he needs to have his own root account on each PC, to be able to connect to it via SSH.

IS there any automation to do this during install, or should I modify /etc/sudoers on each PC?

As I remember, only one user account gets created during install, and it will be an admin account (with sudo privileges) by default.  Any accounts you create after install do NOT have sudo privileges, by default.

There's no need to modify sudoers; it's set up so that any account that is a member of the admin group has sudo privileges.  All you need to do is make sure all accounts other than the administrator's are not members of the admin group, which is the default anyway.

Mark

---

### Post by saltydog on 2008-05-25
Yes Mark, that's clear. But in any case I have to set up at least 2 users on the PC: What I would have preferred was: 

1 - root (the admin)
2 - the default user of the PC (no admin).

One way could be - after installation and after having created a root password, to remove the default user from the admin goup..

---

### Post by mbaker824 on 2008-05-25
> **saltydog said:**
> Yes Mark, that's clear. But in any case I have to set up at least 2 users on the PC: What I would have preferred was: 

1 - root (the admin)
2 - the default user of the PC (no admin).

One way could be - after installation and after having created a root password, to remove the default user from the admin goup..

I think a better way would be to make the "default" user (the one created during install) the admin user (you wouldn't want to use the actual root account for that anyway).  So you would create the same user account on all ten machines during install.  The account created after install would be the actual default user (the non-admin user of the PC).  There's no need to remove any accounts; the order in which they're created doesn't matter.

The actual root account is automatically created, with an auto-generated password, during install.  The admin would use a separate account in the admin group, and use sudo to gain root access.

Mark

---

