---
title: "Installing the server and desktop"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by josephmo on 2008-07-06
I installed the Ubuntu Server 8.04 (32 bit). Whe I was done with the install, and I started the system, I was in a command line mode (no graphical user interface). Is this a newbie user error, or did the desktop not install as part of the install process?

---

### Post by tinny on 2008-07-06
newbie error :)

Servers are for power users. You need to install the Ubuntu 8.04 LTS Desktop Edition.

[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

This will install a Desktop environment for you.

---

### Post by Vivaldi Gloria on 2008-07-06
> **josephmo said:**
> I installed the Ubuntu Server 8.04 (32 bit). Whe I was done with the install, and I started the system, I was in a command line mode (no graphical user interface). Is this a newbie user error, or did the desktop not install as part of the install process?

Server edition comes without a desktop. To install desktop use the command

```
sudo apt-get install ubuntu-desktop
```

---

