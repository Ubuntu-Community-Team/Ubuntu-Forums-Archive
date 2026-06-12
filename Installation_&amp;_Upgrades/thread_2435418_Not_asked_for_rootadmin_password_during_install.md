---
title: "Not asked for root/admin password during install"
date: 2020-01-20
forum: Installation &amp; Upgrades
---

### Post by rtcary on 2020-01-20
This is the first time I have used Ubuntu, and I am installing it via an ISO disk I downloaded. I'm at the screen that asks for Your Name and User Name. My past experience has been with Centos where one enters the password for the Super User during the install and then the name and password for a user. I am not seeing that with Ubuntu.

I am installing over Centos 7 and told the installer to erase and install as a LVM.

What am I missing?

Many thanks...

\rtc

---

### Post by deadflowr on 2020-01-20
Ubuntu's installer doesn't set or ask for a root password.
The initially created user has sudo rights, with which you can set a root password if you want, post-install.

How other distros do things is how other distros do things.

---

### Post by rtcary on 2020-01-20
Thank you for the clarification...

\rtc

---

### Post by crip720 on 2020-01-20
Deadflower can you explain your answer a bit more.  I have been installing ubuntu for years and every installation asks for a password to be set.

---

### Post by CatKiller on 2020-01-20
> **crip720 said:**
> Deadflower can you explain your answer a bit more.  I have been installing ubuntu for years and every installation asks for a password to be set.

There's nothing more to explain. The installer asks you to set a user password. It doesn't ask you to set a password for root; no root password is set; you can't log in as root even if you set a root password.

---

### Post by TheFu on 2020-01-20
RHEL/CentOS and a few other distros have always had a root account.
In Ubuntu, the root account doesn't allow logins. We use sudo to elevate privileges when needed.  It has always been that way and works very well.  Plus, we don't have to worry about remote root logins, since none are possible by default.

The first account, created during the install, is added to the 'sudo' group and is the only one able to use sudo initially.

---

### Post by crip720 on 2020-01-20
Thank you, from the question the OP was not seeing any place for a password, root or user.

---

