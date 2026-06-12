---
title: "Can't change home permissions"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by andreselsuave on 2008-10-15
Hi there, since I installed intrepid beta i'm having some problems with the permissions of my home directory. When I log in I get an error. Something like the session won't be saved because I don't have permission over my $HOME/.dmrc directory. I try to change the permissions but I get a message:

```
sudo chown -R andreselsuave /home/myhome/
chown: can't access «/home/myhome/.gvfs»: Permission denied

```

any help would be appreciated

---

### Post by marttali on 2008-10-15
maybe you should try to do the same using chmod ?
sudo chmod -R 755 ...

---

### Post by kdorf on 2008-10-15
chmod -R u+rwX,go-rwx ~

would be better. You don't set unnecessary execute bits that way. And you don't give everyone write access to your home dir.

---

### Post by andreselsuave on 2008-10-15
Hmmm, chmod gives the same output. I think it has something to do with the upgrade to ubuntu ibex beta 1...

---

### Post by inportb on 2008-10-15
Try doing the same thing in a recovery mode root console.

---

