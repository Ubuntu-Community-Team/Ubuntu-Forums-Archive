---
title: "shell access"
date: 2005-08-09
forum: Installation &amp; Upgrades
---

### Post by doc_holiday on 2005-08-09
What I would like to do is give somebody ssh access to my computer to do some tests over the network. He can execute commands like ping..... but I don't want him to be able to see anything outside his homefolder.
What would be the best way to do this?

---

### Post by adwait on 2005-08-09
Like a normal user, a user who logs in through ssh can't modify anything outside his home folder. The user can do anything, that his username is allowed to do, when he physically is at the computer. So if you want that the user should not be able to even see what is outside his home direcotry...so you can set his permissions that way.

---

### Post by doc_holiday on 2005-08-09
[QUOTE=adwait]So if you want that the user should not be able to even see what is outside his home direcotry...so you can set his permissions that way.[/QUOTE]

And how do I do that, the easy way?

---

