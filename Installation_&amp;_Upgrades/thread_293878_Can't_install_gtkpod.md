---
title: "Can't install gtkpod"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by shortsellyhoonow on 2006-11-05
I am unable to install gtkpod... I get the following error:

sudo apt-get install gtkpod
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gtkpod

What am I doing wrong?

Why is it so hard to register for an account on this forum??

---

### Post by taurus on 2006-11-05
Did you remember to run 

```
sudo aptitude update
```
first?

And what do you mean it's hard to register for an account for this forum?  A little hint would help others in case there is a problem with the registration process...

---

### Post by bikeboy on 2006-11-05
You probably don't have the Universe repository enabled. The Ubuntu wiki has this article to explain what they are and how to add new ones.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by bikeboy on 2006-11-05
> **shortsellyhoonow said:**
> 

Why doesn't this FAGGOT distro have a ******* C compiler?

Ignoring your other ignorant crap...

Typical new Ubuntu users don't need a C compiler because you don't often need to compile software, Those users who want to compile their own have enough knowledge to do it, and will install the build-essential metapackage.

```
sudo aptitude install build-essential
```

---

