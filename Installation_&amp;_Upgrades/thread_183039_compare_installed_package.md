---
title: "compare installed package"
date: 2006-05-27
forum: Installation &amp; Upgrades
---

### Post by dskloet on 2006-05-27
Hi,

I have two computers installed with Breezy and (only) one of them has a problem with fonts in Java. Now I wondered whether there is a way to get a list of all packages installed on one of them but not on the other.

thanks,
David

---

### Post by simonn on 2006-05-27
In a terminal on each of the PCs do:

```

$ dpkg -l | sort > [somefile]

```

Get both of the [somefile]s on to one of the machines and then d do  a diff between them

```

diff [somefile] [theother somefile]

```

---

### Post by dskloet on 2006-05-27
Thanks, it didn't help me to solve the problem (yet?) but at least I learned something :-).

---

