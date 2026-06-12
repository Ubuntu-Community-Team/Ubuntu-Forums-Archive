---
title: "Can i copy a mysql database?"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by Orange Kingdom on 2010-03-31
Hi,

Can i just copying a mysql database to another server?
I know there is mysqldump but why not just with the cp command?

---

### Post by wojox on 2010-03-31
That's what mysqldump primarily is.

---

### Post by new_tolinux on 2010-03-31
You _can_ use cp, but then you have to stop the mysql server.

After that you can simply copy the folders you need to your new mysql server.
I would suggest not to copy the folder of the mysql database itself, because the other server will have this folder of it's own (and there is a service account for Ubuntu specified in it).

---

### Post by Orange Kingdom on 2010-03-31
Ok, thanks.

And what about the user accounts like privileges etc. Will they also be copieed?

---

