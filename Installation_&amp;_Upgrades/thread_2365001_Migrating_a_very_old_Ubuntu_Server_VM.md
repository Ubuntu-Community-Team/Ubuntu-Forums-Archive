---
title: "Migrating a very old Ubuntu Server VM"
date: 2017-06-30
forum: Installation &amp; Upgrades
---

### Post by loonixtarballs on 2017-06-30
Hi.

I have a Hyper-V VM with Oneiric running a few services that I'd like to migrate to a new host. Now, the problem is that if I just move the VM over I get a kernel panic. I've tried updating to Xenial, and this does allow the OS to boot properly, but unfortunately it breaks at least one of the services -- an Apache server.

I don't want to try to fix this and I'm not able to check if anything else is broken, because I don't know what else is running here. I don't know if anyone does anymore. What I'd like is to touch as little as possible and just update the kernel to 4.x. How could I go about doing this?

Thanks.

---

### Post by QIII on 2017-06-30
Hello!

How broadly is your server exposed?

---

### Post by loonixtarballs on 2017-06-30
It's behind a firewall and no ports are open to the outside. I think there's some kind of ticket system running on it or something, but I'm not too clear on how it works without receiving connections from outside.

---

