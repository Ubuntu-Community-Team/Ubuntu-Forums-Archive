---
title: "please help me im fairly new to ubuntu"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by Fallen103 on 2007-05-27
Hi all i am very new to linux and a freind of mine told me about ubuntu and he downloaded 7.04 for me so im trying it out. I have installed this all ok, but when it comes to update using the update manager i get this error message........

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

does anyone know what this means and how to get this to work. I did type in dpkg --configure -a but didn't know what to do

Any help would be much appreciated

---

### Post by ntetreau on 2007-05-27
> **Fallen103 said:**
> Hi all i am very new to linux and a freind of mine told me about ubuntu and he downloaded 7.04 for me so im trying it out. I have installed this all ok, but when it comes to update using the update manager i get this error message........

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

does anyone know what this means and how to get this to work. I did type in dpkg --configure -a but didn't know what to do

Any help would be much appreciated

I'm not exactly sure what your problem is, but most commands that have to do with installing/updating or removing packages need to be run preceded by the sudo command.  You will then be asked for your password.  This is a security measure obviously.  That means that you should run:

```
sudo dpkg --configure -a
```

when your done, run this:

```
sudo apt-get install -f
```

to fix any remaining issues with packages.  You could then try the update again, and hopefully everything will be smooth running for then on.  Welcome to ubuntu!

Nic

---

