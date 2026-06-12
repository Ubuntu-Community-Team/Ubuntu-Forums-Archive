---
title: "Installing from scratch on my work box"
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by Sham on 2006-05-31
I've been using Breezy on my work box, and it has been great from day 1. Everything works which is obviously very handy when you use Ubuntu for your day job ;)

I'm thinking forward to the Dapper upgrade, and how best to do it. The general opinion has been to do a full install from the CD rather than upgrading (which makes sense I suppose).

My partitions are setup as follows:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.2G  3.8G  5.0G  44% /
/dev/sda1              89M   27M   57M  32% /boot
/dev/sda4             122G   43G   74G  37% /home

I havn't installed from the CD for ages, but presumably if I were to install dapper to / and not touch /home, then all my data would be preserved? I will of course do a full system backup anyway, but I just want to avoid the hassle of shipping everything back later ;)

---

### Post by bruce89 on 2006-05-31
[QUOTE=Sham]
I havn't installed from the CD for ages, but presumably if I were to install dapper to / and not touch /home, then all my data would be preserved? I will of course do a full system backup anyway, but I just want to avoid the hassle of shipping everything back later ;)[/QUOTE]
Yes, it should work, but be careful not to format /home.

---

### Post by isotonic on 2006-05-31
i have a 8gb root partition and around 60gb home partition and updated successfully using the manager with no loss of user data...if you have a dsl connection or better then i would try an update first with your setup.

---

### Post by Sham on 2006-05-31
Cool, cheers guys. I thought I would ask because I couldn't remeber an option to not format a partition.

Anyhow, I suppose it wouldn't hurt to do an upgrade first to see how things go.

---

