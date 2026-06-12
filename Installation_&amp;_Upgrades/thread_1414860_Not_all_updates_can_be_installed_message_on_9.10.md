---
title: "Not all updates can be installed message on 9.10"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by magneze on 2010-02-24
This morning I'm getting the "Not all updates can be installed" message with "Run a partial upgrade, to install as many updates as possible". I have 527MB to download apparently.

This seems wrong as I always keep my machine up to date. Has someone pressed the wrong button and caused the 10.04 alpha packages to become available to 9.10 users or something like that?!:confused:

---

### Post by magneze on 2010-02-24
Ignore me, I'm being silly. Now I look at the packages it's some internal stuff. That's why it's so big. :-\":oops:

---

### Post by Donalb on 2010-03-13
I have a similar issue since yesterday. I actually don't understand.
There are 3 kernel updates, 2.6.31.19.32 that won't install & an Openshot that won't install (I don't have Openshot).
 It's telling me run a Partial Upgrade?

---

### Post by phillw on 2010-03-13
Hi,

It's usually caused by a dependancy (a library file) wanting to be removed / updated / replaced.

The command line method can help in resolving these issues

```
sudo apt-get update
sudo apt-get upgrade
```

Sometimes, aptitude can solve dependancies when apt-get cannot (Don'task me why !!).

```
sudo aptitude update
sudo aptitude upgrade
```

Regards,

Phill.

---

### Post by Donalb on 2010-03-13
Thanks dude. 
Playing around with it, somehow one of the sources was broken. Fix Broken in Synaptic did nothing but once I removed Openshot PPA everything is fine, my new kernel is installed and only waiting a restart.
I don't recall every looking at Openshot but I guess I must have.

Reminding me of my favourite Linux quote;
"all over the world, is the sound of linux geeks whining as their uptime counter goes back to O"

---

