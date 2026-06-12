---
title: "mupen64plus"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by Inventech on 2008-07-22
I downloaded mupen64plus and I have no idea how to install it.  Any help would greatly appreciated. 

[http://code.google.com/p/mupen64plus/]("http://code.google.com/p/mupen64plus/")

---

### Post by zvacet on 2008-07-22
I hope that you downloaded bin version.In that case type in terminal

```
su
 # ./install.sh
 # exit
```

You have these instructions in Read me file.

---

### Post by Inventech on 2008-07-22
> **zvacet said:**
> I hope that you downloaded bin version.In that case type in terminal

```
su
 # ./install.sh
 # exit
```

You have these instructions in Read me file.

When I type that code in terminal it asks me for password, what password is it?

---

### Post by xen-uno on 2008-07-22
It's **your** *login* password

---

### Post by Inventech on 2008-07-23
> **xen-uno said:**
> It's **your** *login* password

I tried and all it says is "su: Authentication failure"

---

### Post by xen-uno on 2008-07-23
1st thought is passwords, like the file system, are case sensitive. I would go to System>Administration>Users and Groups, pick your normal login account, hit Properties, and re-define your password. I've never been asked for a password in Ubuntu where my login password didn't work.

---

### Post by dopple on 2008-08-10
Change su to sudo.

---

### Post by bornialla on 2009-08-05
Then what do you do

---

### Post by dopple on 2009-08-07
It's been a while since I installed it but i reckon you navigate to the mupen64plus directory in the terminal then type sudo ./install.sh.

---

