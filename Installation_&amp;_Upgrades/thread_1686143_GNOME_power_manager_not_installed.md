---
title: "GNOME power manager not installed"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by rpk94 on 2011-02-11
I upgraded from 10.04 to 10.10, and the upgrade did not go smoothly. when it said that upgrade was finished, i restrted the computer.It says that the GNOME power manager is not correctly installed. Please contact your adminstrator. What can I do to solve it? I tried going in the terminal, but I can't get through the login. It does not accept my login ID and password. Is there a Chance that all my login data was deleted during the upgrade?

---

### Post by sikander3786 on 2011-02-12
Your data should still be there. Upgrade shouldn't delete any of your personal files.

During the upgrade, I think you ran out of disk space and thats why you are getting a power manager error.

Press Ctrl + Alt + F1 at your login screen and try loggin in using your credentials. Does it accept your password? If yes, please post the output of this command then.

```
df -h
```

---

