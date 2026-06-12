---
title: "Ubuntu 7.10 Server LAMP Installation - Question..."
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by behrk2 on 2008-01-23
Hey all,

So I have installed Ubuntu Server 7.10 (LAMP installation) onto my computer. However, there doesn't seem to be any apache or mysql installed...

After looking at screenshots of installation, it shows that apache, sql, etc. should start at boot time. My boot-up shows nothing about apache or sql starting. (This is all prior to login). Once I logged in, I searched all of the directories and found no apache directories.

I am certain that I selected the LAMP configuration during installation.

Anyone know what is wrong?

Thanks!

---

### Post by louieb on 2008-01-24
Not sure what is going on. 
Go ahead and install **htop **(really nice version of top) and see if any mysql or apache process are running. 
Try running tasksel and see if the lamp-server box is marked.
```
sudo tasksel
```
Other good stuff on LAMP here: [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by behrk2 on 2008-01-24
louieb-

I installed htop, no mysql or apache processes are running. I ran tasksel, and the LAMP server box is not checked...

---

### Post by az on 2008-01-24
> **behrk2 said:**
> louieb-

I installed htop, no mysql or apache processes are running. I ran tasksel, and the LAMP server box is not checked...

Check it.

---

