---
title: "new user can not update"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by merlin666 on 2010-03-02
I gave my laptop to a friend, and so he can use Ubuntu (Jaunty) I added another user to my own profile. All works well, but the Update Manager does not accept his password, and the last update was run back in November. How can an additional user (presumably without SU powers run the Update Manager)?

---

### Post by byStanderone on 2010-03-02
...you will have to give an admin privelege to a particular user so as  for him to do system updates as well.

---

### Post by thebigob on 2010-03-02
The above is correct. Only super users are allowed to do updates as this requires a file lock on a file that is owned by root.

Any user can be given sudo role by running the command visudo as root or sudo visudo.

I would strongly recommend reading the man page before editing this file: man visudo.

---

