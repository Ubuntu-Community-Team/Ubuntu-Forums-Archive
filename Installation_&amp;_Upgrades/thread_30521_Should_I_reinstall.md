---
title: "Should I reinstall?"
date: 2005-04-29
forum: Installation &amp; Upgrades
---

### Post by maniac99 on 2005-04-29
Hey there,

I recently attempted to install Ubuntu and it failed (some cdrom error, I think now a bad disc).  I originally setup a few partitions, one for /home one for /usr and yeh..

When I reattempted to install Ubuntu, since it failed the previous time I just let it do default as I wanted to see if it worked this time and it did /swap and assigned the rest of the space to /

I am wondering, since it's a pretty new install (although I have got everything nice hehe) if I should reinstall and create a few extra partitions.  I figure if I don't, and I wanna reinstall in the future, it might stuff up my files etc?

What do you think?

---

### Post by odix on 2005-04-29
I would prefer to place /tmp /home /var on extra partitions, because in those directories there are a lot of changes.

And for the /tmp it is not necessary to have journaling filesystem, ext2 is good enough.

odiX

---

### Post by Professor X on 2005-04-29
If this installation is for a desktop system, I would say no.  Having more than one partition is mainly used for servers for security reasons (so the data that people access is sepearte from the programs).  It can be useful to have a separate /home partition, or one to share between different operating systems.  The ubuntu default works fine for me.

---

