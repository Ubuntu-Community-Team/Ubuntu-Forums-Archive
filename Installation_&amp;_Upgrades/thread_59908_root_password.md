---
title: "root password"
date: 2005-08-25
forum: Installation &amp; Upgrades
---

### Post by Marco Neudorfer on 2005-08-25
Hello,
Tonight i installed Ubuntu 5.04 and i am very very enthousiastic about it so far.
Everything is so easy!
But my question is: during the installation i wasn't asked for a root password.
When i want to do something with root priviliges, how do i do that without a root password? This may be a dumb question, but i wonder..

Thanks in advance.

Marco Neudorfer

---

### Post by Daniel Rehm on 2005-08-25
[QUOTE=Marco Neudorfer]Hello,
Tonight i installed Ubuntu 5.04 and i am very very enthousiastic about it so far.
Everything is so easy!
But my question is: during the installation i wasn't asked for a root password.
When i want to do something with root priviliges, how do i do that without a root password? This may be a dumb question, but i wonder..

Thanks in advance.

Marco Neudorfer[/QUOTE]
 You can use the sudo command to do anything that needs root privileges.

If you really really want to have a password set for root, do this:

sudo passwd root

and you should first be prompted to enter your user password, then to enter another password. That second one will be your root password. I don't know if you can log in as root in gnome, but you can from the command line.

---

### Post by Buffalo Soldier on 2005-08-25
I would like to redirect you to [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

There it explains what is sudo, how to use it and the reasons why Ubuntu uses it.

---

