---
title: "updating programs"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by dtdave on 2008-01-15
I wanted to know if I install extra programs that are not default, like vlc, compiz pluggins such as 3d windows or whatever, will the updater see those and get updates for them or do I have to get updates for them myself.  Thank you

---

### Post by meindian523 on 2008-01-15
They will be updated automatically,provided you have the repositories you installed them from enabled.

---

### Post by dtdave on 2008-01-15
how do I tell if they are enabled?

---

### Post by Sef on 2008-01-15
Applications > Add/Remove > The box in the upper right should say 'All Available Applications'.   If it does, then they are enabled.

---

### Post by meindian523 on 2008-01-16
@sef

Does that guarantee that even universe and multiverse are enabled?I have not used Add/Remove much,prefer Synaptic/apt-get. ;)

---

### Post by Partyboi2 on 2008-01-16
Software Sources (System>Admin>Software Sources) will tell you if you have the  repo's enabled. But if you downloaded the packages via apt-get, add/remove, synaptic then they are probably already enabled:)

---

### Post by dtdave on 2008-01-16
thanks a million!

---

### Post by dtdave on 2008-01-16
one more question on this, for  the compiz addons, if I want the newest ones, in beta or whatever for a plugin like 3d, or atlantis, would I want to check more than the default in updates to look for in software sources? such as pre-released, and unsupported updates to see them?   Thanks

---

### Post by meindian523 on 2008-01-17
compiz itself is beta(or alpha,I forget),the only plugins which can be more beta than beta are the ones which haven't been coded yet!:)

---

### Post by dtdave on 2008-01-17
thanks for the reply, with the next version of ubuntu, is it good to upgrade to new versions or do a fresh install, I have seen on different distros that they say it is better to do a fresh install than upgrade, just wondering if the ubuntu upgrade process is ok to do or not

---

### Post by meindian523 on 2008-01-17
It's better to do a clean install,```
sudo apt-get dist-upgrade
``` is not very reliable as yet.

---

### Post by dtdave on 2008-01-17
is there a way to backup my home dir  and put it back on in the new, I dont have a seperate partition for home, so if you could give me some steps, or is it as easy as going to my home dir and copy and paste it on a usb drive and re-paste it on the new install overwriting the new home dir      thanks for your response

---

### Post by zvacet on 2008-01-17
Yes,upgrade proces is O.K.  even I don´t use net to upgrade.I prefer upgrade with alternate Cd,but that is just me not universal rule.

---

### Post by Pumalite on 2008-01-17
You can have a separate /home:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by meindian523 on 2008-01-17
First create a /home by following the above,then clean install.

---

### Post by dtdave on 2008-01-20
thanks I will look into it!

---

