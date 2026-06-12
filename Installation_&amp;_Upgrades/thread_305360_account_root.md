---
title: "account root"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by cana on 2006-11-23
i want to be root in my computer but i dont know the password to be super user..

how i can know my root password..

how i can to be super user in my computer..


i am a new user for ubuntu....

---

### Post by cantormath on 2006-11-23
> **cana said:**
> i want to be root in my computer but i dont know the password to be super user..

how i can know my root password..

how i can to be super user in my computer..


i am a new user for ubuntu....

open terminal

```
laptop:~$ sudo -i
```

---

### Post by cantormath on 2006-11-23
You Should not do this, there is really no need, but.....
if you want to set a root password,

open terminal

```
laptop:~$ sudo passwd su
```

---

### Post by cantormath on 2006-11-23
the idea in debian is if you want to do something as root, or similar....
sudo the command, type in your password, and execute.   Its not safe to run as root unless you realllllllllly know what you are doing.

---

### Post by DaveHartburn on 2006-11-23
In Ubuntu, you do not login as root, but become root.

Say you want to remove a file /tmp/bob, as root you need to do
sudo rm /tmp/bob

This will prompt you for a password, put in your own. You do need to make sure you are in the adm group, which you probably should be if you have just done the new install yourself.

If you really want a root shell, you can do
sudo bash

---

### Post by cantormath on 2006-11-23
> **DaveHartburn said:**
> In Ubuntu, you do not login as root, but become root.

Say you want to remove a file /tmp/bob, as root you need to do
sudo rm /tmp/bob

This will prompt you for a password, put in your own. You do need to make sure you are in the adm group, which you probably should be if you have just done the new install yourself.

If you really want a root shell, you can do
sudo bash

you can log in as root.....but I like your analogue, its better to become root when needed....  It is alittle different when you sudo though,  your user is actually on an admin list, a set of users allow to perform admin commands.

---

### Post by bhasi75 on 2006-11-24
I was wondering how to login as root, Thank you all for sharing the information.


> you can log in as root.....but I like your analogue, its better to become root when needed.... 

Be root ONLY when you really need to...

---

