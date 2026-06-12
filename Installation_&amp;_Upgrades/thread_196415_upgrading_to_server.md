---
title: "upgrading to server"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by richardspirit on 2006-06-14
Is it possible to upgrade to the server version without destroying current version?

I am currently on the latest desktop version.

---

### Post by ajgreeny on 2006-06-14
Not sure what you mean.  Surely the desktop version already includes what you need for a server, or if not you can simply add the packages needed using apt-get or synaptic.

---

### Post by richardspirit on 2006-06-14
And it probably does but I don't which ones and I thought that the server version had gui's that would make finding and using the tools easier.

I don't have a lot of experiance with servers but I wanted to experiment.

---

### Post by GameGod on 2006-06-14
No, the server version doesn't come with any extra graphical tools...

If you want to install the server version, from the terminal, type:
```
sudo apt-get install ubuntu-server
```
or from Synaptic just install the "ubuntu-server" package.

(Honestly though, there really isn't any point in doing this...)

---

### Post by richardspirit on 2006-06-14
I tried running the 

sudo apt-get install ubuntu-server 

but it says that it can't find the package.

---

### Post by wifiabc on 2006-07-10
I tried looking for it from synaptics but could not find it too. I also can't locate a LAMP package ??

---

