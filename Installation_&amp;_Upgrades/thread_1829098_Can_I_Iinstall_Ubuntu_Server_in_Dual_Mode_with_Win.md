---
title: "Can I Iinstall Ubuntu Server in Dual Mode with Win 7 on my Laptop?"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by NCMS on 2011-08-20
I am trying to install **ubuntu 10.04.3 LTS  server**  OS  in dual mode on my laptop running Windows 7, 
but I noticed whenever I run   **WUBI.EXE**  file  it fetches and installs the desktop version!!
 
**[COLOR=red]Is there way to install the server insetead?[/COLOR]**
**[COLOR=#ff0000][/COLOR]**

---

### Post by sanderd17 on 2011-08-20
It's not a good idea to install the server with Wubi. Wubi is only for long testing periods (a few months). And I believe that you want your server to run longer.

Also, you can do all the same tasks with the desktop edition as with the server edition. The major difference between the two is that the server edition doesn't come with a graphical environment to save space.

---

### Post by NCMS on 2011-08-20
If there is no difference then no worries ..
 
**Can I create partitions manually wiht  WUBI ?**
 
**[COLOR=red]Thanks...[/COLOR]**

---

### Post by sanderd17 on 2011-08-20
The only advantage of Wubi is that you don't have to create partitions. This method makes it easier to uninstall.

Wubi creates a virtual filesystem inside one of your existing partitions. So Windows sees it as a file, while ubuntu mounts it and uses it as filesystem.

---

### Post by NCMS on 2011-08-20
Oooops, I have noticed that, but what I meant actually creating partitions on Ubuntu itself and specify size of each partition manually, e.g.,  /home  ,  etc...
 
Is this possible ?
 
**THANK YOU**

---

### Post by sanderd17 on 2011-08-20
Hmmm, I don't believe it is. You install it via a Windows program, and you only have a "size" option there, that's for the complete installation. And if you open up a partition program, it will see the real partitions, so it won't see the virtual filesystems that a Wubi installation needs.

But if I were you, I would go for a normal, non-Wubi, dual boot. There you have all freedom of installing the server version and choosing partition sizes.

---

### Post by NCMS on 2011-08-20
**Sanderd17**,

Simply THANK YOU very much for your time,

Thanks...

---

### Post by sanderd17 on 2011-08-20
No problem

---

### Post by Mark Phelps on 2011-08-21
If you're still planning on installing Ubuntu on your laptop, BEFORE you do anything else, do the following:
1) Boot into Win7
2) Use the Backup feature to create and burn a Win7 Repair CD.

This CD will come in handy later, should you either need to repair your Win7 boot loader, or restore it to its original condition.

---

