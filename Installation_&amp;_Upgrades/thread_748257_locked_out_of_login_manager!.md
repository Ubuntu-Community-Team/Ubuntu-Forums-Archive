---
title: "locked out of login manager!"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by upforthedownstroke on 2008-04-07
I'm doing a mass install of Edubuntu Gutsy on ThinkPads for a school program and I've secured the student account via the Users & Groups panel by unchecking "Administer the system". The problem is that I'd like to do a root login from the login screen and do updates and such, but I'd forgotten to allow that option before removing the student account's admin. How do I fix this?

Thank you.

---

### Post by Partyboi2 on 2008-04-08
Boot into recovery mode then at the prompt add a new user
```
adduser *username*
``` (change username to what ever) after you have created a new user give the new user admin rights
usermod -G admin *username (*change username to above username) then reboot into normal mode and login with new user.

---

### Post by upforthedownstroke on 2008-04-08
I didn't have to boot into a recovery terminal, rather just login from virtual terminal 1, but thank you.

---

