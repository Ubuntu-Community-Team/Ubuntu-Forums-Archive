---
title: "[SOLVED] Problem getting/installing updates"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by Snave88 on 2008-08-19
I started up the computer this morning and noticed the availabe updates icon.  I tried to download and install the available updates and came upon my first Ubuntu stumbling block.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

The above is the result I got when I tried to get and install the updates.  I'm a Linux/Ubuntu newbie so any help is greatly appreciated.

---

### Post by coffeecat on 2008-08-19
The hint is in the error message. :wink:

> **Snave88 said:**
> you must manually run 'dpkg --configure -a' to correct the problem. 

But as a newbie you won't know that you have to run it with sudo. Open a terminal (Applications > Accessories) and type:

```
sudo dpkg --configure -a
```You are prompted for your password and, yes, it is going in. Nothing apparently happening is a security feature, not a bug! :)

As you are new to Ubuntu, I strongly recommend you read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) .

---

### Post by Snave88 on 2008-08-19
Thank you for your help and for the link!:redface:

---

