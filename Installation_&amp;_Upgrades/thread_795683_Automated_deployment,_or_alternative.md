---
title: "Automated deployment, or alternative"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by nikkne on 2008-05-15
Hi,
I've decided to upgrade the cluster in our lab from ancient Debian to Ubuntu. After spending couple of days, I've managed to set one machine to have everything we need. Now, I would like to replicate this to other machines (30+). One option is to run rsync, which is a bit annoying. I've read in Server features about Automated deployment, but there is no explanation how to do it, nor any guide. Any suggestions, links are more then welcome :)

Also, when I set all machines, I would like to keep them all in sync (ie. install one package on one, which gets replicated on all other machines). Is this possible?

Each machine has its own disk, and only home dirs are mounted via NFS. I don't want to mount the / over NFS.

Thanks!

---

### Post by Sef on 2008-05-16
> Also, when I set all machines, I would like to keep them all in sync (ie. install one package on one, which gets replicated on all other machines). Is this possible?

Check out [Clonezilla]("http://www.clonezilla.org/").  They have a [server edition]("http://www.clonezilla.org/clonezilla-server-edition/") too.

---

### Post by frootloop on 2009-04-06
Hi there,

Been looking for similar - started reading here:
[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/autodeploy](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/autodeploy)

Hope this helps!

---

