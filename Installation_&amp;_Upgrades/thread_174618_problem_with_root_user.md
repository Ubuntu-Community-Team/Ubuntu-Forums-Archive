---
title: "problem with root user"
date: 2006-05-12
forum: Installation &amp; Upgrades
---

### Post by gekkos on 2006-05-12
When I try to start an apllication like ex. system - administration - services I be asked to give root password. I always get the error 
Failed to run services-admin as user root:
Wrong password.
But when I open a terminal window and change to root the root password works.
What can be the problem that I cannot run these applications as root__
manz thanks

---

### Post by tribaal on 2006-05-12
Hum Ubuntu uses a rootless system (we use sudo instead). You should probably give [this]("https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29") a little read, it helped me a lot understand it.

Cheers!

- trib'

---

### Post by cgjones on 2006-05-12
When it asks for the password, are you using your users password, or have you enabled the root account and are using the password you set for that?

---

